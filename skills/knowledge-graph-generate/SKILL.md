---
name: knowledge-graph-generate
description: Analyze multiple documents to extract entities and relationships, generating a knowledge graph structure (RDF/Turtle).
required_roles:
  scribe: roles/scribe.editor
personas: [information-architect, data-scientist, knowledge-manager]
---

# Knowledge Graph Generator Skill

Analyze a set of documents to identify named entities and their inter-relationships, constructing a knowledge graph to visualize and query the information structure.

## Inputs

- `SOURCE_PATH` - Directory or file list to analyze.
- `OUTPUT_FORMAT` - (Optional) "turtle", "rdf/xml", "json-ld" (default: "turtle").
- `DEPTH` - (Optional) Recursion depth for directory traversal (default: 1).

## Workflow

1.  **Ingest**: Read documents from `SOURCE_PATH`.
2.  **Extract**: Perform Named Entity Recognition (NER) to find People, Organizations, Locations, Concepts.
3.  **Relate**: Identify relationship verbs connecting entities (e.g., "authored by", "located in").
4.  **Serialize**: Generate the graph in the requested `OUTPUT_FORMAT` (e.g., Turtle syntax).

## Output

A serialized graph file or block representing the extracted knowledge.
