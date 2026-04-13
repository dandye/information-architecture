---
name: knowledge-base-qa
description: Conduct complex research Q&A against the compiled knowledge base, generating rich visual outputs (Markdown, Marp slides, Matplotlib images).
required_roles:
  scribe: roles/scribe.viewer
personas: [researcher, data-analyst, content-strategist]
---

# Knowledge Base Q&A Skill

An advanced querying agent that deeply reads a compiled Markdown wiki to answer complex research questions. It doesn't just return terminal text; it synthesizes the knowledge into structured, visual output formats suitable for IDEs like Obsidian.

## Inputs

- `WIKI_DIR` - The directory containing the compiled Markdown knowledge base.
- `QUERY` - The complex research question or analysis request.
- `OUTPUT_FORMAT` - (Optional) The desired format of the output: `markdown`, `marp` (slides), or `matplotlib` (data visualizations). Default is `markdown`.

## Workflow

### Step 1: Retrieval & Synthesis
- Read the index files, MOCs (Maps of Content), and document summaries within `WIKI_DIR`.
- Identify and deeply read the subset of articles relevant to the `QUERY`.
- Synthesize the findings across multiple documents, resolving any contradictory information.

### Step 2: Content Generation
- Structure the synthesized answer according to the requested `OUTPUT_FORMAT`.
- For `markdown`, generate a comprehensive, well-cited article.
- For `marp`, break the findings down into a slide deck presentation.
- For `matplotlib`, generate python code to visualize data trends found in the wiki.

### Step 3: Integration (Optional)
- Suggest where the new findings or synthesized document might be "filed" back into the `WIKI_DIR` to enhance the knowledge base.

## Required Outputs

- **Structured Output File**: The final answer rendered as a `.md` file, a `.md` file with Marp frontmatter, or a `.py`/`.png` file for matplotlib visualizations.
- **Source Citations**: Explicit links back to the specific wiki pages that informed the answer.

## Quick Reference

- **Purpose**: Extract deep, synthesized insights from a large personal knowledge base.
- **Outcome**: Rich, visual answers that can be integrated back into the wiki or used for presentations and reports.