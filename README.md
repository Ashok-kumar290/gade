# GADE - Gradient-Aware Development Environment

[![Python 3.11+](https://img.shields.io/badge/python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![PyPI](https://img.shields.io/pypi/v/gade.svg)](https://pypi.org/project/gade/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

**Allocate AI compute dynamically based on code difficulty.**

GADE measures difficulty across your codebase and focuses 80% of tokens on the 20% hardest regions.

## Quick Start

```bash
pip install gade

# Analyze a repository
gade analyze ./my-project --top 20

# View heatmap
gade heatmap ./my-project
```

## Cloud API

Use the hosted API — no setup required:

```bash
curl -X POST "https://web-production-8b5ca.up.railway.app/analyze" \
  -H "Content-Type: application/json" \
  -d '{"repo_path": "./my-project", "top_k": 10}'
```

📖 **API Docs:** [web-production-8b5ca.up.railway.app/docs](https://web-production-8b5ca.up.railway.app/docs)

## Features

- **5 Difficulty Signals**: Edit churn, complexity, errors, uncertainty, gradient
- **80/20 Allocation**: Smart token distribution by difficulty
- **Multi-LLM Support**: OpenAI, Anthropic, Google, Ollama, Azure, Bedrock
- **Agentic AI Ready**: MCP server, OpenAI tools, LangChain integration
- **REST API**: Hosted cloud API or self-host with `gade serve`

## Installation

```bash
pip install gade
```

## Python SDK

```python
from gade import analyze

result = analyze("./my-project")
for node in result.get_top_k(10):
    print(f"{node.node_name}: {node.difficulty_score:.2f}")
```

## CLI Commands

| Command | Description |
|---------|-------------|
| `gade analyze <path>` | Rank code by difficulty |
| `gade heatmap <path>` | Terminal visualization |
| `gade refactor <path>` | AI-assisted refactoring |

## Difficulty Tiers

| Score | Tier | AI Strategy |
|-------|------|-------------|
| < 0.2 | compress | Summarize |
| 0.2-0.5 | standard | Single-pass |
| 0.5-0.8 | deep | Multi-step + tools |
| ≥ 0.8 | debate | Multi-pass synthesis |

## License

MIT
