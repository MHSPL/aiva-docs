---
title: Changelog
description: Release notes and update history for the AIVA platform.
---

# Changelog

This page documents significant releases, new features, improvements, and bug fixes for the AIVA platform. Entries are listed in reverse chronological order.

For real-time update notifications, check the "What's New" announcements in the AIVA application.

---

## 2026-04-04

**New Features**

- **Optional SNV/Indel calling**: FASTQ uploads now allow disabling SNV/Indel downstream processing. When disabled, only BAM files and raw VCF are produced. Enabled by default.
- **CNV calling**: Optional copy number variation analysis, available as an add-on for FASTQ uploads. Results are annotated and loaded into AIVA for analysis.
- **SV calling**: Optional structural variant calling, available as an add-on for FASTQ uploads. Results are annotated and loaded into AIVA for analysis.
- **VCF download link**: Sample cards now show a VCF download link alongside BAM files for all pipeline-processed samples.

**Improvements**

- **Haplotype phasing**: Read phasing is now always enabled for germline and somatic paired pipelines, adding haplotype information to all variant calls.
- **Compressed VCF output**: Pipelines now output compressed VCF files, reducing storage costs.

---

## 2026-03-30

**New Features**

- **Playbooks**: Reusable, step-by-step AI analysis playbooks for standardized genomic workflows. Browse community-contributed playbooks in the marketplace, create your own, or fork and customize existing ones. See [Playbooks](playbooks/index.md).
- **Pharmacogenomics (PGx) analysis**: Automatically assign star alleles, predict metabolizer phenotypes, and generate CPIC drug recommendations for 88 pharmacogenes as part of the secondary analysis pipeline. See [Pharmacogenomics](analysis/pharmacogenomics.md).
- **WES/WGS credit pricing**: Credits are now charged based on variant count per sample. WES samples (≤200k variants) cost 1 credit, WGS samples (>200k variants) cost 2 credits.

**Improvements**

- Updated the Plus and Pro tier UI to display WES/WGS credit costs and storage slot counts (including BAMs).


---

<!-- Template for new releases:

## YYYY-MM-DD

**New Features**

- Description of new feature.

**Improvements**

- Description of improvement.

**Bug Fixes**

- Description of bug fix.

**Breaking Changes**

- Description of breaking change (if any).

-->

---

## Release Notes Format

Each release entry includes the following sections as applicable:

| Section | Description |
|---------|-------------|
| **New Features** | Entirely new capabilities added to the platform. |
| **Improvements** | Enhancements to existing features, performance improvements, and UX refinements. |
| **Bug Fixes** | Corrections to issues reported by users or discovered during testing. |
| **Breaking Changes** | Changes that may require user action, such as API changes, deprecated features, or modified workflows. |
| **Security** | Security patches and vulnerability fixes. |
| **Deprecations** | Features that are planned for removal in a future release. |

---

## Staying Updated

- **In-app announcements**: The "What's New" notification in the AIVA navigation bar highlights the most important changes.
- **This changelog**: Comprehensive release notes for all updates.
- **API changes**: Breaking API changes are communicated through this changelog. See [API Reference](api/index.md).
