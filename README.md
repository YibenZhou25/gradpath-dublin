# GradPath Dublin

A career-readiness AI agent for international Master's-level CS students
preparing for graduate software engineering roles in Dublin, Ireland.

This repository accompanies the COMP47980 final project.

## How to run

1. Open `gradpath_main_agent.ipynb` in Google Colab.
2. Configure the following Colab secrets:
   - `OPENAI_API_KEY` — your OpenAI API key
   - `GITHUB_TOKEN` — a GitHub personal access token (optional, for higher rate limit)
3. Run all cells in order.

The notebook will automatically clone this repository's knowledge base
on first run and build the OpenAI vector store.