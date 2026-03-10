---
title: Classification API
description: API reference for AI-powered variant classification using ACMG and AMP guidelines in AIVA.
---

# Classification API

The Classification API provides AI-powered variant classification using ACMG (American College of Medical Genetics) or AMP (Association for Molecular Pathology) guidelines. Submit a variant using genomic coordinates, rsID, or HGVS notation and receive a detailed classification with supporting evidence.

---

## Classify a Variant

### Request

```
POST /api/analyze/classify-variant
Content-Type: application/json
```

### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `variant_data` | object | Yes | Variant identifier in one of the supported formats (see below) |
| `classification_type` | string | Yes | Classification framework: `acmg` or `amp` |
| `assembly` | string | No | Genome assembly: `GRCh38` or `GRCh37`. Default: `GRCh38` |
| `phenotype_terms` | array | No | HPO terms or phenotype descriptions to guide classification |
| `description` | string | No | Additional variant description or context |
| `additional_context` | string | No | Extra clinical or research context for the AI |
| `model` | string | No | LLM model to use for classification |

### Variant Data Formats

The `variant_data` parameter accepts three formats:

**Genomic coordinates:**

```json
{
  "variant_data": {
    "chrom": "17",
    "pos": 41245466,
    "ref": "G",
    "alt": "A"
  }
}
```

**rsID:**

```json
{
  "variant_data": {
    "rsid": "rs80357906"
  }
}
```

**HGVS notation:**

```json
{
  "variant_data": {
    "hgvs": "NM_007294.4:c.5266dupC"
  }
}
```

### Examples

=== "cURL"

    **Using genomic coordinates:**

    ```bash
    curl -X POST https://api.aivaportal.com/api/analyze/classify-variant \
      -H "Authorization: Bearer <AIVA_API_KEY>" \
      -H "Content-Type: application/json" \
      -d '{
        "variant_data": {
          "chrom": "17",
          "pos": 41245466,
          "ref": "G",
          "alt": "A"
        },
        "classification_type": "acmg",
        "assembly": "GRCh38",
        "phenotype_terms": ["hereditary breast cancer"],
        "description": "BRCA1 missense variant",
        "additional_context": "Patient with family history of breast cancer"
      }'
    ```

    **Using rsID:**

    ```bash
    curl -X POST https://api.aivaportal.com/api/analyze/classify-variant \
      -H "Authorization: Bearer <AIVA_API_KEY>" \
      -H "Content-Type: application/json" \
      -d '{
        "variant_data": {
          "rsid": "rs80357906"
        },
        "classification_type": "acmg",
        "assembly": "GRCh38"
      }'
    ```

    **Using HGVS notation:**

    ```bash
    curl -X POST https://api.aivaportal.com/api/analyze/classify-variant \
      -H "Authorization: Bearer <AIVA_API_KEY>" \
      -H "Content-Type: application/json" \
      -d '{
        "variant_data": {
          "hgvs": "NM_007294.4:c.5266dupC"
        },
        "classification_type": "acmg",
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

    # Using genomic coordinates
    payload = {
        "variant_data": {
            "chrom": "17",
            "pos": 41245466,
            "ref": "G",
            "alt": "A",
        },
        "classification_type": "acmg",
        "assembly": "GRCh38",
        "phenotype_terms": ["hereditary breast cancer"],
        "description": "BRCA1 missense variant",
        "additional_context": "Patient with family history of breast cancer",
    }

    response = requests.post(
        "https://api.aivaportal.com/api/analyze/classify-variant",
        headers=headers,
        json=payload,
    )
    print(response.json())
    ```

    ```python
    # Using rsID
    payload = {
        "variant_data": {"rsid": "rs80357906"},
        "classification_type": "acmg",
        "assembly": "GRCh38",
    }

    response = requests.post(
        "https://api.aivaportal.com/api/analyze/classify-variant",
        headers=headers,
        json=payload,
    )
    print(response.json())
    ```

    ```python
    # Using HGVS notation
    payload = {
        "variant_data": {"hgvs": "NM_007294.4:c.5266dupC"},
        "classification_type": "acmg",
        "assembly": "GRCh38",
    }

    response = requests.post(
        "https://api.aivaportal.com/api/analyze/classify-variant",
        headers=headers,
        json=payload,
    )
    print(response.json())
    ```

=== "JavaScript"

    ```javascript
    // Using genomic coordinates
    const response = await fetch(
      "https://api.aivaportal.com/api/analyze/classify-variant",
      {
        method: "POST",
        headers: {
          "Authorization": "Bearer <AIVA_API_KEY>",
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          variant_data: {
            chrom: "17",
            pos: 41245466,
            ref: "G",
            alt: "A",
          },
          classification_type: "acmg",
          assembly: "GRCh38",
          phenotype_terms: ["hereditary breast cancer"],
          description: "BRCA1 missense variant",
          additional_context: "Patient with family history of breast cancer",
        }),
      }
    );
    const data = await response.json();
    console.log(data);
    ```

    ```javascript
    // Using rsID
    const response = await fetch(
      "https://api.aivaportal.com/api/analyze/classify-variant",
      {
        method: "POST",
        headers: {
          "Authorization": "Bearer <AIVA_API_KEY>",
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          variant_data: { rsid: "rs80357906" },
          classification_type: "acmg",
          assembly: "GRCh38",
        }),
      }
    );
    const data = await response.json();
    console.log(data);
    ```

---

## Classification Types

### ACMG Classification

When `classification_type` is set to `acmg`, the AI evaluates the variant against ACMG/AMP criteria and returns one of five tiers:

| Classification | Description |
|----------------|-------------|
| Pathogenic | Strong evidence of disease association |
| Likely Pathogenic | Probable disease association |
| Uncertain Significance (VUS) | Insufficient evidence to classify |
| Likely Benign | Probable benign variant |
| Benign | Strong evidence of benign nature |

ACMG criteria evaluated include: PVS1, PS1-PS4, PM1-PM6, PP1-PP5, BA1, BS1-BS4, BP1-BP7.

### AMP Classification

When `classification_type` is set to `amp`, the AI evaluates the variant using AMP/ASCO/CAP guidelines for somatic variants:

| Tier | Classification | Description |
|------|----------------|-------------|
| Tier I | Strong clinical significance | Variants with strong evidence of clinical actionability |
| Tier II | Potential clinical significance | Variants with potential clinical actionability |
| Tier III | Unknown clinical significance | Variants with insufficient evidence |
| Tier IV | Benign or likely benign | Variants without clinical significance |

---

## Response Format

The classification response includes the AI-generated classification along with supporting evidence:

```json
{
  "classification": "Likely Pathogenic",
  "criteria_applied": ["PS1", "PM2", "PP3"],
  "evidence_summary": "This variant has been previously reported as pathogenic...",
  "variant_info": {
    "chrom": "17",
    "pos": 41245466,
    "ref": "G",
    "alt": "A",
    "gene": "BRCA1"
  }
}
```

!!! note "AI-assisted classification"
    Classifications are generated by AI based on available evidence and should be reviewed by a qualified clinical geneticist before use in clinical decision-making.
