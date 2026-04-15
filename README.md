# Repolex Knowledge Graph of jquast/blessed

RDF knowledge graph data for [jquast/blessed](https://github.com/jquast/blessed), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [lexq](https://github.com/repolex-ai/lexq) query tool using [uv](https://docs.astral.sh/uv/getting-started/installation/).

If you have uv installed, just copy/paste this into your terminal:

```bash
uv tool install git+https://github.com/repolex-ai/lexq
```

This installs lexq onto your system, in your user context. Verify the install:

```bash
lexq --help
```

**lexq is designed to be used primarily by LLMs in a terminal.** Start up your favorite LLM and ask it to use the lexq tool. It's that easy!

To load this repo's data:

```bash
lexq download jquast/blessed
```

This will automatically download essential data files from the last parsed commit. Consult `lexq --moreinfo` for other options, including downloading multiple commits, blobs, etc.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── f44b071db8480c787f3dffd80c4e0595850a9134
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── f44b071db8480c787f3dffd80c4e0595850a9134.nq.gz
│   └── repolex
│       └── f44b071db8480c787f3dffd80c4e0595850a9134
│           └── chunk-001.nq.gz
├── blob
│   ├── 41401622153b9bd168f86a6d293389104dda3bb6.nq.gz
│   ├── 481d411e55029e02b589ffd5917d07df7647d399.nq.gz
│   ├── 9561fb1061f6de114633c70871232a6896dcbe8a.nq.gz
│   ├── 9ca6184eba9747b23436762899b93dd782299c83.nq.gz
│   └── d65016ced670ec0755587c66052106aa9d93e941.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── f44b071db8480c787f3dffd80c4e0595850a9134.nq.gz
├── filetree
│   └── f44b071db8480c787f3dffd80c4e0595850a9134.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 15 files
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

## Source repository

[jquast/blessed](https://github.com/jquast/blessed)

---
*Parsed on 2026-04-15 by [repolex](https://repolex.ai)*
