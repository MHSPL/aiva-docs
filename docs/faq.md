---
title: Frequently Asked Questions
description: Answers to common questions about AIVA accounts, uploads, AI chat, data privacy, subscriptions, and troubleshooting.
---

# Frequently Asked Questions

Find answers to the most common questions about using AIVA. If your question is not covered here, contact support through the **Help** modal in the application header.

---

## Account and Billing

??? question "How do I create an account?"
    Visit the AIVA sign-up page and register using your email address. After signing up, verify your email address by clicking the link sent to your inbox. See [Account Setup](getting-started/account-setup.md) for a full walkthrough.

??? question "What subscription plans are available?"
    AIVA offers five tiers: **Free**, **Trial**, **Plus**, **Pro**, and **Enterprise**. Each tier provides progressively more features, more weekly credits, and additional AI capabilities. See [Subscription Tiers](getting-started/subscription-tiers.md) for a detailed comparison.

??? question "How do I upgrade my subscription?"
    Click the tier indicator in the top-right corner of the navigation bar, select **Manage Subscription**, select tier by clicking **Upgrade**, and follow the secure payment flow. Your new tier is activated immediately upon successful payment.

??? question "Can I try all features before paying?"
    Yes. The **Trial** tier gives you temporary access to the complete feature set. Signing up with a new email address will automatically grant you a trial.

??? question "What happens to my data if I downgrade?"
    Your data is never deleted when you change tiers. All previously uploaded samples, conversations, and analysis results remain accessible. However, data is only retained for 30 days when downgrading to the Free tier.

??? question "Is my payment information secure?"
    All payment processing is handled by Stripe, a PCI-DSS Level 1 certified payment processor. AIVA does not store your credit card information.

??? question "Do you offer institutional or enterprise pricing?"
    For teams larger than 10 users or organizations with custom requirements, contact us for enterprise pricing options. Reach out to tarun@mamidi.ai.

---

## File Uploads and Formats

??? question "What file formats does AIVA support?"
    AIVA supports the following formats:

    - **FASTQ** (`.fastq`, `.fastq.gz`): FASTQ format, including gzip-compressed files.
    - **VCF** (`.vcf`, `.vcf.gz`): Variant Call Format, including gzip-compressed files.
    - **CSV** (`.csv`): Comma-separated values with a header row.
    - **TSV** (`.tsv`, `.txt`): Tab-separated values with a header row.

    See [VCF Upload](samples/vcf-upload.md) for VCF/CSV/TSV uploads, or [Secondary Analysis](samples/secondary-analysis.md) for FASTQ files.

