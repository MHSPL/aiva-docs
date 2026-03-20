---
title: Creating Playbooks
description: Write custom AIVA playbooks with step-by-step AI instructions for standardized genomic analysis workflows.
---

# Creating Playbooks

Create custom playbooks to automate your analysis workflows. A playbook contains step-by-step instructions that guide the AIVA AI assistant through a structured analysis sequence.

---

## Creating a New Playbook

1. Navigate to the **Playbooks** section.
2. Click **New Playbook**.
3. Enter a **title** and **description** for the playbook.
4. Begin adding steps.

---

## Writing Playbook Steps

Each step in a playbook is an instruction that tells AIVA what to do. Steps are executed in order.

### Step Structure

Each step includes:

- **Step title**: A short label describing the step (e.g., "Identify pathogenic variants").
- **Instruction**: The detailed instruction for the AI. Write this as you would write a prompt in AIVA Chat.
- **Expected tool** (optional): Indicate which tool the step should use (Genomic Data Query, Variant Annotation, Biomedical Literature, etc.). This is a hint for the AI but not a hard requirement.
- **Output format** (optional): Specify how the results should be presented (table, list, summary, chart).

### Example Steps

**Step 1: Sample Overview**

- Title: "Get sample overview"
- Instruction: "Provide a summary of this sample including total variant count, breakdown by variant type and consequence, and the number of variants per chromosome."

**Step 2: Identify Pathogenic Variants**

- Title: "Find pathogenic variants"
- Instruction: "List all variants classified as Pathogenic or Likely Pathogenic in ClinVar. Include the gene, variant position, consequence, ClinVar classification, and gnomAD allele frequency."

**Step 3: Literature Evidence**

- Title: "Search for supporting literature"
- Instruction: "For each pathogenic variant found in the previous step, search for publications supporting the pathogenicity classification. Summarize the key findings."

**Step 4: Generate Summary**

- Title: "Create findings summary"
- Instruction: "Summarize the analysis in a structured format with sections for: key findings, clinical implications, and recommended next steps."

---

## Best Practices for Writing Steps

- **Be specific**: "List all missense variants with CADD > 20 and gnomAD AF < 0.001" is better than "Find important variants."
- **Reference previous steps**: Steps can build on results from earlier steps. Use phrases like "For each variant found in the previous step..." to chain analyses.
- **Specify output format**: Tell AIVA whether you want a table, a list, a paragraph summary, or a chart.
- **Include context**: If a step requires domain knowledge, include it in the instruction. For example: "Classify the variant using ACMG criteria. Consider PP3 (computational evidence supports a deleterious effect) if CADD > 25."
- **Keep steps focused**: Each step should accomplish one task. Split complex analyses into multiple steps for clarity.

---

## Managing Playbook Versions

Playbooks support version control:

- **Save as draft**: Work on a playbook without publishing it.
- **Publish**: Make the playbook available for use (and optionally visible in the marketplace).
- **Version history**: Each published version is tracked. You can view the change history and revert to a previous version.
- **Edit and republish**: Update a published playbook by editing it and publishing a new version.

!!! note "Version numbering"
    Versions are numbered sequentially (v1, v2, v3, etc.). When you fork another user's playbook, version numbering starts fresh on your copy.

---

## Testing a Playbook

Before sharing a playbook:

1. Click **Test** in the playbook editor.
2. Select a sample to run the playbook against.
3. Watch AIVA execute each step.
4. Review the results for accuracy, completeness, and formatting.
5. Adjust steps as needed and re-test.

---

## Organizing Playbooks

Your personal playbook library shows all playbooks you have created or forked. You can:

- **Search** playbooks by title or content.
- **Filter** by status (draft, published, archived).
- **Archive** playbooks you no longer use.
- **Duplicate** a playbook to create a variant for a different use case.
