# AGENTS Instructions

This repository is a monorepo. Each library lives in a subdirectory under `libs/`.

When you modify code in any library, run the following commands in that library's directory before creating a pull request:

- `make format` – run code formatters
- `make lint` – run the linter
- `make test` – execute the test suite

To run a particular test file or to pass additional pytest options you can specify the `TEST` variable:

```
TEST=path/to/test.py make test
```

Other pytest arguments can also be supplied inside the `TEST` variable.

## Libraries

The repository contains several Python libraries. The JS/TS SDK now lives in
[langchain-ai/langgraphjs](https://github.com/langchain-ai/langgraphjs); `libs/sdk-js` only holds a pointer README.
Below is a high-level overview:

- **checkpoint** – base interfaces for LangGraph checkpointers.
- **checkpoint-postgres** – Postgres implementation of the checkpoint saver.
- **checkpoint-sqlite** – SQLite implementation of the checkpoint saver.
- **checkpoint-conformance** – conformance test suite for checkpointer implementations.
- **cli** – official command-line interface for LangGraph.
- **langgraph** – core framework for building stateful, multi-actor agents.
- **prebuilt** – high-level APIs for creating and running agents and tools.
- **sdk-py** – Python SDK for the LangGraph Server API.

### Dependency map

The diagram below lists downstream libraries for each production dependency as
declared in that library's `pyproject.toml`.

```text
checkpoint
├── checkpoint-postgres
├── checkpoint-conformance
├── checkpoint-sqlite
├── prebuilt
└── langgraph

prebuilt
└── langgraph

sdk-py
├── langgraph
└── cli
```

Changes to a library may impact all of its dependents shown above.

- Do NOT use Sphinx-style double backtick formatting (` ``code`` `). Use single backticks (`` `code` ``) for inline code references in docstrings and comments.
