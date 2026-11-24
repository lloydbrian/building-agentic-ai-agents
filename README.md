# Building Agentic AI Agents: UdaPlay

UdaPlay is an AI research agent that answers questions about video games. It searches a local ChromaDB database of 15 games first, checks whether the results answer the question, and falls back to a Tavily web search when they don't. Built for Udacity's *Building Agents* course.

- `starter/`: the project code and notebooks. See [starter/README.md](starter/README.md) for setup.
- `docs/`: the course overview, instructions, rubric and environment setup.

## Quick start

```bash
cd starter
pip install -r requirements.txt notebook
cp .env.example .env   # then fill in your keys
```

Run `Udaplay_01_starter_project.ipynb` (builds the vector database), then `Udaplay_02_starter_project.ipynb` (runs the agent), both from `starter/`.
