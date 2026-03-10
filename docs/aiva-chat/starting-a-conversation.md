---
title: Starting a Conversation
description: How to create, search, rename, and manage AIVA Chat conversations in AIVA.
---

# Starting a Conversation

AIVA Chat organizes your interactions into conversations. Each conversation maintains its own history and context, making it easy to keep different analyses separate and return to previous work.

---

## Creating a New Conversation

There are two ways to start a new conversation:

### From the Sidebar

1. Navigate to the **Chat** tab in the header navigation bar.
2. In the conversation sidebar on the left, click the **New Conversation** button at the top.
3. A new, empty conversation opens in the main chat area.
4. Type your first message and press ++enter++ to begin.

### By Typing Directly

If no conversation is currently active, simply type your question into the message input field and press ++enter++. A new conversation is created automatically with your first message.

!!! tip "One topic per conversation"
    For the best results, keep each conversation focused on a single analysis topic or sample. AIVA uses the full conversation history as context, so mixing unrelated topics in one conversation can reduce the relevance of responses. Start a new conversation when you switch to a different analysis task.

---

## The Conversation Sidebar

The sidebar on the left side of the Chat page lists all your conversations, organized by recency. It provides several features for managing your conversation history.

### Browsing Conversations

Conversations are listed with their title and a timestamp. Click any conversation to load it in the main chat area. The full message history is restored, including all tool results, tables, and charts.

### Searching Conversations

Use the **search bar** at the top of the sidebar to find past conversations by keyword. The search matches against conversation titles, helping you locate specific analyses quickly.

!!! info "Search scope"
    The sidebar search filters conversations by title. If you need to find a specific message or result within a conversation, open the conversation and use your browser's built-in find feature (++ctrl+f++ or ++cmd+f++).

### Renaming Conversations

By default, new conversations are titled based on their first message. To assign a more descriptive name:

1. Hover over the conversation in the sidebar.
2. Click the **rename** option (or right-click for the context menu).
3. Enter a new title and confirm.

Descriptive titles such as "BRCA Panel Analysis - Patient 042" or "gnomAD Frequency Review" make it much easier to return to specific work later.

### Deleting Conversations

To remove a conversation you no longer need:

1. Hover over the conversation in the sidebar.
2. Click the **delete** option (or right-click for the context menu).
3. Confirm the deletion when prompted.

!!! warning "Deletion is permanent"
    Deleted conversations cannot be recovered. All messages, tool results, charts, and generated content within the conversation are permanently removed. Make sure you have exported or saved any important results before deleting.

---

## Conversation Context

AIVA maintains awareness of the full conversation history. This means you can:

- **Ask follow-up questions** without repeating context. For example, after asking "What pathogenic variants are in BRCA1?", you can follow up with "Show me the allele frequencies for those" -- AIVA understands "those" refers to the BRCA1 variants from the previous answer.

- **Refine results iteratively**. Start with a broad question, then narrow down. For example: "List all missense variants" followed by "Filter those to only variants with CADD score above 25."

- **Reference previous tool outputs**. If AIVA generated a table or chart earlier in the conversation, you can refer back to it in subsequent questions.

!!! note "Context window limits"
    Very long conversations may eventually exceed the language model's context window. If you notice responses becoming less accurate or losing track of earlier context, consider starting a new conversation and re-establishing the relevant context in your first message.

---

## Selecting a Sample for Analysis

When you ask AIVA a question about "your data," it needs to know which sample to query. There are several ways to establish this:

- **Mention the sample by name** in your message (e.g., "In the BRCA_panel sample, how many variants are there?").
- **Open Chat from a sample**. If you click the Chat action from within a data table view, a new conversation is created with that sample already in context.
- **Let AIVA ask**. If your question is about data but no sample is specified, AIVA may ask you to clarify which sample to query.

---

## Best Practices

- **Use descriptive first messages** to set the context. A first message like "I want to analyze the pathogenic variants in my WES sample for patient 042" gives AIVA a clear starting point.
- **Rename conversations** as soon as the topic becomes clear, especially if you maintain many active conversations.
- **Start fresh conversations** for unrelated analyses rather than continuing in an existing thread.
- **Review tool outputs** when AIVA shows what tool it used and the query it ran. This transparency helps you verify that the analysis is correct.

---

## Next Steps

- [:octicons-arrow-right-24: Query your uploaded data](querying-data.md)
- [:octicons-arrow-right-24: Explore all AI tools](ai-tools.md)
- [:octicons-arrow-right-24: See example workflows](example-workflows.md)
- [:octicons-arrow-right-24: Choose a language model](model-selection.md)
