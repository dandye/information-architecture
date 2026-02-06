---
name: ontology-map
description: Map local tags, categories, or terms to standard formal ontologies (like SKOS or industry-specific standards) to ensure interoperability.
required_roles:
  scribe: roles/scribe.editor
personas: [taxonomist, information-architect]
---

# Ontology Mapper Skill

Analyze a list of local terms (tags, categories) and suggest mappings to standard ontologies to improve content classification and interoperability.

## Inputs

- `SOURCE_TERMS` - A list of terms or a path to a file containing terms to map.
- `TARGET_ONTOLOGY` - (Optional) The standard ontology to map to (e.g., "SKOS", "Dublin Core", "Schema.org"). Default: "SKOS".

## Workflow

1.  **Analyze**: Review the `SOURCE_TERMS` to understand their local context and usage.
2.  **Search**: Look up potential matches in the `TARGET_ONTOLOGY` spec.
3.  **Map**: suggest:
    - **Exact Match** (`skos:exactMatch`)
    - **Broader Match** (`skos:broader`)
    - **Narrower Match** (`skos:narrower`)
    - **Related Match** (`skos:related`)

## Output

A mapping table (Markdown or CSV) linking Input Term -> Target URI/Term -> Relation Type.
