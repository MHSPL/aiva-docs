---
title: Upload Endpoints
description: API reference for uploading FASTQ, VCF, CSV, and TSV files to AIVA, including direct uploads, cloud URLs, Small Variant Annotation, and Structural Variant Annotation.
---

# Upload Endpoints

Upload variant data files to AIVA programmatically. Supports FASTQ files for variant calling, direct VCF/CSV/TSV upload, cloud URL imports, and optional annotation with Small Variant Annotation or Structural Variant Annotation.

---

## FASTQ File Upload

Upload FASTQ files for variant calling through the Parabricks pipeline.

!!! info "Subscription required"
    FASTQ upload and variant calling requires a **Pro**, **Plus**, or **Trial** subscription tier.

### Request

```
POST /jobs/upload/parabricks
Content-Type: multipart/form-data
```

### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `pipeline_type` | string | Yes | Pipeline type: `germline`, `somatic_paired`, or `somatic_tumor_only` |
| `sequencer_type` | string | Yes | Sequencer type: `illumina`, `pacbio`, `ont`, `ultima`, `mgi`, or `element` |
| `data_type` | string | Yes | Data type: `wgs` (whole genome) or `wes` (whole exome) |
| `read_layout` | string | Yes | Read layout: `paired` or `single` |
| `sample_count` | integer | Yes | Number of samples being uploaded |
| `sample_name` | string | Yes | Name for the sample |
| `assembly` | string | Yes | Genome assembly (e.g., `GRCh38`, `GRCh37`) |
| `vep_annotation` | boolean | No | Run Small Variant Annotation on the output VCF. Default: `false` |
| `sample_1_r1` | file | Yes | Read 1 FASTQ file for sample 1 |
| `sample_1_r2` | file | Conditional | Read 2 FASTQ file for sample 1 (required for paired-end reads) |
| `samples_metadata` | JSON string | Yes | JSON array of sample metadata objects |
| `interval_file` | file | No | BED file for targeted regions (WES) |

### samples_metadata Format

The `samples_metadata` parameter is a JSON array of objects describing each sample:

**For germline pipelines:**

```json
[
  {
    "index": 1,
    "label": "Sample_001",
    "inputMode": "file",
    "relationship": "proband"
  }
]
```

| Field | Type | Description |
|-------|------|-------------|
| `index` | integer | Sample index (1-based) |
| `label` | string | Sample label |
| `inputMode` | string | `file` for direct upload, `url` for cloud URL |
| `relationship` | string | Relationship for germline: `proband`, `mother`, `father`, `sibling`, `other` |

**For somatic pipelines:**

```json
[
  {
    "index": 1,
    "label": "Tumor_001",
    "inputMode": "file",
    "sampleRole": "tumor"
  },
  {
    "index": 2,
    "label": "Normal_001",
    "inputMode": "file",
    "sampleRole": "normal"
  }
]
```

| Field | Type | Description |
|-------|------|-------------|
| `index` | integer | Sample index (1-based) |
| `label` | string | Sample label |
| `inputMode` | string | `file` for direct upload, `url` for cloud URL |
| `sampleRole` | string | Role for somatic: `tumor` or `normal` |

### Examples

=== "cURL"

    ```bash
    curl -X POST https://api.aivaportal.com/jobs/upload/parabricks \
      -H "Authorization: Bearer <AIVA_API_KEY>" \
      -F "pipeline_type=germline" \
      -F "sequencer_type=illumina" \
      -F "data_type=wgs" \
      -F "read_layout=paired" \
      -F "sample_count=1" \
      -F "sample_name=Patient-001" \
      -F "assembly=GRCh38" \
      -F "vep_annotation=true" \
      -F "sample_1_r1=@reads_R1.fastq.gz" \
      -F "sample_1_r2=@reads_R2.fastq.gz" \
      -F 'samples_metadata=[{"index":1,"label":"Patient-001","inputMode":"file","relationship":"proband"}]'
    ```

