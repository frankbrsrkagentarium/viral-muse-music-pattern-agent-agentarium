---
dataset_name: viral-muse-vectorized-kg
pretty_name: Viral Muse Vectorized Knowledge Graph
version: v1.0.0
created_at_utc: 2025-12-13
license: CC-BY-4.0
tags:
  - knowledge-graph
  - master-grid
  - synthetic-data
  - retrieval
  - agentic
  - content-patterns
task_categories:
  - text-retrieval
  - text-generation
languages:
  - en
---

# Viral Muse Vectorized Knowledge Graph (KG)

This dataset is a **synthetic, structured Master Grid** built for retrieval + linking workflows.
It contains:

- **Atoms** (nodes): normalized semantic units derived from source rows
- **Edges** (relations): deterministic internal links, platform-alignment links, and rule-based semantic links
- **Knowledge Map**: dataset registry (schemas, atomization strategy, enabled rules)

## Files

- `viral_muse_atoms_master_v1.csv`
- `viral_muse_edges_master_v1.csv`
- `viral_muse_knowledge_map_v1.csv`
- `viral_muse_kg_manifest_v1.json`

## What’s inside

### Atom counts

{
  "creative_partner_advice_map": 406,
  "genre_transformation_rules": 169,
  "lyric_structure_map": 300,
  "tiktok_concept_patterns": 299,
  "viral_pattern_signals": 308,
  "viral_potential_rated": 616
}

Total atoms: **2098**

### Edge counts by relation type

{
  "guided_by": 203,
  "has_bundle": 308,
  "platform_aligned": 7440,
  "platform_multi_aligned": 260,
  "semantic_related": 857
}

Total edges: **9068**

## Schema

### atoms_master columns

atom_id, source_dataset_id, source_row_id, atom_category, primary_label, secondary_labels, attributes, tags, provenance, confidence, status, notes

### edges_master columns

edge_id, from_atom_id, to_atom_id, relation_type, relation_subtype, weight, confidence, source_rule_ids, notes

## Intended use

Use this KG to:

- retrieve “best matching” patterns (atoms) for a given request
- follow relationships to adjacent patterns (edges) for expansion
- power ranking, recommendation, and structured reasoning inside agent pipelines

## Recommended ingestion pattern

1) **Vector DB**: upsert **atoms** as documents
- Vector ID recommendation: `viral_muse:<source_dataset_id>:<atom_id>`
- Attach metadata: `source_dataset_id`, `source_row_id`, `atom_category`, `confidence`, `status`, `version`

2) **Graph layer**: ingest **edges** into a graph store (or adjacency index)
- Use `edge_id` as primary key
- Validate that `from_atom_id` and `to_atom_id` exist in atoms

## Data origin & safety

- **Synthetic**: not collected from real users
- **No personal data**
- **Non-operational**: patterns are for creative/retrieval workflows

## Limitations

- CPA semantic connectivity is intentionally conservative (low shared vocabulary)
- Genre transformation rules (GTR) are present as atoms but have minimal linking in v1 (to be expanded with transformation-specific rules)

## Citation / attribution

If you use this dataset publicly, attribute:
**Agentarium / Viral Muse (synthetic)** (CC-BY-4.0)

