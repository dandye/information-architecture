# Information Architecture Skills for Gemini CLI

A collection of skills for Information Architecture tasks, designed to help with content analysis, organization, and strategy.

## Available Skills

### Content Analysis & Strategy

- **[content-analyze-gaps](skills/content-analyze-gaps/SKILL.md)**
  Identify content gaps and organizational opportunities. Analyzes missing content areas, redundancies, and consolidation opportunities.

- **[content-audit](skills/content-audit/SKILL.md)**
  Comprehensive content quality and maintenance assessment. Evaluates documentation quality, relevance, maintenance needs, and provides actionable recommendations.

- **[content-inventory](skills/content-inventory/SKILL.md)**
  Systematic cataloging of information assets. Creates comprehensive inventories of all content with metadata and characteristics.

- **[semantic-markup-generate](skills/semantic-markup-generate/SKILL.md)**
  Generate semantic web markup (JSON-LD, Schema.org) for documents. Enhances SEO and machine readability.

- **[semantic-extract](skills/semantic-extract/SKILL.md)**
  Extract structured data from existing HTML/Markdown content. Identify existing tables, lists, and metadata.

- **[semantic-validate](skills/semantic-validate/SKILL.md)**
  Validate existing JSON-LD or Microdata against Schema.org standards. Ensure markup correctness for search engines.

- **[knowledge-graph-generate](skills/knowledge-graph-generate/SKILL.md)**
  Analyze multiple documents to identify entities and relationships, constructing a knowledge graph structure.

- **[ontology-map](skills/ontology-map/SKILL.md)**
  Map local tags/categories to formal ontologies like SKOS to improve interoperability.

- **[vocabulary-overlap-analysis](skills/vocabulary-overlap-analysis/SKILL.md)**
  Analyze vocabulary overlap and identify named entities unique to domain/document corpora.

### Information Architecture

- **[metadata-schema-design](skills/metadata-schema-design/SKILL.md)**
  Design comprehensive metadata frameworks. Develops structured metadata templates and tagging systems.

- **[sitemap-generate](skills/sitemap-generate/SKILL.md)**
  Generate hierarchical site structure and navigation maps. Creates visual representations of information architecture and content relationships.

- **[taxonomy-generate](skills/taxonomy-generate/SKILL.md)**
  Develop hierarchical classification systems. Creates parent-child categorical structures for content organization.

- **[thesaurus-generate](skills/thesaurus-generate/SKILL.md)**
  Generate controlled vocabulary thesaurus for content domains. Creates comprehensive thesauri with preferred terms, broader/narrower/related terms.

## Capabilities

This extension provides a suite of Information Architecture tools designed to help you analyze, organize, and structure content effectively.

- **Content Strategy**: Analyze content gaps, audit quality, and inventory assets.
- **Structural Design**: Generate sitemaps and design metadata schemas.
- **Classification**: Develop taxonomies and thesauri for consistent categorization.

## Commands

| Command | Description | Skill |
| :--- | :--- | :--- |
| `/ia:gaps` | Identify content gaps and organizational opportunities. | [content-analyze-gaps](skills/content-analyze-gaps/SKILL.md) |
| `/ia:audit` | Comprehensive content quality and maintenance assessment. | [content-audit](skills/content-audit/SKILL.md) |
| `/ia:inventory` | Systematic cataloging of information assets. | [content-inventory](skills/content-inventory/SKILL.md) |
| `/ia:metadata` | Design comprehensive metadata frameworks. | [metadata-schema-design](skills/metadata-schema-design/SKILL.md) |
| `/ia:sitemap` | Generate hierarchical site structure and navigation maps. | [sitemap-generate](skills/sitemap-generate/SKILL.md) |
| `/ia:taxonomy` | Develop hierarchical classification systems. | [taxonomy-generate](skills/taxonomy-generate/SKILL.md) |
| `/ia:thesaurus` | Generate controlled vocabulary thesaurus for content domains. | [thesaurus-generate](skills/thesaurus-generate/SKILL.md) |
| `/ia:semantic` | Generate semantic web markup (JSON-LD, Schema.org) for documents. | [semantic-markup-generate](skills/semantic-markup-generate/SKILL.md) |
| `/ia:semantic-extract` | Extract structured data from existing HTML/Markdown content. | [semantic-extract](skills/semantic-extract/SKILL.md) |
| `/ia:semantic-validate` | Validate existing JSON-LD or Microdata against Schema.org standards. | [semantic-validate](skills/semantic-validate/SKILL.md) |
| `/ia:knowledge-graph-generate` | Analyze multiple documents to extract entities and relationships. | [knowledge-graph-generate](skills/knowledge-graph-generate/SKILL.md) |
| `/ia:ontology-map` | Map local content tags/categories to formal ontologies (SKOS). | [ontology-map](skills/ontology-map/SKILL.md) |
| `/ia:vocab-overlap` | Analyze vocabulary overlap and identify named entities unique to domain/document corpora. | [vocabulary-overlap-analysis](skills/vocabulary-overlap-analysis/SKILL.md) |
