# Information Architecture Skills for Gemini CLI

A collection of skills for Information Architecture tasks, designed to help with content analysis, organization, and strategy.

## Available Skills

### Content Analysis & Strategy

- **[card-sorting-generate](skills/card-sorting-generate/SKILL.md)**
  Generate materials for card sorting studies. Creates detailed lists of content items (cards) for user research and information architecture validation.

- **[content-analyze-gaps](skills/content-analyze-gaps/SKILL.md)**
  Identify content gaps and organizational opportunities. Analyzes missing content areas, redundancies, and consolidation opportunities.

- **[content-audit](skills/content-audit/SKILL.md)**
  Comprehensive content quality and maintenance assessment. Evaluates documentation quality, relevance, maintenance needs, and provides actionable recommendations.

- **[content-inventory](skills/content-inventory/SKILL.md)**
  Systematic cataloging of information assets. Creates comprehensive inventories of all content with metadata and characteristics.

- **[json-ld-generate](skills/json-ld-generate/SKILL.md)**
  Generate JSON-LD structured data for web content. Maps content to Schema.org types to improve search engine understanding and rich result eligibility.

- **[semantic-markup-generate](skills/semantic-markup-generate/SKILL.md)**
  Generate semantic web markup (JSON-LD, Schema.org) for documents. Enhances SEO and machine readability.

### Knowledge Base Management

- **[knowledge-base-compile](skills/knowledge-base-compile/SKILL.md)**
  Incremental compiler that takes raw source documents and generates a structured Markdown knowledge base wiki.

- **[knowledge-base-lint](skills/knowledge-base-lint/SKILL.md)**
  Perform health checks on the knowledge base to find inconsistencies, impute missing data, and suggest new article connections.

- **[knowledge-base-qa](skills/knowledge-base-qa/SKILL.md)**
  Conduct complex research Q&A against the compiled knowledge base, generating rich visual outputs (Markdown, Marp slides, Matplotlib images).

### Information Architecture

- **[document-tree-generate](skills/document-tree-generate/SKILL.md)**
  Transform lengthy documents into a semantic tree structure. Optimized for context-aware Retrieval-Augmented Generation (RAG) and LLM usage.

- **[metadata-schema-design](skills/metadata-schema-design/SKILL.md)**
  Design comprehensive metadata frameworks. Develops structured metadata templates and tagging systems.

- **[ontology-define](skills/ontology-define/SKILL.md)**
  Design formal ontologies using OWL/RDFS. Defines classes, properties, and relationships for complex semantic modeling.

- **[sitemap-generate](skills/sitemap-generate/SKILL.md)**
  Generate hierarchical site structure and navigation maps. Creates visual representations of information architecture and content relationships.

- **[taxonomy-generate](skills/taxonomy-generate/SKILL.md)**
  Develop hierarchical classification systems. Creates parent-child categorical structures for content organization.

- **[thesaurus-generate](skills/thesaurus-generate/SKILL.md)**
  Generate controlled vocabulary thesaurus for content domains. Creates comprehensive thesauri with preferred terms, broader/narrower/related terms.

- **[user-flow-generate](skills/user-flow-generate/SKILL.md)**
  Visualize user paths and interactions. Creates flowcharts representing user journeys to complete specific tasks.

## Capabilities

This extension provides a suite of Information Architecture tools designed to help you analyze, organize, and structure content effectively.

- **Content Strategy**: Analyze content gaps, audit quality, inventory assets, and generate card sorting materials.
- **Structural Design**: Generate sitemaps, user flows, and design metadata schemas.
- **Classification & Semantics**: Develop taxonomies, thesauri, and formal ontologies.
- **Structured Data**: Generate semantic web markup and JSON-LD for documents.
- **Knowledge Base Management**: Ingest raw data, compile into wikis, perform complex Q&A, and run data integrity health checks.

## Commands

| Command | Description | Skill |
| :--- | :--- | :--- |
| `/ia:gaps` | Identify content gaps and organizational opportunities. | [content-analyze-gaps](skills/content-analyze-gaps/SKILL.md) |
| `/ia:audit` | Comprehensive content quality and maintenance assessment. | [content-audit](skills/content-audit/SKILL.md) |
| `/ia:inventory` | Systematic cataloging of information assets. | [content-inventory](skills/content-inventory/SKILL.md) |
| `/ia:card-sort` | Generate materials for card sorting studies. Creates detailed lists of content items (cards) for user research. | [card-sorting-generate](skills/card-sorting-generate/SKILL.md) |
| `/ia:doc-tree` | Transform lengthy documents into a semantic tree structure optimized for LLMs. | [document-tree-generate](skills/document-tree-generate/SKILL.md) |
| `/ia:metadata` | Design comprehensive metadata frameworks. | [metadata-schema-design](skills/metadata-schema-design/SKILL.md) |
| `/ia:ontology` | Design formal ontologies using OWL/RDFS. Defines classes, properties, and relationships. | [ontology-define](skills/ontology-define/SKILL.md) |
| `/ia:sitemap` | Generate hierarchical site structure and navigation maps. | [sitemap-generate](skills/sitemap-generate/SKILL.md) |
| `/ia:taxonomy` | Develop hierarchical classification systems. | [taxonomy-generate](skills/taxonomy-generate/SKILL.md) |
| `/ia:thesaurus` | Generate controlled vocabulary thesaurus for content domains. | [thesaurus-generate](skills/thesaurus-generate/SKILL.md) |
| `/ia:user-flow` | Visualize user paths and interactions. Creates flowcharts representing user journeys to complete specific tasks. | [user-flow-generate](skills/user-flow-generate/SKILL.md) |
| `/ia:semantic` | Generate semantic web markup (JSON-LD, Schema.org) for documents. | [semantic-markup-generate](skills/semantic-markup-generate/SKILL.md) |
| `/ia:json-ld` | Generate JSON-LD structured data for web content. Maps content to Schema.org types. | [json-ld-generate](skills/json-ld-generate/SKILL.md) |
| `/ia:kb-compile` | Incremental compiler that takes raw source documents and generates a structured Markdown knowledge base wiki. | [knowledge-base-compile](skills/knowledge-base-compile/SKILL.md) |
| `/ia:kb-qa` | Conduct complex research Q&A against the compiled knowledge base, generating rich visual outputs. | [knowledge-base-qa](skills/knowledge-base-qa/SKILL.md) |
| `/ia:kb-lint` | Perform health checks on the knowledge base to find inconsistencies, impute missing data, and suggest new article connections. | [knowledge-base-lint](skills/knowledge-base-lint/SKILL.md) |
