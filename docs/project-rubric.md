# Project Requirements

## RAG

**Prepare and process the local game dataset for a vector database and RAG pipeline.**

- `Udaplay_01_starter_project.ipynb` loads, processes and formats the game JSON files.
- The processed data is added to a persistent vector database (ChromaDB) with embeddings.
- The notebook shows the database can be queried with semantic search.

## Agent

**Implement tools for internal retrieval, evaluation and web search fallback.**

- At least three tools:
  - one that retrieves game information from the vector database
  - one that evaluates the quality of the retrieved results
  - one that searches the web through an API (Tavily)
- Each tool is a function or class integrated into the agent workflow.
- The agent first tries internal knowledge, evaluates the result, and falls back to web search if needed.

**Build a stateful agent that manages conversation and tool usage.**

- The agent is a class or function that keeps conversation state.
- It handles multiple queries in a session and remembers earlier context.
- Its workflow is a state machine or similar abstraction.
- It produces clear, structured, cited answers.

**Demonstrate the agent with example queries.**

- `Udaplay_02_starter_project.ipynb` runs the agent on at least three example queries (release dates, platforms, publishers and so on).
- The output for each query shows the agent's reasoning, tool usage and final answer, with a citation where there is one.
