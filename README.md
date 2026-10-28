# Repolex Knowledge Graph of explosion/prodigy-hf

RDF knowledge graph data for [explosion/prodigy-hf](https://github.com/explosion/prodigy-hf), parsed by [repolex](https://repolex.ai).

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
rlex download explosion/prodigy-hf
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── cef6257d29f43282942ade8998592e59379bc317
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── cef6257d29f43282942ade8998592e59379bc317
│           └── chunk-001.nq.gz
├── blob
│   ├── 0755dcfffac088e52f0b904a125f74e3fb544c54.nq.gz
│   ├── 091738158cb950991f5f4b5415cfd08a314d5b35.nq.gz
│   ├── 1b113aa596a7e2e3e0945a475fa01e4295a1b116.nq.gz
│   ├── 2bbc3c4ae158af3c3d0ca37430f27fae64fe0fb5.nq.gz
│   ├── 2ddd1f4d00273ed1c8b8ff3b17d9d45adcafbecf.nq.gz
│   ├── 2f141c115ddc6ac05b35e183d45ba5039d3d283f.nq.gz
│   ├── 368a804662f619ea5afa419547ab66d7b04d8fb7.nq.gz
│   ├── 6769e21d99a63338394e47bc4c7d0aba1e88d5a5.nq.gz
│   ├── 6dbd43fbd7f530f3f0c554c63605be7e3d220485.nq.gz
│   ├── 7956f3618a8ae1e6cad74371bb341972fa262760.nq.gz
│   ├── 7f52ec31c746198cf6e55b9bdaa664d651d706e2.nq.gz
│   ├── 8530b8c9960d78211969f0e1b4a975d191bc8ae9.nq.gz
│   ├── 8b986f928f19eed42712e1901d2a9a55ad3dcf29.nq.gz
│   ├── 9582143d62d96eaf1c880121e5d5418adc98721b.nq.gz
│   ├── b36adbefccf7f3203bad36fc4e0c6ca2997fb50f.nq.gz
│   ├── d627907dd1dfef769c106d7fd370c7fe53cd8c63.nq.gz
│   └── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── cef6257d29f43282942ade8998592e59379bc317.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 24 files
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

[explosion/prodigy-hf](https://github.com/explosion/prodigy-hf)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
