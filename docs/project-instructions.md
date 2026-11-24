# Project Instructions

## Part 1: RAG pipeline

- Set up a ChromaDB vector database
- Process and embed game data from the JSON files
- Implement semantic search
- Create a reusable vector store manager

## Part 2: Agent

Build an agent with three core tools:

- `retrieve_game`: search the vector database
- `evaluate_retrieval`: assess whether the results answer the question
- `game_web_search`: fall back to web search

Implement a state machine for the agent workflow and a reporting format for clear output.

## Connecting Part 1 and Part 2

Part 2 reuses the database built in Part 1, so the two notebooks must agree:

- Run both notebooks from the `starter/` folder.
- In Part 1, create the database with `chromadb.PersistentClient(path="chromadb")` and a collection named `udaplay`. Part 2 loads exactly that path and name.
- Use the embedding function from [Environment Setup](environment-setup.md) when creating the collection.
- Don't delete the `chromadb/` folder that Part 1 creates. If you do, re-run Part 1 before Part 2.

If Part 2 finds no results, or says the collection `udaplay` does not exist, one of these doesn't match.

## Before sharing

- Keep API keys private: never commit or share `.env`. `.env.example` lists the variable names.
- Keep the `lib/` folder; both notebooks import from it.
- Save both notebooks with their outputs, after running every cell.

## Expected output

- Run at least three example queries: at least one the local dataset can answer, and at least one it can't, so the web fallback runs. The three queries in the Part 2 notebook do this: two are in the dataset, and Mortal Kombat X is not.
- For each query, show the steps the agent took: retrieve from the vector database → evaluate the results → search the web only when they aren't good enough → final answer.
- When an answer comes from the web, cite the source URL.
- Answers vary between runs, because LLM output and web results change. What matters is that the retrieve → evaluate → fall back process is shown.
