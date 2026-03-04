---
name: variants-find
description: Identify duplicative documents in a corpus or directory tree. De-dupe them by determining which should be canonical and which should be deprecated, or analyze missing topics if both are correct variants.
required_roles:
  scribe: roles/scribe.viewer
personas: [information-architect, content-strategist, documentation-manager]
---

# Find Document Variants Skill

Identify duplicative documents in a corpus or directory tree. This skill helps de-dupe content by determining which document should be the canonical version and which should be deprecated (e.g., an external blog post vs. an internal gDoc, or a main documentation page vs. a local gDoc). If both variants are determined to be correct and serve different purposes, it analyzes what topics are missing from each to ensure comprehensive coverage across both.

## Inputs

- `CORPUS_PATH` - The path to the corpus or directory tree to analyze for variants.
- `CANONICAL_RULES` - (Optional) Rules or guidelines to determine which variant should be canonical (e.g., "docs pages should be canonical over local gDocs").

## Workflow

### Step 1: Identify Variants

Scan the `CORPUS_PATH` to identify documents that are substantially similar or duplicative.
- Use text similarity metrics to group related documents.
- Flag groups of documents that appear to be variants of the same core content.

### Step 2: Canonical vs. Deprecated Analysis

For each group of variants, apply `CANONICAL_RULES` to determine the relationships between the documents.
- Identify the **Canonical** document: The primary, most authoritative version.
- Identify **Deprecated** documents: Versions that should be phased out or redirected to the canonical version.

### Step 3: Gap Analysis for Correct Variants

If multiple documents in a variant group are deemed to be "correct" (e.g., they serve distinct audiences or use cases like an internal vs. external guide), compare their content.
- Identify topics present in Variant A but missing in Variant B.
- Identify topics present in Variant B but missing in Variant A.

### Step 4: Recommendations

Generate actionable recommendations for handling each variant group.

## Required Outputs

A `VARIANTS_ANALYSIS_REPORT` in markdown format containing:
- **Variant Groups**: A list of document groups identified as duplicative.
- **De-duplication Actions**: Recommendations on which documents to mark as canonical and which to deprecate.
- **Gap Analysis**: For correctly identified distinct variants, a list of missing topics from each.

## Quick Reference

- **Purpose**: Consolidate redundant content and ensure comprehensive coverage across valid variants.
- **Outcome**: Actionable de-duplication and gap analysis report.
