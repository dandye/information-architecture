---
name: knowledge-base-lint
description: Perform health checks on the knowledge base to find inconsistencies, impute missing data, and suggest new article connections.
required_roles:
  scribe: roles/scribe.editor
personas: [knowledge-manager, information-architect]
---

# Knowledge Base Linting Skill

A maintenance utility that performs "health checks" over a compiled Markdown wiki. It incrementally cleans up the wiki to enhance data integrity, consistency, and interconnectedness.

## Inputs

- `WIKI_DIR` - The directory containing the compiled Markdown knowledge base.
- `WEB_SEARCH` - (Optional) Boolean, whether to allow the LLM to use web searches to impute missing data (default: true).

## Workflow

### Step 1: Consistency Check
- Scan the `WIKI_DIR` for broken links, orphaned pages (no backlinks), and inconsistent naming conventions.
- Identify contradictory statements or outdated facts across different articles.

### Step 2: Data Imputation
- Identify articles with missing critical metadata or incomplete sections.
- If `WEB_SEARCH` is true, perform targeted web searches to fill in the missing information.

### Step 3: Discovery & Connection
- Analyze the graph of the wiki to find "missing links" (articles that share strong thematic ties but are not linked).
- Propose new umbrella concepts or articles that could bridge disparate clusters of knowledge.

### Step 4: Maintenance Report Generation
- Compile the findings into an actionable report or directly apply non-destructive fixes.

## Required Outputs

- **Linting Report**: A `.md` file detailing errors found, data imputed, and suggested structural improvements.
- **Auto-fixes (Optional)**: Directly updated `.md` files in the `WIKI_DIR` where minor corrections (like broken links) were resolved.

## Quick Reference

- **Purpose**: Maintain the health, integrity, and usefulness of an evolving personal knowledge base.
- **Outcome**: A cleaner, more consistent, and more deeply connected wiki.