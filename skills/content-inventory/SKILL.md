---
name: content-inventory
description: Systematic cataloging of information assets. Creates comprehensive inventories or card sorting materials from content.
required_roles:
  scribe: roles/scribe.viewer
personas: [information-architect, content-manager, ux-researcher]
---

# Content Inventory Skill

Create a systematic catalog of information assets within a specified path. This skill builds a comprehensive inventory including metadata, file characteristics, and format analysis. It can also generate materials for card sorting studies.

## Inputs

- `PATH` - The directory or file path to inventory (e.g., "/documentation")
- `OUTPUT_FORMAT` - (Optional) The output format: "csv", "json", "markdown", "card-sort-csv", "card-sort-print" (default: "json")
- `METADATA_EXTRACTION` - (Optional) Boolean, whether to extract deep metadata (author, date, tags) (default: true)
- `FORMAT_ANALYSIS` - (Optional) Boolean, whether to analyze file formats and types (default: true)
- `SAMPLE_SIZE` - (Optional) Max number of items to include (useful for card sorting or large audits) (default: all)

## Workflow

### Step 1: Asset Discovery

Recursively scan the `PATH` to identify all files and assets.
- Record file paths, names, and sizes.
- Filter out administrative files.

### Step 2: Sampling (Optional)

If `SAMPLE_SIZE` is specified:
- Select a representative sample (e.g., top traffic, key sections, or random).
- Ensure coverage across the hierarchy.

### Step 3: Metadata Extraction & Formatting

Extract metadata based on `METADATA_EXTRACTION` and `OUTPUT_FORMAT`.
- **Standard Inventory**: Title, URL/Path, Author, Date, Type.
- **Card Sorting**:
    - **Label**: Clean, user-friendly title.
    - **Description**: Short summary/snippet.
    - **ID**: Unique identifier.

### Step 4: Output Generation

Compile the data into the requested `OUTPUT_FORMAT`.

## Required Outputs

A `CONTENT_REPORT` in the specified format.

**Example (Card Sort CSV):**
```csv
ID,Label,Description,Url
1,Reset Password,How to recover account,/auth/reset
2,Pricing,Subscription tiers,/pricing
```

## Quick Reference

- **Purpose**: Governance, Audit, and UX Research (Card Sorting).
- **Use Case**: Migration planning, creating datasets for OptimalSort/Maze.