=== "Python"

    ```python
    import requests

    headers = {"Authorization": "Bearer <AIVA_API_KEY>"}

    files = {
        "sample_1_r1": open("reads_R1.fastq.gz", "rb"),
        "sample_1_r2": open("reads_R2.fastq.gz", "rb"),
    }

    data = {
        "pipeline_type": "germline",
        "sequencer_type": "illumina",
        "data_type": "wgs",
        "read_layout": "paired",
        "sample_count": 1,
        "sample_name": "Patient-001",
        "assembly": "GRCh38",
        "vep_annotation": "true",
        "samples_metadata": '[{"index":1,"label":"Patient-001","inputMode":"file","relationship":"proband"}]',
    }

    response = requests.post(
        "https://api.aivaportal.com/jobs/upload/parabricks",
        headers=headers,
        files=files,
        data=data,
    )
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    const formData = new FormData();
    formData.append("pipeline_type", "germline");
    formData.append("sequencer_type", "illumina");
    formData.append("data_type", "wgs");
    formData.append("read_layout", "paired");
    formData.append("sample_count", "1");
    formData.append("sample_name", "Patient-001");
    formData.append("assembly", "GRCh38");
    formData.append("vep_annotation", "true");
    formData.append("sample_1_r1", r1File);
    formData.append("sample_1_r2", r2File);
    formData.append(
      "samples_metadata",
      JSON.stringify([
        { index: 1, label: "Patient-001", inputMode: "file", relationship: "proband" }
      ])
    );

    const response = await fetch("https://api.aivaportal.com/jobs/upload/parabricks", {
      method: "POST",
      headers: { "Authorization": "Bearer <AIVA_API_KEY>" },
      body: formData,
    });
    const data = await response.json();
    console.log(data);
    ```

### Response

```json
{
  "job_id": "job_abc123",
  "status": "upload_pending",
  "message": "FASTQ upload initiated. Processing job created."
}
```

---

## FASTQ Cloud URL Upload

Upload FASTQ files from cloud storage URLs using the same endpoint but with `inputMode: "url"` in the samples metadata.

!!! info "Subscription required"
    FASTQ upload and variant calling requires a **Pro**, **Plus**, or **Trial** subscription tier.

### Request

```
POST /jobs/upload/parabricks
Content-Type: multipart/form-data
```

Instead of attaching files, provide cloud URLs in the `samples_metadata`:

```json
[
  {
    "index": 1,
    "label": "Patient-001",
    "inputMode": "url",
    "relationship": "proband",
    "r1Url": "gs://my-bucket/reads_R1.fastq.gz",
    "r2Url": "gs://my-bucket/reads_R2.fastq.gz"
  }
]
```

**Supported URL schemes:**

| Scheme | Provider |
|--------|----------|
| `gs://` | Google Cloud Storage |
| `s3://` | Amazon S3 |
| `az://` | Azure Blob Storage |
| `https://` | Any publicly accessible URL |

### Examples

=== "cURL"

    ```bash
    curl -X POST https://api.aivaportal.com/jobs/upload/parabricks \
      -H "Authorization: Bearer <AIVA_API_KEY>" \
      -F "pipeline_type=germline" \
      -F "sequencer_type=illumina" \
      -F "data_type=wgs" \
      -F "read_layout=paired" \
      -F "sample_count=1" \
      -F "sample_name=Patient-001" \
      -F "assembly=GRCh38" \
      -F 'samples_metadata=[{"index":1,"label":"Patient-001","inputMode":"url","relationship":"proband","r1Url":"gs://my-bucket/reads_R1.fastq.gz","r2Url":"gs://my-bucket/reads_R2.fastq.gz"}]'
    ```