??? question "What are the file size limits?"
    Each upload consumes credits from your weekly allowance. Free accounts cannot upload. Check your credit balance via the usage indicator in the header, or see [Subscription Tiers](getting-started/subscription-tiers.md#credit-system) for credit costs and file size limits per tier.

??? question "Can I upload files from cloud storage?"
    Yes. Plus, Pro, Trial, and Enterprise accounts can import files directly from Google Cloud Storage (`gs://`), Amazon S3 (`s3://`), Azure Blob Storage (`az://`), or public HTTPS URLs. See [VCF Upload](samples/vcf-upload.md#cloud-url-import).

??? question "What is Small Variant Annotation?"
    Small Variant Annotation uses AIVA's annotation engine to annotate variants with multiple databases. When enabled during upload, it adds columns such as gene symbol, consequence type, SIFT and Ditto predictions, and more. It is available on Trial, Plus, Pro, and Enterprise tiers. See [VCF Upload](samples/vcf-upload.md#annotation-options-vcf-only).

??? question "Can I upload without annotation and annotate later?"
    Limited. You can upload files without Small Variant Annotation or Structural Variant Annotation and explore the raw data immediately. On-demand annotation only supports handful of variants at a time, use the AIVA Chat [Variant Annotation tool](aiva-chat/ai-tools.md#variant-annotation), which performs real-time lookups against ClinVar, gnomAD, CADD, SIFT, and PolyPhen.

??? question "My upload failed. What should I do?"
    Open the [Job Manager](samples/job-monitoring.md) and review the error message on the failed job. Common causes include unsupported file formats, malformed headers (VCF files must include the `#CHROM` line), insufficient credits or exceeding file size limits, or network interruptions during transfer. Fix the underlying issue and re-upload. Please reach out to tarun@mamidi.ai for more assistance.

??? question "Can I upload multiple files at once?"
    AIVA processes one file upload at a time. You can submit multiple uploads in sequence, and each will be queued and processed independently. Monitor all jobs in the [Job Manager](samples/job-monitoring.md).

---

## AIVA Chat

??? question "What is AIVA?"
    AIVA (AI assisted Variant Analysis) is our AI Clinical Analyst. It can query your uploaded samples, search biomedical literature, annotate variants, generate charts, explore gene-drug interactions, and more, all through natural language conversation. See [AIVA Chat](aiva-chat/index.md) for a full overview.

??? question "What tools does AIVA have access to?"
    AIVA has access to 10+ specialized tools: Genomic Data Query, Web Search, Variant Annotation (ClinVar, gnomAD, CADD, SIFT, PolyPhen), Biomedical Literature search, Code Interpreter, Knowledge Graph, Clinical Trials search, Phenotype-Gene Prioritization, MCP custom integrations, and Task Manager. See [AI Tools](aiva-chat/ai-tools.md) for details on each.

??? question "Can I control which tools AIVA uses?"
    Yes. You can enable or disable individual tools from the tool configuration panel in the chat input area. This lets you restrict AIVA to specific capabilities or reduce response latency.

??? question "Can I choose which AI model AIVA uses?"
    Yes. AIVA offers a selection of language models with different tradeoffs between speed, cost, and reasoning capability. See [Model Selection](aiva-chat/model-selection.md).

??? question "Can AIVA modify my data?"
    No. AIVA has read-only access to your sample data. It can query, analyze, and visualize your data but cannot insert, update, or delete rows.

??? question "Can AIVA access other users' data?"
    No. AIVA queries are scoped to samples you own or that have been shared with you through a [project](collaboration/projects.md). It cannot access data belonging to other accounts.

??? question "My conversation seems to lose context in long chats. What can I do?"
    Very long conversations may exceed the language model's context window, causing it to lose track of earlier messages. Either switch to a model with 1M token capacity (e.g., Gemini PRO models) or start a new conversation and re-establish the key context in your first message. Keeping conversations focused on a single topic also helps maintain coherence.

---

## Data Privacy and Security

??? question "Where is my data stored?"
    Uploaded files are processed and stored on AIVA's secure cloud infrastructure. Parsed variant data is stored in a secure database. RLS (Row Level Security) is enabled to ensure data isolation.

??? question "Who can access my data?"
    Only you can access your data by default. If you create a [project](collaboration/projects.md) and invite collaborators, they gain access to the samples assigned to that project based on their assigned role. AIVA staff do not access your data except as required for technical support with your explicit consent.

??? question "Is AIVA HIPAA compliant?"
    AIVA includes features designed for HIPAA compliance, including PHI detection and access controls. See [Compliance](compliance/index.md) for details on the security measures in place.

??? question "Can I delete my data?"
    Yes. You can delete samples and projects from the [samples](samples/managing-samples.md) and [projects](collaboration/projects.md) tabs. Deleted samples and their associated data (flags, comments, etc.) are permanently removed from the database.

??? question "Does AIVA send my data to external services?"
    When AIVA uses tools like Web Search, Biomedical Literature, or Clinical Trials, it sends search queries to external APIs, but it does **not** send your raw variant data. The Genomic Data Query tool runs queries locally against our database. Variant annotation lookups send individual variant identifiers (chromosome, position, alleles) to annotation services for lookup but do not transmit your full dataset.

---

## Subscription Features

??? question "What features are available on the Free tier?"
    The Free tier includes: limited AI chat queries per day, limited API access, and read-only access to the Playbooks marketplace. See [Subscription Tiers](getting-started/subscription-tiers.md) for the full comparison.

??? question "What do I gain by upgrading to Plus?"
    Plus adds: more weekly credits and higher query limits, clinical reports with AI auto-fill, API access, and advanced AI capabilities. See [Subscription Tiers](getting-started/subscription-tiers.md).

??? question "What is the difference between Plus and Pro?"
    Pro provides 10 credits per week and higher AI query limits, and includes standard support. All Plus features are included. Pro is designed for small to medium-sized teams.

??? question "What is the MCP integration?"
    The Model Context Protocol (MCP) allows you to connect AIVA to external tools and services that you configure. This enables custom workflows tailored to your specific bioinformatics pipeline. MCP is available on Trial, Plus, and Pro tiers. See [MCP Integration](aiva-chat/mcp/index.md).

---

## Troubleshooting

??? question "The table view is slow or unresponsive."
    AIVA's table view uses virtualized rendering and server-side pagination to handle datasets with millions of rows. If you experience slowness:

    - Check your internet connection. Data is fetched page by page from the server.
    - Try reducing the number of visible columns using the column visibility controls.
    - Close other browser tabs to free up memory.
    - If the issue persists, contact support with your browser version and dataset size.

??? question "AIVA is not responding or responses are very slow."
    Possible causes:

    - **High server load**: During peak usage, responses may take longer. Wait a moment and try again.
    - **Complex query**: Some queries (e.g., aggregations over millions of rows) require more processing time. AIVA will stream the response as it becomes available.
    - **Network issues**: SSE streaming requires a stable connection. If your connection is intermittent, responses may appear to stall. Refresh the page and try again.

??? question "I see an error about exceeding my usage limit."
    Your subscription tier determines your credit balance and AI query usage. Check your current usage via the usage indicator in the header. Credits reset every Sunday. To continue, either wait for your credits to reset or [upgrade your plan](getting-started/subscription-tiers.md).

??? question "Charts or plots are not rendering in the chat."
    AIVA generates charts using matplotlib in a sandboxed Python environment. If a chart fails to render:

    - The error message in the chat will indicate what went wrong.
    - Try rephrasing your request with more specific instructions (e.g., "Create a bar chart with matplotlib showing variant counts per chromosome").
    - If the issue persists, ask AIVA to provide the data as a table instead.

??? question "I cannot find a conversation I had previously."
    Use the search bar in the conversation sidebar to filter by title. If you cannot find the conversation, it may have been deleted. Deleted conversations cannot be recovered. Consider renaming important conversations with descriptive titles to make them easier to find in the future. You can also export the conversation as a html page.

??? question "My Small Variant Annotation job has been running for a long time."
    Small Variant Annotation processes each variant through the annotation pipeline. For large files (whole-genome VCFs with millions of variants), this can take a significant amount of time. The job continues processing in the background. Check the [Jobs](samples/job-monitoring.md) tab for the current status. If the job appears stuck in the same state for an extended period, it may have encountered an error. Contact support if needed.

??? question "How do I report a bug or request a feature?"
    Use the **Help** modal in the application header to access our slack channel. Include details about the issue: what you were trying to do, what happened, any error messages, and your browser/OS information.

---

## Still Have Questions?

If your question is not answered here, reach out through the **Help** modal in the AIVA header. You can also explore the full documentation:

- [:octicons-arrow-right-24: Getting Started](getting-started/index.md)
- [:octicons-arrow-right-24: Samples and Uploads](samples/index.md)
- [:octicons-arrow-right-24: AIVA Chat](aiva-chat/index.md)
- [:octicons-arrow-right-24: Table View](data-table/index.md)
- [:octicons-arrow-right-24: Collaboration](collaboration/index.md)
