# Repolex Knowledge Graph of pydantic/logfire-vscode

RDF knowledge graph data for [pydantic/logfire-vscode](https://github.com/pydantic/logfire-vscode), parsed by [repolex](https://repolex.ai).

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
rlex download pydantic/logfire-vscode
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── fe7c609d07a8002c0f8b5a16723c7ef80591a6ea
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── fe7c609d07a8002c0f8b5a16723c7ef80591a6ea
│           └── chunk-001.nq.gz
├── blob
│   ├── 013c9d836fc567b5410d75f765f6559c5c359cbc.nq.gz
│   ├── 0cb7a5fe7668750f661e5e3fc8d42d624006e141.nq.gz
│   ├── 10a414a3b50b7bb21d10d471d5de10b551aef126.nq.gz
│   ├── 1cbdd6f3434e544f2694ce385e57faca51bfabc8.nq.gz
│   ├── 1d57e728c35f1af59e144a03a9fb0d36b30552db.nq.gz
│   ├── 22f43492efadc5530a6cfac1b6c68407fed448b1.nq.gz
│   ├── 295182ab7ad11afef10bb5d518ac836c0917b9be.nq.gz
│   ├── 2ae8b6ceb7c78624fb0b2521a58b8ccb6cc95a05.nq.gz
│   ├── 42695d20e81571d8c0e3b8abae7382db682c902e.nq.gz
│   ├── 44045a23affa75b37a5005dc57ffed5bc06cd0cc.nq.gz
│   ├── 49cddf58e51a10066da98b71625604805836327a.nq.gz
│   ├── 4bc709b9470343178c4c078d1e8eee6327c64776.nq.gz
│   ├── 4dce9f3781a5614512d127765d4c1d46107eb659.nq.gz
│   ├── 5b7f7a925cc054db9e518cec6849ff369e1b35b6.nq.gz
│   ├── 61663941a3d848c97e888eda774259277425ae6a.nq.gz
│   ├── 61972aabb52a839cded5d3877d754fc09bce30ec.nq.gz
│   ├── 74a8ddcf704b30c5b9e29f7161250786512564c5.nq.gz
│   ├── 7bf1c3dc5959e053bcc07d7afb9be44bb35b1165.nq.gz
│   ├── 80069c684b9a6031de0bccef0bab72a452f744e6.nq.gz
│   ├── 87c81e8b46e9b7873fa10ac0141ac754e7f39047.nq.gz
│   ├── 8a39a77f2727310666783508959dbea5f11e6027.nq.gz
│   ├── 9238bfd8f14ee27843c7508f2f0455ec93f7cc27.nq.gz
│   ├── 93a84c5ed8acb512863520f6abba081e4d016a43.nq.gz
│   ├── 9b2b077cc653f309a2d1e57b54b9773d920bcdf3.nq.gz
│   ├── 9b7571dd5cec891ced16029cc178771fbc5ee17e.nq.gz
│   ├── a4ae942a45bf4787650d051561833cdf1f3d8a80.nq.gz
│   ├── a607ea92e0526ca61b0226ace17568db3e33463b.nq.gz
│   ├── a83049944675a2a0d1db35782bd0736bfa228df6.nq.gz
│   ├── b12799a3660db21818fb39a9d8af0d13518c4dff.nq.gz
│   ├── b29ca609cd744198dc1afc84c81e3bb590a888a5.nq.gz
│   ├── c48c519dc2f9e3ce315c9a51c537bee4329251ce.nq.gz
│   ├── c9427626198a51062356c200622a91f05b65b91b.nq.gz
│   ├── d2ee4216d186dc114ee3d5b7a47d368a87e80988.nq.gz
│   ├── e000b9a6e555498f1496118130ac69df152d1418.nq.gz
│   ├── e2cdca36558357dcc93311ab479c2cb2659a378e.nq.gz
│   ├── e38dd04ff9e3fd9b36925126d300ab9da692d6c6.nq.gz
│   └── f9b22b793c2998a2d5b65850b80b8a459bab32f4.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── fe7c609d07a8002c0f8b5a16723c7ef80591a6ea.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 44 files
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

[pydantic/logfire-vscode](https://github.com/pydantic/logfire-vscode)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
