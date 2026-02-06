---
name: card-sorting-generate
description: Generate materials for card sorting studies. Creates detailed lists of content items (cards) for user research and information architecture validation.
required_roles:
  scribe: roles/scribe.viewer
personas: [information-architect, ux-researcher, content-strategist]
---

# Generate Card Sorting Materials Skill

Prepare the materials necessary for a card sorting study. This skill analyzes content within a directory to generate a list of "cards" representing topics or pages, which can be used in open or closed card sorting exercises to validate categorization.

## Inputs

- `PATH` - The content source directory (e.g., "/help-center")
- `DEPTH` - (Optional) Depth of directory traversal to select cards (default: 2)
- `SAMPLE_SIZE` - (Optional) Maximum number of cards to generate (default: 50)
- `OUTPUT_FORMAT` - (Optional) Output format: "csv", "json", "print-ready" (default: "csv")

## Workflow

### Step 1: Content Scanning

Scan the `PATH` to identify potential content items.
- Filter out administrative files or non-content assets.
- Focus on "leaf" nodes (actual pages) or significant section headers.

### Step 2: Card Selection

Select a representative sample of content items.
- If total items > `SAMPLE_SIZE`, use a sampling strategy (e.g., top traffic, strategic importance, or random distribution) to reduce the set.
- Ensure coverage across different sections.

### Step 3: Card Formatting

Prepare the data for each card.
- **Label**: Clean, user-friendly title of the page/topic.
- **Description**: Short summary or snippet (for context).
- **ID**: Unique identifier (path or number).

### Step 4: Output Generation

Format the list into the requested `OUTPUT_FORMAT`.
- **CSV**: Compatible with tools like OptimalSort or Maze.
- **JSON**: Structured data for custom apps.
- **Print-Ready**: Formatted for printing and cutting (Markdown/HTML).

## Required Outputs

A `CARD_SORT_DATASET` in the specified `OUTPUT_FORMAT`.

**Example (CSV):**
```csv
ID,Label,Description,Url
1,How to Reset Password,Instructions for account recovery,/auth/reset
2,Pricing Plans,Overview of subscription tiers,/pricing
3,API Keys,Managing developer credentials,/settings/api
```

## Quick Reference

- **Purpose**: Prepare for user research to understand how users mentally model information.
- **Types**: Open Sort (users create categories) vs. Closed Sort (users sort into fixed categories).
- **Ideal Size**: 30-60 cards for an effective study.
