---
name: metadata-schema-design
description: Design comprehensive metadata frameworks and ontologies. Defines schemas, classes, properties, and relationships for CMS and Semantic Web.
required_roles:
  scribe: roles/scribe.editor
personas: [information-architect, data-architect, ontologist]
---

# Design Metadata Schema & Ontology Skill

Develop a comprehensive content model, metadata schema, or formal ontology. This skill defines structured fields, validation rules, and semantic relationships to ensure consistency, interoperability, and machine-readability.

## Inputs

- `PATH` - The content domain to apply the schema to (e.g., "/content" or description of domain)
- `OUTPUT_FORMAT` - (Optional) Format: "json-schema", "xml", "markdown", "turtle", "owl", "rdfxml" (default: "json-schema")
- `STANDARDS` - (Optional) List of standards to align with: "dublin-core", "schema.org", "skos", "owl" (default: ["dublin-core"])
- `STRICTNESS` - (Optional) For ontologies: "rdfs", "owl-lite", "owl-dl" (default: "rdfs")
- `BASE_URI` - (Optional) Base URI for semantic outputs (e.g., "http://example.org/ontology/")

## Workflow

### Step 1: Conceptual Modeling

Analyze the domain to identify key entities (Classes) and attributes (Properties/Fields).
- **Entities/Classes**: E.g., Article, Product, Person.
- **Attributes/Properties**: E.g., Title, Price, Author.

### Step 2: Definition & Constraints

Define the structure based on the `OUTPUT_FORMAT`:
- **For Schemas (JSON/XML)**: Define Data Types, Required/Optional, Validation Rules.
- **For Ontologies (Turtle/OWL)**: Define Object Properties (relationships), Datatype Properties, and logical Restrictions.

### Step 3: Standards Alignment

Map definitions to requested `STANDARDS`.
- E.g., Map "Title" to `dc:title` or `schema:headline`.
- E.g., Map "Broader Term" to `skos:broader`.

### Step 4: Output Generation

Generate the definition file in the requested `OUTPUT_FORMAT`.

## Required Outputs

A `SCHEMA_OR_ONTOLOGY` document.

**Example (Turtle/Ontology):**
```turtle
@prefix : <http://example.org/> .
:Product a owl:Class .
:hasPrice a owl:DatatypeProperty ; rdfs:domain :Product .
```

**Example (JSON Schema):**
```json
{ "type": "object", "properties": { "title": { "type": "string" } } }
```

## Quick Reference

- **Purpose**: Unify data modeling for CMS (Validation) and Knowledge Graphs (Reasoning).
- **Tools**: Protégé, JSON Schema Validator.
