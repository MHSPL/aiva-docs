---
title: Filters to Prompts Cheat Sheet
description: A one-minute cheat sheet for users moving from manual filter-and-table variant interpretation to agentic analysis with AIVA. The filters you know, written as prompts.
hide:
  - toc
---

# Filters to prompts: the 1-minute version

Used to interpreting variants with filters and tables? You already know how to use AIVA. The one habit to change:

!!! tip "The only rule"
    **Describe the variants you want. Do not rebuild the filter steps.** AIVA writes the query, gathers the evidence, and shows its work, so you spend your time deciding instead of clicking.

---

## Your filters, as prompts

Attach your sample first (type `@` and pick it), then ask:

| You would filter for | Just say |
|---|---|
| `FILTER = PASS` | "Keep only variants that PASS quality filters." |
| `gnomAD AF < 0.01` | "Show rare variants under 1% population frequency." |
| Missense / frameshift / stop-gained | "Limit to missense, frameshift, and stop-gained." |
| A gene panel | "Only variants in BRCA1, BRCA2, TP53, PTEN." |
| ClinVar Pathogenic / Likely Pathogenic | "List Pathogenic and Likely Pathogenic variants." |
| Stack several at once | "List PASS variants under 0.1% frequency with HIGH impact in BRCA1, BRCA2." |

---

## Try these right now

These are the same starters you see on the new-chat screen. Click into the chat and paste one:

> "list rare pathogenic variants in @sample:"

> "show PASS variants with gnomAD allele frequency below 0.01 in @sample:"

> "how many PASS variants with gnomAD AF below 0.001 and HIGH or MODERATE impact are in @sample:?"

!!! note "Count first, then list"
    Just like watching a variant counter, ask "how many?" before "list them." If the count is small, list it. If it is large, add another filter.

---

## The loop you already know

1. **Narrow** with a prompt (replaces your filter cascade).
2. **Review** the agent's shortlist and its cited evidence.
3. **Confirm** in the table view, then flag, classify, and sign off.

The variant table is still there. Use chat to narrow the field fast, then open the table to review row by row.

---

Want the full walkthrough, including a worked diagnostic review and how to verify the agent's answers? Read [From Filters to Prompts: in depth](prompting-guide/from-filters-to-prompts.md).
