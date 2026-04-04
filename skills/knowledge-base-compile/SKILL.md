---
name: knowledge-base-compile
description: Incremental compiler that takes raw source documents (articles, papers, datasets) and generates a structured Markdown knowledge base wiki.
required_roles:
  scribe: roles/scribe.editor
personas: [researcher, knowledge-manager, content-strategist]
---

# Compile Knowledge Base Skill

An incremental compiler for personal knowledge bases. It ingests raw data such as downloaded articles, papers, code repos, datasets, and images (e.g., from an Obsidian Web Clipper) and produces a well-structured, interconnected Markdown wiki.

## Inputs

- `RAW_DIR` - The directory containing raw source materials (markdown, text, PDFs, images).
- `WIKI_DIR` - The destination directory for the compiled Markdown knowledge base.

## Workflow

### Step 1: Ingest & Summarize
- Scan the `RAW_DIR` for new or updated source documents.
- Generate a brief summary and extract key metadata for each source document.
- Ensure any local images or assets are properly linked and referenced.

### Step 2: Categorization & Concept Extraction
- Identify key concepts, entities, and themes across the newly ingested documents.
- Categorize these documents into existing topics or propose new categories.

### Step 3: Article Generation
- For significant concepts, synthesize the raw data into cohesive, standalone Markdown articles.
- Merge insights from new raw data into existing wiki articles incrementally.

### Step 4: Interlinking (Backlinks)
- Establish bidirectional links (backlinks) between the new concept articles and existing articles.
- Update index files and maps of content (MOCs) to reflect the new structure.

## Required Outputs

- **Compiled Wiki Pages**: A collection of structured `.md` files in the `WIKI_DIR`.
- **Index Files**: Maintained structural entry points (e.g., `Home.md`, `Concepts.md`).
- **Compilation Log**: A brief summary of what documents were ingested, what concepts were extracted, and what articles were updated or created.

## Quick Reference

- **Purpose**: Transform a messy folder of raw bookmarks and articles into a heavily interlinked, cleanly structured personal knowledge base.
- **Outcome**: An Obsidian-ready Markdown wiki that is easily navigable and ready for advanced Q&A.