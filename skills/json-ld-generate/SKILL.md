---
name: json-ld-generate
description: Generate JSON-LD structured data for web content. Maps content to Schema.org types to improve search engine understanding and rich result eligibility.
required_roles:
  scribe: roles/scribe.editor
personas: [seo-specialist, content-strategist, web-developer]
---

# Generate JSON-LD Skill

Generate valid JSON-LD (JavaScript Object Notation for Linked Data) markup for web pages. This skill analyzes content and maps it to specific Schema.org definitions, creating structured data blocks ready for insertion into HTML.

## Inputs

- `CONTENT` - The content text or file path to analyze.
- `SCHEMA_TYPE` - (Optional) The target Schema.org type (e.g., "Article", "FAQPage", "Product", "Person"). If not provided, the skill attempts to infer it.
- `CONTEXT_URL` - (Optional) The base schema context URL (default: "https://schema.org").
- `VALIDATE` - (Optional) Boolean, whether to validate required fields for the chosen type (default: true).

## Workflow

### Step 1: Type Identification

If `SCHEMA_TYPE` is not provided, analyze `CONTENT` to determine the most appropriate Schema.org type.
- **Article/BlogPosting**: Text with headline, author, date.
- **FAQPage**: List of questions and answers.
- **Product**: Name, price, description, SKU.
- **Event**: Name, date, location.

### Step 2: Entity Extraction

Extract relevant properties from the `CONTENT` based on the target type.
- **Common Properties**: `name`, `description`, `url`, `image`.
- **Type-Specific**:
    - *Article*: `headline`, `author`, `datePublished`.
    - *Product*: `offers`, `aggregateRating`, `brand`.
    - *FAQPage*: `mainEntity` (Question/Answer array).

### Step 3: Structure Construction

Construct the JSON object following JSON-LD syntax.
- Include `@context`: "https://schema.org".
- Include `@type`: The determined type.
- Nest objects correctly (e.g., `author` as a Person object).

### Step 4: Output Generation

Serialize the object to a JSON string wrapped in a `<script type="application/ld+json">` tag.

## Required Outputs

A `JSON_LD_BLOCK` string.

**Example:**
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Understanding Semantic Web",
  "author": {
    "@type": "Person",
    "name": "Jane Doe"
  },
  "datePublished": "2023-10-27"
}
</script>
```

## Quick Reference

- **Purpose**: Enhance SEO and enable rich results (snippets) in search engines.
- **Tools**: Google Rich Results Test, Schema.org Validator.
