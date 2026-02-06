---
name: ontology-define
description: Design formal ontologies using OWL/RDFS. Defines classes, properties, and relationships for complex semantic modeling.
required_roles:
  scribe: roles/scribe.editor
personas: [ontologist, knowledge-engineer, information-architect]
---

# Define Ontology Skill

Create a formal ontology definition to model complex domains. This skill goes beyond simple taxonomies by defining classes, object properties, datatype properties, and logical restrictions using standards like OWL (Web Ontology Language) and RDFS (Resource Description Framework Schema).

## Inputs

- `DOMAIN_DESCRIPTION` - Description of the domain to model (e.g., "University System" or path to documentation).
- `FORMAT` - (Optional) Output format: "turtle", "rdfxml", "json-ld", "manchester" (default: "turtle").
- `BASE_URI` - (Optional) Base URI for the ontology (e.g., "http://example.org/ontology/").
- `STRICTNESS` - (Optional) Level of logical rigor: "rdfs", "owl-lite", "owl-dl" (default: "owl-lite").

## Workflow

### Step 1: Conceptual Modeling

Analyze the `DOMAIN_DESCRIPTION` to identify key entities and relationships.
- **Classes**: Sets of individuals (e.g., `Professor`, `Course`, `Student`).
- **Properties**: Relationships between individuals or values.

### Step 2: Property Definition

Define properties with domain and range constraints.
- **Object Properties**: Relate two instances (e.g., `teaches` relates `Professor` to `Course`).
- **Datatype Properties**: Relate instances to literals (e.g., `hasCredits` relates `Course` to `Integer`).
- **Characteristics**: Transitive, Symmetric, Inverse, Functional.

### Step 3: Hierarchy & Restrictions

Organize classes and properties into hierarchies (subClassOf, subPropertyOf).
- Apply restrictions if supported by `STRICTNESS` (e.g., "A Course must be taught by at least one Professor").

### Step 4: Serialization

Generate the ontology file in the requested `FORMAT`.
- Define prefixes (rdf, rdfs, owl, xsd).
- Declare the ontology header.
- Serialize all triples.

## Required Outputs

An `ONTOLOGY_FILE` content in the specified `FORMAT`.

**Example (Turtle):**
```turtle
@prefix : <http://example.org/uni/> .
@prefix owl: <http://www.w3.org/2002/07/owl#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .

:UniversityOntology a owl:Ontology .

:Person a owl:Class .

:Student a owl:Class ;
    rdfs:subClassOf :Person .

:enrolledIn a owl:ObjectProperty ;
    rdfs:domain :Student ;
    rdfs:range :Course .
```

## Quick Reference

- **Purpose**: Enable reasoning and interoperability in Knowledge Graphs.
- **Standards**: W3C OWL 2, RDFS.
- **Tools**: Protégé, RDFLib.