=== "Python"

    ```python
    import requests
    import json

    headers = {"Authorization": "Bearer <AIVA_API_KEY>"}

    data = {
        "pipeline_type": "germline",
        "sequencer_type": "illumina",
        "data_type": "wgs",
        "read_layout": "paired",
        "sample_count": 1,
        "sample_name": "Patient-001",
        "assembly": "GRCh38",
        "samples_metadata": json.dumps([
            {
                "index": 1,
                "label": "Patient-001",
                "inputMode": "url",
                "relationship": "proband",
                "r1Url": "gs://my-bucket/reads_R1.fastq.gz",
                "r2Url": "gs://my-bucket/reads_R2.fastq.gz",
            }
        ]),
    }

    response = requests.post(
        "https://api.aivaportal.com/jobs/upload/parabricks",
        headers=headers,
        data=data,
    )
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    const formData = new FormData();
    formData.append("pipeline_type", "germline");
    formData.append("sequencer_type", "illumina");
    formData.append("data_type", "wgs");
    formData.append("read_layout", "paired");
    formData.append("sample_count", "1");
    formData.append("sample_name", "Patient-001");
    formData.append("assembly", "GRCh38");
    formData.append(
      "samples_metadata",
      JSON.stringify([
        {
          index: 1,
          label: "Patient-001",
          inputMode: "url",
          relationship: "proband",
          r1Url: "gs://my-bucket/reads_R1.fastq.gz",
          r2Url: "gs://my-bucket/reads_R2.fastq.gz",
        }
      ])
    );

    const response = await fetch("https://api.aivaportal.com/jobs/upload/parabricks", {
      method: "POST",
      headers: { "Authorization": "Bearer <AIVA_API_KEY>" },
      body: formData,
    });
    const data = await response.json();
    console.log(data);
    ```

---

## VCF Direct File Upload

Upload a VCF, CSV, or TSV file directly without annotation.

### Request

```
POST /jobs/upload
Content-Type: multipart/form-data
```

### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `file` | file | Yes | The file to upload (VCF, CSV, or TSV) |
| `sample_name` | string | No | Display name for the sample. Defaults to the filename. |
| `assembly` | string | No | Genome assembly: `GRCh38` or `GRCh37`. Default: `GRCh38` |
| `sample_type` | string | No | Sample type description |
| `notes` | string | No | Notes about the sample |
| `split_by_sample` | boolean | No | Split multi-sample VCF into individual samples. Default: `false` |

### Examples

=== "cURL"

    ```bash
    curl -X POST https://api.aivaportal.com/jobs/upload \
      -H "Authorization: Bearer <AIVA_API_KEY>" \
      -F "file=@sample.vcf" \
      -F "sample_name=Patient-001" \
      -F "assembly=GRCh38"
    ```

=== "Python"

    ```python
    import requests

    headers = {"Authorization": "Bearer <AIVA_API_KEY>"}

    files = {"file": open("sample.vcf", "rb")}
    data = {
        "sample_name": "Patient-001",
        "assembly": "GRCh38",
    }

    response = requests.post(
        "https://api.aivaportal.com/jobs/upload",
        headers=headers,
        files=files,
        data=data,
    )
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    const formData = new FormData();
    formData.append("file", fileInput);
    formData.append("sample_name", "Patient-001");
    formData.append("assembly", "GRCh38");

    const response = await fetch("https://api.aivaportal.com/jobs/upload", {
      method: "POST",
      headers: { "Authorization": "Bearer <AIVA_API_KEY>" },
      body: formData,
    });
    const data = await response.json();
    console.log(data);
    ```

### Response

```json
{
  "job_id": "job_abc123",
  "status": "queued",
  "message": "File uploaded successfully. Processing job created."
}
```

---

## VCF Direct Cloud Upload

Import a VCF file from a cloud storage URL without annotation.

### Request

```
POST /jobs/upload/from-cloud-url
Content-Type: application/json
```

### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `cloud_url` | string | Yes | Cloud storage URL of the file |
| `sample_name` | string | No | Display name for the sample |
| `assembly` | string | No | Genome assembly: `GRCh38` or `GRCh37`. Default: `GRCh38` |
| `split_by_sample` | boolean | No | Split multi-sample VCF. Default: `false` |

**Supported URL schemes:**

