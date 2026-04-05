---
title: Prompting Guide
description: Practical prompting strategies and workflows for getting the most out of AIVA Chat, including best practices, multi-sample analysis, and clinical data integration.
---

# Prompting guide

AIVA is the first agentic variant analysis platform. It translates your natural language questions into tool calls, SQL queries, and structured analysis. The quality of your results depends on how you frame your questions. This section covers practical strategies and worked examples drawn from real analysis workflows.

---

## Best practices

### Be specific about what you want

Vague prompts produce vague answers. Include gene names, frequency thresholds, consequence types, and sample identifiers in your questions. The more context you give AIVA, the more precise and actionable the results.

| Goal | Instead of | Try |
|------|-----------|-----|
| Filter variants | "Show me important variants" | "List missense and nonsense variants in BRCA1 with gnomAD AF below 0.01" |
| Count by gene | "How many variants do I have?" | "How many variants per gene are in @samples:patient_042?" |
| Find rare variants | "Find rare variants" | "List variants with gnomAD AF below 0.001 and HIGH or MODERATE impact in @samples:cohort_40" |
| Quality filtering | "Show good variants" | "List variants that PASS filters with read depth above 20 in @samples:sample1" |

### Ask for counts before listing

For large datasets, asking AIVA to list all matching variants can produce overwhelming output. The chat displays up to 100 results at a time, so starting with a count helps you decide whether to list everything, add more filters, or export the results.

!!! tip "Start with counts"
    Ask "How many rare missense variants are in SCN1A?" first. If the answer is 3, ask to list them. If the answer is 200, add more filters before requesting the full list.

**Example workflow:**

> "How many variants in @samples:family_cohort have a gnomAD allele frequency below 0.001 and a DITTO score above 0.8?"

Then follow up:

> "List those variants, sorted by DITTO score descending."

### Chain your prompts

AIVA maintains conversation context across messages. You can build up your analysis step by step rather than asking one massive question. Each follow-up benefits from the context of previous answers.

**Example prompt chain:**

1. "How many samples in @samples:cohort_40 carry rare variants in SCN1A?"
2. "Which specific samples have those variants?"
3. "For sample HG003, list the SCN1A variants with their consequence and allele frequency."
4. "Classify the most significant variant using ACMG criteria."

!!! info "Conversation context"
    AIVA remembers previous messages in the conversation. You do not need to repeat sample names or filters from earlier prompts. If context gets lost in very long conversations, start a new conversation and re-establish the key details in your first message.

### Reference your data explicitly

Use the `@` mention to tell AIVA which dataset to query. Without it, AIVA may not know which sample you mean. You can reference multiple samples in a single prompt.

!!! tip "The @ mention menu"
    Type `@` in the chat input to open the mention menu. Select a sample to attach it to your message. See [Quick Start](../quick-start.md) for a walkthrough.

**Referencing specific files:**

- `@samples:clinical_data` to query your clinical metadata
- `@samples:multisample_vcf` to query a multi-sample VCF
- `@samples:sample1, @samples:sample2` to reference multiple individual samples

---

## Quick reference

1. **Attach your data**: Type `@` and select your sample before asking questions about it.
2. **Be specific**: Include gene names, frequency thresholds, consequence types, and sample identifiers.
3. **Filter for quality**: Ask AIVA to filter for PASS status and minimum read depth to exclude artifacts.
4. **Count first, list second**: Ask for counts before requesting full variant lists.
5. **Chain prompts**: Build analysis step by step. AIVA remembers conversation context.
6. **Cross-reference datasets**: Query clinical data first to establish context, then query variants.
7. **Match your model to the task**: Use faster models for simple queries and more capable models for multi-step analysis.

---

## In this section

<div class="grid-cards" markdown>

<div class="card" markdown>

### Multi-sample analysis

Workflows for querying multi-sample VCFs, per-sample breakdowns, and gene-specific cohort queries.

[:octicons-arrow-right-24: Multi-sample analysis](multi-sample-analysis.md)

</div>

<div class="card" markdown>

### Clinical data integration

Cross-reference clinical metadata with variant data for family-based analysis and segregation workflows.

[:octicons-arrow-right-24: Clinical data](clinical-data.md)

</div>

<div class="card" markdown>

### Upload strategy and model tips

Choosing between single and multiple VCF uploads, and selecting the right model for your analysis.

[:octicons-arrow-right-24: Upload strategy](upload-strategy.md)

</div>

</div>
