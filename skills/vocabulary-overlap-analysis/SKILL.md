---
name: vocabulary-overlap-analysis
description: Analyze vocabulary overlap and identify named entities unique to domain/document corpora.
required_roles:
  scribe: roles/scribe.viewer
personas: [information-architect, content-strategist, taxonomist, linguist]
---

# Vocabulary Overlap & Domain Entity Analysis Skill

Analyze a set of target documents to identify domain-specific vocabulary and named entities that are unique to your corpus. By contrasting your content's vocabulary against general-purpose reference corpora or a secondary document set, this skill helps surface proprietary terminology, key subject matter entities, and vocabulary overlaps.

## Inputs

- `TARGET_PATH` - The directory or file path of the target document corpus to analyze (e.g., "/documentation/product-guides").
- `REFERENCE_PATH` - (Optional) A path to a secondary document corpus to compare against. If not provided, the analysis will use general web, general English, and common domain knowledge baselines.
- `MIN_FREQUENCY` - (Optional) The minimum number of occurrences for a term or entity to be included in the analysis (default: 2).
- `EXCLUDE_COMMON` - (Optional) Boolean, whether to automatically filter out standard English stopwords and common business/industry jargon (default: true).

## Workflow

### Step 1: Corpus Profiling & Tokenization

Extract and profile all text from files in `TARGET_PATH`.
- Extract raw text from markdown, HTML, PDF, or text files.
- Clean and normalize the text (punctuation stripping, markup cleaning, etc.). **Do not perform blanket lowercase conversion** during tokenization and n-gram generation to preserve case casing cues essential for Named Entity Recognition (NER).
- Tokenize the text into individual words (unigrams) and common phrases (bigrams and trigrams) maintaining original casing.
- Identify potential Named Entities (proper nouns, technical abbreviations, capitalized concepts).

### Step 2: Contrastive Frequency Analysis

Contrast target frequencies against reference datasets to isolate characteristic terms.
- Calculate term frequencies (TF) and document frequencies (DF) in the target corpus.
- If `REFERENCE_PATH` is provided, perform the same frequency extraction for the reference corpus.
- If no reference path is provided, evaluate the term list against standard baseline general English corpora (e.g., Wikipedia or common web text datasets) and standard industry terminology.
- Calculate contrastive scores (e.g., TF-IDF or Log-Likelihood ratio) to highlight terms that are significantly more frequent in the target corpus than in the baseline.

### Step 3: Domain Entity Extraction & Classification

Isolate, consolidate, and categorize unique vocabulary and named entities.
- Filter terms to isolate those exclusive to `TARGET_PATH` (zero or very low overlap with the reference baseline).
- **Variant Consolidation & Concept Mapping**: Analyze casing, punctuation, and orthographic variants (e.g., "Scattered Spider", "scattered spider", "Scattered-Spider") and merge them into a single canonical concept. Define a capitalized or formal **Preferred Term**, and map all alternative representations as **Variant Terms**.
- Classify these consolidated unique terms into distinct semantic groups:
  - **Proprietary Entities**: Brand names, proprietary product names, internal tool names, code names.
  - **Domain Jargon & Technical Terms**: Specialized technical, operational, or industry-specific terms.
  - **Key Subject Matter Concepts**: Essential concepts defining the core subject matter of the documents.
  - **Acronyms & Abbreviations**: Short-hand terms and their expansions.

### Step 4: Overlap & Commonality Assessment

Assess the degree of similarity and overlap between the corpora.
- Calculate vocabulary overlap coefficients (e.g., Jaccard Similarity index or overlap coefficient) between `TARGET_PATH` and `REFERENCE_PATH` (if provided).
- Generate a mapped list of shared terminology representing common thematic ground.

## Required Outputs