| Scheme | Provider |
|--------|----------|
| `gs://` | Google Cloud Storage |
| `s3://` | Amazon S3 |
| `az://` | Azure Blob Storage |
| `https://` | Any publicly accessible URL |

### Examples

=== "cURL"

    ```bash
    curl -X POST https://api.aivaportal.com/jobs/upload/from-cloud-url \
      -H "Authorization: Bearer <AIVA_API_KEY>" \
      -H "Content-Type: application/json" \
      -d '{
        "cloud_url": "gs://my-bucket/samples/sample.vcf",
        "sample_name": "Patient-002",
        "assembly": "GRCh38"
      }'
    ```

=== "Python"

    ```python
    import requests

    headers = {
        "Authorization": "Bearer <AIVA_API_KEY>",
        "Content-Type": "application/json",
    }

    payload = {
        "cloud_url": "gs://my-bucket/samples/sample.vcf",
        "sample_name": "Patient-002",
        "assembly": "GRCh38",
    }

    response = requests.post(
        "https://api.aivaportal.com/jobs/upload/from-cloud-url",
        headers=headers,
        json=payload,
    )
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    const response = await fetch("https://api.aivaportal.com/jobs/upload/from-cloud-url", {
      method: "POST",
      headers: {
        "Authorization": "Bearer <AIVA_API_KEY>",
        "Content-Type": "application/json",
      },
      body: JSON.stringify({
        cloud_url: "gs://my-bucket/samples/sample.vcf",
        sample_name: "Patient-002",
        assembly: "GRCh38",
      }),
    });
    const data = await response.json();
    console.log(data);
    ```

### Response

```json
{
  "job_id": "job_def456",
  "status": "queued",
  "message": "Cloud download job created. File will be downloaded and processed."
}
```

---

## VCF Small Variant Annotation File Upload

Upload a VCF file with Small Variant Annotation enabled.

!!! info "Subscription required"
    Small Variant Annotation requires a **Plus**, **Pro**, or **Trial** subscription tier.

Small Variant Annotation adds the following fields to your variant data:

- **Consequence** -- predicted variant consequence (e.g., missense_variant, stop_gained)
- **Gene Symbol** -- HGNC gene symbol
- **SIFT** -- SIFT prediction and score
- **gnomAD** -- Population allele frequencies
- **ClinVar** -- Clinical significance
- **Amino Acid** -- Amino acid change information

### Request

```
POST /jobs/upload
Content-Type: multipart/form-data
```

### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `file` | file | Yes | The VCF file to upload |
| `sample_name` | string | No | Display name for the sample |
| `assembly` | string | No | Genome assembly: `GRCh38` or `GRCh37`. Default: `GRCh38` |
| `vep_annotation` | boolean | Yes | Set to `true` to enable Small Variant Annotation |
| `enable_ditto` | boolean | No | Enable DITTO pathogenicity scoring. Default: `false` |
| `split_by_sample` | boolean | No | Split multi-sample VCF. Default: `false` |

### Examples

=== "cURL"

    ```bash
    curl -X POST https://api.aivaportal.com/jobs/upload \
      -H "Authorization: Bearer <AIVA_API_KEY>" \
      -F "file=@sample.vcf" \
      -F "sample_name=Patient-001" \
      -F "assembly=GRCh38" \
      -F "vep_annotation=true" \
      -F "enable_ditto=false"
    ```

=== "Python"

    ```python
    import requests

    headers = {"Authorization": "Bearer <AIVA_API_KEY>"}

    files = {"file": open("sample.vcf", "rb")}
    data = {
        "sample_name": "Patient-001",
        "assembly": "GRCh38",
        "vep_annotation": "true",
        "enable_ditto": "false",
    }

    response = requests.post(
        "https://api.aivaportal.com/jobs/upload",
        headers=headers,
        files=files,
        data=data,
    )
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    const formData = new FormData();
    formData.append("file", fileInput);
    formData.append("sample_name", "Patient-001");
    formData.append("assembly", "GRCh38");
    formData.append("vep_annotation", "true");
    formData.append("enable_ditto", "false");

    const response = await fetch("https://api.aivaportal.com/jobs/upload", {
      method: "POST",
      headers: { "Authorization": "Bearer <AIVA_API_KEY>" },
      body: formData,
    });
    const data = await response.json();
    console.log(data);
    ```

