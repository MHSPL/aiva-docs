---
title: AI Auto-Fill
description: Use AIVA's AI to automatically generate report section content based on sample data, flagged variants, and analysis findings.
---

# AI Auto-Fill

AI Auto-Fill uses AIVA's AI assistant to generate content for report sections automatically. Instead of writing every section from scratch, you can let the AI draft content based on your sample data, flagged variants, comments, and classifications -- then review and refine as needed.

---

## How It Works

1. Open a report in the editor.
2. Navigate to the section you want to fill.
3. Click the **AI Auto-Fill** button on the section.
4. AIVA analyzes the associated sample data and generates content appropriate for that section type.
5. The generated content appears in the editor, where you can review, edit, and refine it.

!!! note "AI-generated content requires review"
    Auto-filled content is a draft. Always review and verify AI-generated text before finalizing the report, especially for clinical reports where accuracy is critical.

---

## What the AI Uses

When generating content, AIVA considers:

- **Sample metadata** -- Sample name, file type, upload date, and annotation status.
- **Variant data** -- Total variant counts, distributions by consequence, chromosome, and gene.
- **Flagged variants** -- Variants you have flagged with their flag types and associated notes.
- **ACMG classifications** -- Formal classifications applied to variants using [ACMG criteria](../analysis/acmg-classification.md).
- **Comments** -- [Threaded comments](../collaboration/threaded-comments.md) attached to variants.
- **Section context** -- The section type and title inform the tone and structure of the generated content.

---

## Section Types and Auto-Fill Behavior

| Section Type | What the AI Generates |
|--------------|-----------------------|
| **Summary / Overview** | High-level summary of the sample, total variant counts, and key findings. |
| **Methods** | Description of the analysis pipeline including upload format, annotation tools used, and filtering criteria. |
| **Results** | Detailed breakdown of variant findings, organized by clinical significance or gene. |
| **Variant Table** | Structured table of flagged variants with classifications, frequencies, and predictions. |
| **Interpretation** | Clinical interpretation of key findings with supporting evidence from annotations and literature. |
| **Recommendations** | Suggested next steps based on the findings (e.g., confirmatory testing, genetic counseling, clinical trial enrollment). |
| **References** | List of databases and literature sources consulted during analysis. |

---

## Customizing Auto-Fill Output

You can guide the AI's output by:

- **Editing the section title** -- A more specific title (e.g., "BRCA1/BRCA2 Variant Analysis" instead of "Results") produces more focused content.
- **Adding a prompt note** -- Some sections allow you to add a brief instruction for the AI (e.g., "Focus on pharmacogenomic implications").
- **Pre-filling partial content** -- If you write the first paragraph, the AI continues from where you left off, maintaining your tone and focus.

---

## Regenerating Content

If the auto-filled content does not meet your needs:

1. Click **Regenerate** on the section.
2. Optionally adjust the section title or prompt note.
3. AIVA generates a new draft.

Previous drafts are preserved in the section's version history.

---

## Best Practices

- **Fill sections in order** -- The AI can reference previously filled sections for consistency. Fill the Summary first, then Results, then Interpretation.
- **Link variants before auto-filling** -- [Link flagged variants](sample-linking.md) to the report before running Auto-Fill so the AI has access to your curated evidence.
- **Review all clinical statements** -- Verify classifications, population frequencies, and clinical significance statements against the source databases.
- **Use Auto-Fill as a starting point** -- The AI excels at drafting structured content and pulling together data. Your domain expertise is needed for final clinical judgment.

!!! warning "Clinical responsibility"
    AI Auto-Fill is a productivity tool, not a substitute for clinical expertise. The signing clinician or researcher is responsible for the accuracy and completeness of the final report.
