# Repolex Knowledge Graph of bentoml/BentoCrewAI

RDF knowledge graph data for [bentoml/BentoCrewAI](https://github.com/bentoml/BentoCrewAI), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download bentoml/BentoCrewAI
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 9ceb8976d7813d0a50c0ff420f9d5b447e553778
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 9ceb8976d7813d0a50c0ff420f9d5b447e553778
│           └── chunk-001.nq.gz
├── blob
│   ├── 25538cf0a042cf189542ccc49fc74cf08607df04.nq.gz
│   ├── 295c456e2d78a9a553977e96e8cc545042aee76b.nq.gz
│   ├── 37142575db42320444c56b7fcddeab35d5fbb28f.nq.gz
│   ├── 5167484275431e0a2a7d4a17e5b791a6201916a4.nq.gz
│   ├── 5fabf2bc18da6f4506ebb6daf7a846709a285a4a.nq.gz
│   ├── 6830b1443c47e638ea9fffdc850a6f95f32e913e.nq.gz
│   ├── 7a1f2b1be4dc55d0b78e4d3c6d0fbcf7612b652a.nq.gz
│   ├── 83de202e5451ddba462195589b03d83d44a3b35c.nq.gz
│   ├── b125293033e0cf7368102b33b89794ef2268bf77.nq.gz
│   ├── d418ae5a784b1625f69a5dbb28d98d8875bb7279.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e916f39bb62057f9ce28bb7746328d52c7e413fd.nq.gz
│   └── f30820855e8349d1e89e2c96e48015086d624df9.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 9ceb8976d7813d0a50c0ff420f9d5b447e553778.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 20 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[bentoml/BentoCrewAI](https://github.com/bentoml/BentoCrewAI)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
