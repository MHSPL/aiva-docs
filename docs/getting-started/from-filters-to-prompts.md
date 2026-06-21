---
title: From Filters to Prompts
description: A mental-model guide for clinical geneticists moving from manual filter-and-table variant triage to agentic analysis with AIVA. Includes a filter-to-prompt translation table, a reframed triage workflow, and how to verify the agent's work.
---

# From filters to prompts

If you have triaged variants in tools like Franklin, VarSeq, Alissa, or Emedgene, you already have a mental model: build a filter cascade, watch the variant count drop, scan the surviving rows, and work each candidate by hand. AIVA does not take that model away. It sits on top of it. The difference is that **you describe the result you want, and the agent builds the filter, gathers the evidence, and shows its work**, instead of you clicking through every step.

This page is the bridge. It maps what you already do to how you do it in AIVA, so the agentic workflow feels like a faster version of your current one rather than a new tool to learn from scratch.

!!! info "You are not giving up the table"
    AIVA keeps the full filterable variant table you are used to (see [Tertiary Analysis](../analysis/tertiary-analysis.md)). Agentic analysis is an *addition*, not a replacement. Most experienced users move fluidly between the two: ask the agent to narrow the field, then open the table to review the survivors row by row.

---

## The shift in one picture

The work is the same. What changes is *who drives the mechanics* and *where your attention goes*.

| | Manual triage (the tools you know) | Agentic analysis (AIVA) |
|---|---|---|
| **How you start** | Build a filter cascade: PASS, gnomAD AF, consequence, gene panel | Ask in plain English for the same result |
| **Who applies the logic** | You, click by click | The agent translates your request into a query and runs it |
| **Where evidence comes from** | You open ClinVar, gnomAD, PubMed in separate tabs | The agent pulls ClinVar, gnomAD, literature, and trials inline |
| **What you see** | Rows that survived your filter | The same rows, plus a written rationale and the tool calls used |
| **Where your time goes** | Mechanics: clicking, copying, tab-switching | Judgment: reviewing evidence and deciding |
| **The output** | A shortlist you assembled | A shortlist the agent assembled, for you to confirm |

!!! quote "What this feels like in practice"
    *"It doesn't replace my expertise, but it streamlines the process and lets me spend more time thinking critically about the variant instead of gathering evidence."* (Shaurita Hutchins, PhD Researcher, UAB)

The goal is not to trust a black box. It is to delegate the **gathering** so you can spend your expertise on the **deciding**.

---

## Your filter cascade, as prompts

This is the core translation. Everything you express as a filter, you can express as a sentence. Attach your sample first by typing `@` and selecting it, then ask.

| What you would filter for | The AIVA prompt |
|---|---|
| `FILTER = PASS` | "Keep only variants that PASS quality filters in @samples:patient_042." |
| `gnomAD AF < 0.01` | "Show rare variants with gnomAD allele frequency below 1%." |
| Consequence in {missense, frameshift, stop_gained} | "Limit to missense, frameshift, and stop-gained consequences." |
| Restrict to a gene panel | "Only variants in BRCA1, BRCA2, TP53, PTEN, MLH1, and MSH2." |
| `DP > 20` and `GQ > 20` | "Exclude calls with read depth under 20 or genotype quality under 20." |
| ClinVar = Pathogenic / Likely Pathogenic | "List variants classified Pathogenic or Likely Pathogenic in ClinVar." |
| CADD > 20, REVEL > 0.7, or high DITTO | "Prioritize variants with CADD above 20 and a DITTO score above 0.8." |
| Zygosity = homozygous / compound het | "Show homozygous variants, and flag any gene with two or more heterozygous hits." |
| Sort by a column | "Sort those by DITTO score, highest first." |

The real power is **stacking these in one sentence**, the way you would chain filters:

> "In @samples:patient_042, list PASS variants with gnomAD AF below 0.001 and a HIGH or MODERATE consequence in any ACMG SF v3.2 gene, sorted by DITTO descending."

That single prompt is an entire filter cascade. The agent runs it, returns the surviving variants as a table, and tells you how many matched, so you can decide whether to tighten further or start reviewing.

!!! tip "Count before you list"
    Just like watching the variant counter in a filter panel, ask for a count first: *"How many variants match?"* If it is 4, list them. If it is 400, add another filter. The chat shows up to 100 results at a time, so this keeps output reviewable.

---

## A familiar workflow, reframed

Here is a standard diagnostic triage, the kind you would do by hand, run as a conversation. Notice that each step is a decision point you control; the agent only does the gathering between your prompts.

=== "Step 1: Narrow the field"

    > "In @samples:patient_042, show PASS variants with gnomAD AF below 0.001 and a HIGH or MODERATE consequence. How many are there?"

    *The agent runs the query and reports a count: your starting shortlist, the same one a filter cascade would produce.*