---

## VCF Small Variant Annotation Cloud Upload

Import a VCF file from a cloud URL with Small Variant Annotation enabled.

!!! info "Subscription required"
    Small Variant Annotation requires a **Plus**, **Pro**, or **Trial** subscription tier.

### Request

```
POST /jobs/upload/from-cloud-url
Content-Type: application/json
```

### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `cloud_url` | string | Yes | Cloud storage URL of the VCF file |
| `sample_name` | string | No | Display name for the sample |
| `assembly` | string | No | Genome assembly: `GRCh38` or `GRCh37`. Default: `GRCh38` |
| `vep_annotation` | boolean | Yes | Set to `true` to enable Small Variant Annotation |

### Examples

=== "cURL"

    ```bash
    curl -X POST https://api.aivaportal.com/jobs/upload/from-cloud-url \
      -H "Authorization: Bearer <AIVA_API_KEY>" \
      -H "Content-Type: application/json" \
      -d '{
        "cloud_url": "gs://my-bucket/samples/sample.vcf",
        "sample_name": "Patient-002",
        "assembly": "GRCh38",
        "vep_annotation": true
      }'
    ```

=== "Python"

    ```python
    import requests

    headers = {
        "Authorization": "Bearer <AIVA_API_KEY>",
        "Content-Type": "application/json",
    }

    payload = {
        "cloud_url": "gs://my-bucket/samples/sample.vcf",
        "sample_name": "Patient-002",
        "assembly": "GRCh38",
        "vep_annotation": True,
    }

    response = requests.post(
        "https://api.aivaportal.com/jobs/upload/from-cloud-url",
        headers=headers,
        json=payload,
    )
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    const response = await fetch("https://api.aivaportal.com/jobs/upload/from-cloud-url", {
      method: "POST",
      headers: {
        "Authorization": "Bearer <AIVA_API_KEY>",
        "Content-Type": "application/json",
      },
      body: JSON.stringify({
        cloud_url: "gs://my-bucket/samples/sample.vcf",
        sample_name: "Patient-002",
        assembly: "GRCh38",
        vep_annotation: true,
      }),
    });
    const data = await response.json();
    console.log(data);
    ```

---

## VCF Structural Variant Annotation File Upload

Upload a VCF file with Structural Variant Annotation enabled.

!!! info "Subscription required"
    Structural Variant Annotation requires a **Plus**, **Pro**, or **Trial** subscription tier.

Structural Variant Annotation is designed for structural variant VCF files containing variant types such as:

- **DEL** -- Deletions
- **DUP** -- Duplications
- **INS** -- Insertions
- **INV** -- Inversions
- **BND** -- Breakends
- **CNV** -- Copy number variants

Structural Variant Annotation adds the following annotations:

- Gene annotations and overlap
- DGV and gnomAD-SV population frequencies
- ClinVar structural variant matches
- Regulatory element overlap
- Clinical ranking from 1 (benign) to 5 (pathogenic)

### Request

```
POST /jobs/upload
Content-Type: multipart/form-data
```

### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `file` | file | Yes | The structural variant VCF file to upload |
| `sample_name` | string | No | Display name for the sample |
| `assembly` | string | No | Genome assembly: `GRCh38` or `GRCh37`. Default: `GRCh38` |
| `annotsv_annotation` | boolean | Yes | Set to `true` to enable Structural Variant Annotation |
| `split_by_sample` | boolean | No | Split multi-sample VCF. Default: `false` |

### Examples

=== "cURL"

    ```bash
    curl -X POST https://api.aivaportal.com/jobs/upload \
      -H "Authorization: Bearer <AIVA_API_KEY>" \
      -F "file=@structural_variants.vcf" \
      -F "sample_name=SV-Sample-001" \
      -F "assembly=GRCh38" \
      -F "annotsv_annotation=true"
    ```

