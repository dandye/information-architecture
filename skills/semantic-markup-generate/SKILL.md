---
name: semantic-markup-generate
description: Generate semantic web markup (JSON-LD, Schema.org) for documents. Enhances SEO and machine readability by extracting entities and structural data.
required_roles:
  scribe: roles/scribe.editor
personas: [information-architect, seo-specialist, web-developer]
---

# Generate Semantic Markup Skill

Analyze content to identify entities, relationships, and structural data, then generate valid Schema.org semantic markup (JSON-LD) to improve search engine visibility and machine understanding.

## Inputs

- `PATH` - The document or content to analyze (e.g., "/blog/post-1.md")
- `TYPE` - (Optional) The specific Schema.org type to generate (e.g., "Article", "Product", "Event", "FAQPage"). If omitted, infer from content.
- `OUTPUT_FORMAT` - (Optional) Format of the markup: "json-ld", "microdata", "rdfa" (default: "json-ld")
- `VALIDATE` - (Optional) Boolean, whether to validate against Schema.org constraints (default: true)

## Workflow

### Step 1: content Type Analysis

Analyze the document at `PATH` to determine its primary content type.
- Map content patterns to valid Schema.org types (e.g., Recipe, HowTo, TechArticle).
- If `TYPE` is provided, verify content suitability for that type.

### Step 2: Entity & Property Extraction

Extract relevant properties for the determined type.
- **Core Properties**: Name, Description, Image, Author, DatePublished.
- **Type-Specific Properties**:
    - *Product*: SKU, Price, Availability, Review.
    - *Event*: StartDate, Location, Organizer.
    - *Article*: Headline, Publisher, MainEntityOfPage.
- **Relationships**: Identify referenced entities (e.g., Organization, Person) to nest within the markup.

### Step 3: Markup Generation

Construct the semantic data structure in the requested `OUTPUT_FORMAT`.
- Ensure proper nesting of complex objects.
- Use full URIs (https://schema.org/Type) where appropriate context is needed, or define context.

### Step 4: Validation

If `VALIDATE` is true, check against:
- Google Structured Data requirements.
- Schema.org mandatory properties.
- Data type correctness (e.g., ISO 8601 for dates).

## Required Outputs

A `SEMANTIC_MARKUP_BLOCK` containing the generated code.

**Example (JSON-LD):**
```json
{
  "@context": "https://schema.org",
  "@type": "TechArticle",
  "headline": "How to Configure Gemini CLI",
  "datePublished": "2024-03-15",
  "author": {
    "@type": "Person",
    "name": "Jane Doe"
  }
}
```

## Quick Reference

- **Purpose**: Make content understandable to search engines and AI agents.
- **Standard**: Schema.org (Google's preferred standard).
- **Tools**: Validate using Google's Rich Results Test tool.
