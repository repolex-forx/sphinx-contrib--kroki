# Repolex Knowledge Graph of sphinx-contrib/kroki

RDF knowledge graph data for [sphinx-contrib/kroki](https://github.com/sphinx-contrib/kroki), parsed by [repolex](https://repolex.ai).

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
rlex download sphinx-contrib/kroki
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 2665ddf784498abc14917ac7a1ab391b1a2e9bc0
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 2665ddf784498abc14917ac7a1ab391b1a2e9bc0
│           └── chunk-001.nq.gz
├── blob
│   ├── 040e56c68a231f7b66dcc98229e754368849fc7f.nq.gz
│   ├── 136f2c2d59e6f65d6ab585255e71ae2c45e56e77.nq.gz
│   ├── 1a424d537100e74ced2daa6684f05a94e12a0918.nq.gz
│   ├── 2e506d254ac55938785074caece2742db18dcf6d.nq.gz
│   ├── 30b41d220d610f15ba2af06f0404c169375c1b39.nq.gz
│   ├── 3fdd0ae01ff396964be504e5cda01ffab082f0c4.nq.gz
│   ├── 416c05ea84564fa1c76edc6dd572d0c34dcfbd79.nq.gz
│   ├── 445ac66860f6072859e26daccdcfbc07d38ba94b.nq.gz
│   ├── 485744e3c5ccecb488f632aee6b506d2ad44acaa.nq.gz
│   ├── 4bf9856feef300275d2539882ac2cce1081a82d3.nq.gz
│   ├── 4c4f3c972f9554a10d4071d913fb70a06d111903.nq.gz
│   ├── 54c742d4afffca1406d62170453f6997366c4304.nq.gz
│   ├── 572ddc8fb2cc524768c17066fe08b152c02bae1f.nq.gz
│   ├── 7bab121604e70a8f98a1713711bbdf5ea39c9dc5.nq.gz
│   ├── 81d1a73f33fce4dbab10e5260388bffe9a8a97f3.nq.gz
│   ├── 943771ca51fa53c3e71dc30f454dea2d1d4ab40f.nq.gz
│   ├── 9bf6724d376e20b19367b12466b81d05fc496cba.nq.gz
│   ├── a2aa298ddce0a6061be5be65228fea0504b96814.nq.gz
│   ├── b7791f7525d9e79e8b0cbe4a162635f482a321b3.nq.gz
│   ├── cedd1031d6d0ed1e8896c249312b506e954699e7.nq.gz
│   └── ec009d6f384997efc1768140429dddb3cf60ac98.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 2665ddf784498abc14917ac7a1ab391b1a2e9bc0.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 29 files
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

[sphinx-contrib/kroki](https://github.com/sphinx-contrib/kroki)

---
*Parsed on 2026-11-06 by [repolex](https://repolex.ai)*