=== "Python"

    ```python
    import requests

    headers = {"Authorization": "Bearer <AIVA_API_KEY>"}

    files = {"file": open("structural_variants.vcf", "rb")}
    data = {
        "sample_name": "SV-Sample-001",
        "assembly": "GRCh38",
        "annotsv_annotation": "true",
    }

    response = requests.post(
        "https://api.aivaportal.com/jobs/upload",
        headers=headers,
        files=files,
        data=data,
    )
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    const formData = new FormData();
    formData.append("file", fileInput);
    formData.append("sample_name", "SV-Sample-001");
    formData.append("assembly", "GRCh38");
    formData.append("annotsv_annotation", "true");

    const response = await fetch("https://api.aivaportal.com/jobs/upload", {
      method: "POST",
      headers: { "Authorization": "Bearer <AIVA_API_KEY>" },
      body: formData,
    });
    const data = await response.json();
    console.log(data);
    ```

---

## VCF Structural Variant Annotation Cloud Upload

Import a structural variant VCF file from a cloud URL with Structural Variant Annotation enabled.

!!! info "Subscription required"
    Structural Variant Annotation requires a **Plus**, **Pro**, or **Trial** subscription tier.

### Request

```
POST /jobs/upload/from-cloud-url
Content-Type: application/json
```

### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `cloud_url` | string | Yes | Cloud storage URL of the VCF file |
| `sample_name` | string | No | Display name for the sample |
| `assembly` | string | No | Genome assembly: `GRCh38` or `GRCh37`. Default: `GRCh38` |
| `annotsv_annotation` | boolean | Yes | Set to `true` to enable Structural Variant Annotation |

### Examples

=== "cURL"

    ```bash
    curl -X POST https://api.aivaportal.com/jobs/upload/from-cloud-url \
      -H "Authorization: Bearer <AIVA_API_KEY>" \
      -H "Content-Type: application/json" \
      -d '{
        "cloud_url": "gs://my-bucket/sv/structural_variants.vcf",
        "sample_name": "SV-Sample-002",
        "assembly": "GRCh38",
        "annotsv_annotation": true
      }'
    ```

=== "Python"

    ```python
    import requests

    headers = {
        "Authorization": "Bearer <AIVA_API_KEY>",
        "Content-Type": "application/json",
    }

    payload = {
        "cloud_url": "gs://my-bucket/sv/structural_variants.vcf",
        "sample_name": "SV-Sample-002",
        "assembly": "GRCh38",
        "annotsv_annotation": True,
    }

    response = requests.post(
        "https://api.aivaportal.com/jobs/upload/from-cloud-url",
        headers=headers,
        json=payload,
    )
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    const response = await fetch("https://api.aivaportal.com/jobs/upload/from-cloud-url", {
      method: "POST",
      headers: {
        "Authorization": "Bearer <AIVA_API_KEY>",
        "Content-Type": "application/json",
      },
      body: JSON.stringify({
        cloud_url: "gs://my-bucket/sv/structural_variants.vcf",
        sample_name: "SV-Sample-002",
        assembly: "GRCh38",
        annotsv_annotation: true,
      }),
    });
    const data = await response.json();
    console.log(data);
    ```

---

## File Format Requirements

### VCF Files

- Must follow VCF 4.x specification.
- Compressed files (`.vcf.gz`) are supported.
- Multi-sample VCF files are supported (use `split_by_sample` to separate).

### CSV Files

- First row must contain column headers.
- Standard comma delimiter.
- UTF-8 encoding.

### TSV Files

- First row must contain column headers.
- Tab-delimited.
- UTF-8 encoding.

### FASTQ Files

- Standard FASTQ format.
- Compressed files (`.fastq.gz`, `.fq.gz`) are supported.
- Paired-end reads require separate R1 and R2 files.

---

## Next Steps

After uploading, monitor your job status using the [Job Monitoring](job-monitoring.md) endpoints.