=== "Step 2: Add clinical context"

    > "The patient presents with early-onset breast and ovarian cancer. Of those variants, which fall in genes associated with hereditary breast and ovarian cancer?"

    *The agent intersects your shortlist with phenotype-relevant genes, the step where you would normally cross-reference a panel by hand.*

=== "Step 3: Gather the evidence"

    > "For the top candidate, summarize its ClinVar classification, gnomAD frequency, and any recent literature on its pathogenicity."

    *Instead of opening three tabs, you get ClinVar, gnomAD, and cited literature in one answer, each with the tool call shown so you can verify the source.*

=== "Step 4: Classify"

    > "Classify this variant using ACMG/AMP criteria based on the evidence above."

    *The agent proposes criteria and a classification with its reasoning. You review the evidence codes and adjust. The [ACMG classifier](../analysis/acmg-classification.md) is where you confirm and lock it in.*

=== "Step 5: Document"

    > "Flag this variant as Primary and add a comment summarizing the rationale."

    *The flag and note land on the variant in the table, building your audit trail as you go.*

Five prompts replace dozens of clicks and tab-switches. At every step you are the one reading the evidence and making the call; the agent just removed the busywork between decisions.

---

## When to use chat vs. the table

Neither replaces the other. A good rule of thumb:

<div class="grid-cards" markdown>

<div class="card" markdown>

### Reach for **chat** when…

- You want to narrow thousands of variants to a shortlist fast
- The question spans external evidence (ClinVar, literature, trials)
- You are exploring an open question ("what could explain this phenotype?")
- You want a written rationale you can paste into notes
- The task repeats across samples, so you can capture it as a [Playbook](../playbooks/index.md)

</div>

<div class="card" markdown>

### Reach for the **table** when…

- You want to eyeball every surviving row yourself
- You are doing precise column-by-column comparison
- You need to flag, comment, and classify in a tight loop
- You want to export an exact filtered view to a report
- You are confirming what the agent proposed

</div>

</div>

The most efficient pattern is **chat to narrow, table to confirm**: ask AIVA to reduce the field and explain its picks, then open [Tertiary Analysis](../analysis/tertiary-analysis.md) to review, flag, and sign off. The floating chat bubble lives inside the table view, so you never leave your data to ask a follow-up.

---

## Trust, but verify

The most common onboarding worry is fair: *"How do I know the agent is right?"* You verify it the same way you would verify a junior analyst's shortlist, and AIVA is built to make that easy.

- **The tool calls are visible.** When AIVA queries your data or looks up ClinVar, it shows the tool it used and a summary of what it ran. You are never reading an unsourced claim; you can see where every number came from.
- **Ask for the source.** *"Which ClinVar submission supports that?"* or *"Show me the query you ran."* The agent will surface the underlying evidence and the exact filter it applied.
- **Cross-check in the table.** Anything the agent shortlists, you can reproduce as a filter in the table view and confirm row for row. The two views query the same data.
- **You own the classification.** AIVA proposes ACMG criteria; it does not finalize them. The [ACMG classifier](../analysis/acmg-classification.md) and report sign-off remain your decision and your signature.

!!! warning "AIVA accelerates evidence-gathering, not clinical judgment"
    Treat AIVA's output as a well-organized evidence package from a fast assistant, not a verdict. Every classification and every reported finding still passes through your review. The audit trail (tool calls, flags, comments, and ACMG worksheets) exists precisely so the work is defensible.

---

## Common onboarding mistakes

| Mistake | Do this instead |
|---|---|
| Prompts too vague ("show me the important variants") | Name genes, thresholds, and consequences, just like a filter |
| Forgetting to attach the sample | Type `@` and select your sample so the agent knows what to query |
| Asking for a 500-row list in chat | Count first, tighten filters, then list, or switch to the table |
| Treating the answer as final | Ask for sources and confirm in the table before reporting |
| Re-typing the same multi-step triage each time | Save it as a [Playbook](../playbooks/index.md) and reuse it per sample |
| Abandoning the table | Use chat to narrow, the table to review and sign off |

---

## Next steps

<div class="grid-cards" markdown>

<div class="card" markdown>

### Prompting guide

Worked examples, prompt chaining, and patterns for multi-sample and clinical-data workflows.

[:octicons-arrow-right-24: Prompting guide](../prompting-guide/index.md)

</div>

<div class="card" markdown>

### Tertiary analysis

The filterable table view, variant flagging, comments, and the floating chat assistant.

[:octicons-arrow-right-24: Table view](../analysis/tertiary-analysis.md)

</div>

<div class="card" markdown>

### Playbooks

Turn a triage workflow you repeat into a one-click, shareable analysis.

[:octicons-arrow-right-24: Playbooks](../playbooks/index.md)

</div>

</div>
