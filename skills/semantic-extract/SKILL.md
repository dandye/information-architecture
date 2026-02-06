---
name: semantic-extract
description: Extract structured data and entities from existing HTML, Markdown, or text files to audit metadata availability.
required_roles:
  scribe: roles/scribe.editor
personas: [content-strategist, data-analyst]
---

# Semantic Extractor Skill

Parse documents to identify and extract existing structured data (tables, lists, headers) and potential entities, converting them into a raw structured format for audit or migration.

## Inputs

- `PATH` - The source document to process.
- `OUTPUT_FORMAT` - (Optional) "json", "csv", "yaml" (default: "json").

## Workflow

1.  **Read**: Load content from `PATH`.
2.  **Identify**:
    - Locate HTML tables, definition lists, header hierarchies.
    - Detect key-value pairs (e.g., in frontmatter).
3.  **Extract**: Pull the raw data from these structures.
4.  **Format**: Convert the extracted data into the requested `OUTPUT_FORMAT`.

## Output

A structured object containing the extracted data, keyed by the source element (e.g., "Table 1", "Frontmatter").
