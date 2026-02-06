---
name: semantic-validate
description: Validate existing JSON-LD or Microdata in documents against Schema.org standards to ensure correctness and search engine readability.
required_roles:
  scribe: roles/scribe.editor
personas: [seo-specialist, web-developer, qa-engineer]
---

# Semantic Validator Skill

Parse and validate semantic markup (JSON-LD, Microdata, RDFa) within documents to ensure adherence to Schema.org standards and Google Structured Data guidelines.

## Inputs

- `PATH` - The document containing markup to validate.
- `STRICT` - (Optional) Boolean, whether to enforce strict schema compliance (default: true).

## Workflow

1.  **Parse**: Extract structured data blocks from the document at `PATH`.
2.  **Validate**: Check against Schema.org definitions for:
    - Required properties for the specific type.
    - Data type validity (e.g., Dates, URLs).
    - Nesting correctness.
3.  **Report**: Output a list of errors, warnings, and valid entities found.

## Output

A report detailing:
- **Valid Entities**: Types and counts found.
- **Errors**: Critical issues preventing valid parsing.
- **Warnings**: Recommended properties missing or potential issues.
