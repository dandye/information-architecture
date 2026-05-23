---
name: document-tree-generate
description: Transform lengthy documents into a semantic tree structure. It extracts sections, summaries, and hierarchies optimized for use with Large Language Models (LLMs).
required_roles:
  scribe: roles/scribe.editor
personas: [information-architect, document-analyst, knowledge-manager]
---

# Generate Document Tree Skill

Transform lengthy documents (e.g., PDFs, Markdown files) into a semantic **tree structure**, similar to a "table of contents" but optimized for context-aware Retrieval-Augmented Generation (RAG) and use with Large Language Models (LLMs). This skill is inspired by approaches like PageIndex to structure dense documents into hierarchical nodes.

## Inputs

- `DOCUMENT_PATH` - The path to the document to process (e.g., PDF or Markdown file).
- `MODEL` - (Optional) The LLM model to use for summarization and structuring (default: "gpt-4o").
- `MAX_PAGES_PER_NODE` - (Optional) Maximum number of pages per node for pagination boundaries (default: 10).
- `MAX_TOKENS_PER_NODE` - (Optional) Maximum tokens allowed per hierarchical node (default: 20000).
- `INCLUDE_NODE_SUMMARY` - (Optional) Boolean, whether to generate and include a summary for each node (default: true).
- `TOC_CHECK_PAGES` - (Optional) Number of pages at the beginning of the document to check for an existing Table of Contents (default: 20).

## Workflow

### Step 1: Document Parsing & Text Extraction

Read the document specified by `DOCUMENT_PATH`.
- If it's a PDF, extract text page by page.
- If it's a Markdown file, parse headers (e.g., `#`, `##`, `###`) to determine heading levels and hierarchy.
- Optionally detect an existing Table of Contents within the first `TOC_CHECK_PAGES`.

### Step 2: Semantic Chunking & Hierarchy Building

Divide the extracted text into semantic chunks based on document structure (headings) and length constraints (`MAX_PAGES_PER_NODE`, `MAX_TOKENS_PER_NODE`).
- Build a hierarchical tree where major sections become parent nodes and subsections become child nodes.
- Ensure each node maintains start and end indices (either page numbers or line/token offsets) to map back to the original document.

### Step 3: Node Summarization

For each node in the tree, generate a concise summary of its contents using the specified `MODEL`.
- This step is executed if `INCLUDE_NODE_SUMMARY` is true.
- Summaries help LLMs quickly determine if a node contains relevant context for answering a query.

### Step 4: Tree Output Generation

Format the finalized hierarchical tree into the requested output structure.

## Required Outputs

A `DOCUMENT_TREE_OUTPUT` string containing the semantic tree in a structured JSON format (JSONC).

**Example:**
```jsonc
{
  "title": "Financial Stability",
  "node_id": "0006",
  "start_index": 21,
  "end_index": 22,
  "summary": "The Federal Reserve monitors and addresses risks to financial stability...",
  "nodes": [
    {
      "title": "Monitoring Financial Vulnerabilities",
      "node_id": "0007",
      "start_index": 22,
      "end_index": 28,
      "summary": "The Federal Reserve's framework for monitoring vulnerabilities in the financial system..."
    },
    {
      "title": "Domestic and International Cooperation",
      "node_id": "0008",
      "start_index": 28,
      "end_index": 31,
      "summary": "In 2023, the Federal Reserve collaborated with domestic and international agencies..."
    }
  ]
}
```

## Quick Reference

- **Purpose**: Transform long documents into an LLM-friendly semantic tree for vectorless RAG or efficient context retrieval.
- **Tools**: Compatible with tools that process complex documents, reports, and manuals.
