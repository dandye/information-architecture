---
name: named-entity-normalization
description: Normalize named entities and concept variants into canonical forms using controlled vocabularies or standard taxonomies.
required_roles:
  scribe: roles/scribe.viewer
personas: [information-architect, content-strategist, taxonomist, knowledge-engineer]
---

# Named Entity Normalization (NEN) & Entity Grounding Skill

Resolve lexical variations, typos, casing differences, and industry aliases of named entities within a document set into single canonical concepts. This skill maps unstructured entity mentions directly to unique database identifiers, standard taxonomies, or a custom controlled vocabulary (thesaurus), resolving vocabulary bloat and embedding fragmentation.

## Inputs

- `PATH` - The document directory or file path containing raw entities to normalize (e.g., "/threat-intel-reports").
- `TAXONOMY_PATH` - (Optional) Path to a target taxonomy, glossary, database, or controlled vocabulary (e.g., a MITRE ATT&CK group catalog or medical UMLS schema) to ground entities against. If not provided, the agent will construct a self-consistent canonical thesaurus directly from the document set's unique concepts.
- `CANONICAL_MAPPING` - (Optional) Boolean, whether to output a JSON mapping dictionary (thesaurus) alongside the markdown report (default: true).
- `HYBRID_STRATEGY` - (Optional) Boolean, whether to apply LLM-driven semantic inference (HNEN) for highly heterogeneous or inconsistent parameter names alongside lexical string matching (default: true).

## Workflow

### Step 1: Entity Extraction & Mentions Profiling

Locate all Named Entity mentions in the document set at `PATH`.
- Extract proper nouns, technical acronyms, brand names, and domain terms.
- Preserve casing and structural delimiters (e.g., hyphens, spaces) to retain context.
- Profile entity occurrences, document frequencies, and variation patterns.

### Step 2: Orthographic & Lexical Normalization

Apply base linguistic cleaning rules to standardize formatting variants.
- Clean punctuation, strip extra whitespaces, and standardize hyphens.
- Identify obvious case variants (e.g., "Scattered Spider", "SCATTERED SPIDER", "scattered spider") and orthographic variants (e.g., "ScatteredSpider").

### Step 3: Canonical Candidate Generation & Grounding

Match entity mentions to target canonical entries in `TAXONOMY_PATH` or general domain baselines.
- **Dictionary / Database Grounding**: Compare cleaned entity strings against the target taxonomy's names and alias fields.
- **Two-Step Retrieval (Semantic Re-ranking)**: For ambiguous entities, retrieve candidates based on string similarity and re-rank candidates by analyzing sentence context and concept definitions.
- **LLM-Driven Semantic Inference (HNEN)**: If `HYBRID_STRATEGY` is true and terms are highly heterogeneous (e.g., parameter naming conventions like `V_in`, `Vin`, `InputVoltage`), use semantic inference to map them to unified concepts based on datasheet conventions and domain schemas.

### Step 4: Synonym Grouping & Thesaurus Synthesis

Compile synonym sets and designate Preferred Terms.
- Resolve multiple different text names (e.g., "UNC3944", "Oktapus", "Scattered Spider") to a single **Preferred Term** representing the canonical concept.
- Create a comprehensive **Synonym & Alias Map** capturing all variations under their respective preferred canonical keys.

## Required Outputs

A `NAMED_ENTITY_NORMALIZATION_REPORT` in markdown format containing:
- **Executive Summary**: Metrics on total entity mentions, unique canonical concepts generated, compression ratio (raw mentions to canonical entities), and taxonomy coverage.
- **Canonical Concept Glossary**: A structured table containing:
  - **Preferred Term**: The formal, capitalized canonical name.
  - **Entity Type**: Category (e.g., Threat Group, Software, Concept, Parameter).
  - **Target Identifier**: Grounded ID (e.g., `MITRE_G1017` or custom ID) if matched against a taxonomy.
  - **Lexical Variants**: List of casing, spelling, and abbreviation variations consolidated.
  - **Vendor/Industry Aliases**: Industry synonyms resolved (e.g., "Oktapus", "UNC3944").
- **Actionable Preprocessor Implementation Plan**: A python snippet or configuration schema showing how to load the generated mapping as a pre-tokenization preprocessor layer to prevent embedding fragmentation.

If `CANONICAL_MAPPING` is true:
- **`nen-thesaurus.json`**: A structured JSON mapping file where keys are raw spelling variants (all lowercased for robust lookup) and values are the corresponding Preferred Terms.

## Quick Reference

- **Purpose**: Deduplicate and ground unstructured text entities to standard taxonomies or a controlled vocabulary, preventing parameter duplication and embedding fragmentation.
- **Outcome**: A canonical entity glossary and preprocessor-ready JSON thesaurus mapping file.

## References

- **BERN2**: Sung, M., Jeong, M., Choi, Y., Kim, D., Lee, J., & Kang, J. (2022). *BERN2: an advanced neural biomedical named entity recognition and normalization tool*. Bioinformatics. [https://doi.org/10.1093/bioinformatics/btac598](https://doi.org/10.1093/bioinformatics/btac598)
- **Species Normalization**: Awan, Z., Kahlke, T., Ralph, P., & Kennedy, P. (2023). *Bi-Encoders based Species Normalization -- Pairwise Sentence Learning to Rank*. arXiv:2310.14366. [https://doi.org/10.48550/arxiv.2310.14366](https://doi.org/10.48550/arxiv.2310.14366)
- **KG Canonicalization**: Dash, S., Rossiello, G., Mihindukulasooriya, N., Bagchi, S., & Gliozzo, A. (2020). *Open Knowledge Graphs Canonicalization using Variational Autoencoders*. arXiv:2012.04780. [https://doi.org/10.48550/arxiv.2012.04780](https://doi.org/10.48550/arxiv.2012.04780)
- **Heterogeneous NEN (HNEN)**: Chen, H. C., Xu, Y. P., & Zhang, Y. (2025). *D2S-FLOW: Automated Parameter Extraction from Datasheets... Using Large Language Models*. arXiv:2502.16540. [https://doi.org/10.48550/arxiv.2502.16540](https://doi.org/10.48550/arxiv.2502.16540)