A `VOCABULARY_OVERLAP_REPORT` in markdown format containing:
- **Executive Summary**: Key vocabulary metrics including total unique tokens, density of domain-specific terms, and overlap coefficients.
- **Unique Domain Entities**: A structured table of named entities unique to the target corpus, classified by category (e.g., Product, Brand, Concept, Acronym) showing the **Preferred Term**, consolidated **Variant Terms**, frequency counts, and contextual examples.
- **Domain Jargon & Technical Glossary**: A list of specialized terms and phrases unique to this corpus, complete with contextual definitions derived from the source material.
- **Vocabulary Overlap Matrix**: A detailed analysis of shared vs. exclusive vocabulary, highlighting areas of alignment and divergence.
- **Actionable Recommendations**: Strategic guidance on how to apply these findings to:
  - Custom taxonomy and metadata schema development.
  - Glossary and controlled vocabulary creation.
  - Search engine optimization (SEO) and query expansion strategies.
  - Automated content classification and tagging.

## Quick Reference

- **Purpose**: Uncover unique named entities and domain-specific terminology to establish controlled vocabularies and map content characteristics.
- **Outcome**: An actionable, structured domain vocabulary map and catalog of proprietary named entities.

## References

- Aghaei, E., Niu, X., Shadid, W., & Al-Shaer, E. (2022). SecureBERT: A Domain-Specific Language Model for Cybersecurity. *arXiv preprint arXiv:2204.02685*. [https://doi.org/10.48550/arxiv.2204.02685](https://doi.org/10.48550/arxiv.2204.02685)
- Aghaei, E., Jain, S., Arun, P., & Sambamoorthy, A. (2025). SecureBERT 2.0: Advanced Language Model for Cybersecurity Intelligence. *arXiv preprint arXiv:2510.00240*. [https://doi.org/10.48550/arxiv.2510.00240](https://doi.org/10.48550/arxiv.2510.00240)
- Ashfaq, F. (2025). Enhancing ECG Report Generation With Domain-Specific Tokenization for Improved Medical NLP Accuracy. *IEEE Xplore*.
- Beltagy, I., Lo, K., & Cohan, A. (2019). SciBERT: A Pretrained Language Model for Scientific Text. *arXiv preprint arXiv:1903.10676*. [https://doi.org/10.48550/arxiv.1903.10676](https://doi.org/10.48550/arxiv.1903.10676)
- Provilkov, I., Emelianenko, D., & Voita, E. (2020). BPE-Dropout: Simple and Effective Subword Regularization. *Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics*. [https://doi.org/10.18653/v1/2020.acl-main.170](https://doi.org/10.18653/v1/2020.acl-main.170)
- Radaideh, R., & Khreis, A. (2026). SMSI: System Model Security Inference: Automated Threat Modeling for Cyber-Physical Systems. *arXiv preprint arXiv:2604.23905*. [https://doi.org/10.48550/arxiv.2604.23905](https://doi.org/10.48550/arxiv.2604.23905)
- Ruiz-Ródenas, Á., Pujante Sáez, J., García-Algora, D., Rodríguez Béjar, M., Blasco, J., & Hernández-Ramos, J. L. (2025). SynthCTI: LLM-Driven Synthetic CTI Generation to enhance MITRE Technique Mapping. *arXiv preprint arXiv:2507.16852*. [https://doi.org/10.48550/arxiv.2507.16852](https://doi.org/10.48550/arxiv.2507.16852)
- Teklehaymanot, H. K., Fazlija, D., & Nejdl, W. (2025). MoVoC: Morphology-Aware Subword Construction for Geez Script Languages. *arXiv preprint arXiv:2509.08812*. [https://doi.org/10.48550/arxiv.2509.08812](https://doi.org/10.48550/arxiv.2509.08812)
- Teklehaymanot, H., Fazlija, D., & Nejdl, W. (2026). LGSE: Lexically Grounded Subword Embedding Initialization for Low-Resource Language Adaptation. *arXiv preprint arXiv:2603.22629*. [https://doi.org/10.48550/arxiv.2603.22629](https://doi.org/10.48550/arxiv.2603.22629)
