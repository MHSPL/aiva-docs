---
title: Clinical Trials
description: Search ClinicalTrials.gov through AIVA Chat to find active, recruiting, and completed trials relevant to patient variants, genes, and conditions.
---

# Clinical Trials

The Clinical Trials tool searches ClinicalTrials.gov directly from AIVA Chat. Use it to find trials relevant to specific genes, variants, conditions, or interventions -- helping connect genomic findings to potential therapeutic opportunities.

---

## Capabilities

- **Search by condition** -- Find trials for specific diseases or syndromes (e.g., "hereditary breast cancer," "Lynch syndrome").
- **Search by gene** -- Locate trials that mention specific genes in their eligibility criteria or study descriptions.
- **Search by intervention** -- Find trials testing a particular drug, therapy, or procedure.
- **Filter by status** -- Focus on recruiting, active, or completed trials.
- **Filter by phase** -- Narrow results to Phase 1, 2, 3, or 4 trials.
- **Retrieve trial details** -- Get titles, NCT numbers, sponsors, phases, enrollment status, and eligibility summaries.

---

## Example Prompts

| Goal | Prompt |
|------|--------|
| Gene-specific trials | "Are there any active clinical trials for TP53-mutated breast cancer?" |
| Drug-specific trials | "Find recruiting trials for olaparib in ovarian cancer." |
| Phase filtering | "What phase 3 trials are studying PARP inhibitors?" |
| Rare disease | "Are there any clinical trials for patients with PALB2 mutations?" |
| Combination therapy | "Find trials combining immunotherapy with targeted therapy for BRAF-mutated melanoma." |
| Eligibility | "What are the eligibility criteria for NCT04171700?" |

---

## Understanding the Results

AIVA returns trial information in a structured format:

| Field | Description |
|-------|-------------|
| **Title** | Official title of the clinical trial |
| **NCT Number** | Unique ClinicalTrials.gov identifier (e.g., NCT04171700) |
| **Phase** | Trial phase (Phase 1, 2, 3, 4, or combinations) |
| **Status** | Recruiting, Active not recruiting, Completed, Terminated, etc. |
| **Sponsor** | Organization leading the trial |
| **Conditions** | Diseases or conditions being studied |
| **Interventions** | Drugs, biologics, or procedures being tested |

!!! tip "Use NCT numbers for follow-up"
    If you find a trial of interest, you can ask AIVA for more details using its NCT number, or visit `clinicaltrials.gov/study/NCTxxxxxxxx` directly.

---

## Common Use Cases

### Connecting Variants to Trials

After identifying a pathogenic variant, search for trials that enroll patients with that specific mutation:

> "I found a pathogenic BRCA1 variant. Are there any recruiting trials for BRCA1-mutated ovarian cancer?"

### Exploring Treatment Options

When interpreting variants in actionable genes, find trials testing targeted therapies:

> "What clinical trials are testing EGFR inhibitors for non-small cell lung cancer?"

### Rare Disease Research

For uncommon conditions, clinical trials may represent the only therapeutic option:

> "Find any clinical trials related to Fanconi anemia, regardless of phase or status."

---

## Combining with Other Tools

Clinical Trials integrates naturally with other AIVA tools:

- **Genomic Data Query + Clinical Trials** -- Query your data for actionable variants, then search for trials targeting those variants.
- **Knowledge Graph + Clinical Trials** -- Find drugs that target a specific gene, then search for trials testing those drugs.
- **Variant Annotation + Clinical Trials** -- Look up a variant's clinical significance, then find relevant trials for the associated condition.
- **Web Search + Clinical Trials** -- Search for the latest treatment guidelines, then find active trials for recommended therapies.

See [Example Workflows](example-workflows.md) for end-to-end analysis patterns.

---

## Limitations

- Results are sourced from ClinicalTrials.gov and may not include trials registered only on other registries (e.g., EU Clinical Trials Register, ANZCTR).
- Trial information reflects what is publicly registered. Enrollment status may not always be current.
- AIVA summarizes trial information but does not provide medical advice about trial eligibility or suitability.

!!! warning "Not a substitute for clinical judgment"
    Clinical trial results from AIVA are informational. Decisions about patient enrollment should involve the treating physician and the trial's principal investigator.
