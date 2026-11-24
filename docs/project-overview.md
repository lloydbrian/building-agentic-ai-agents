# Project Overview

## Scenario

UdaPlay is an assistant for a gaming analytics company. Executives, analysts and gamers ask natural language questions such as:

- "Who published Grand Theft Auto: San Andreas?"
- "When was Pokémon Gold and Silver released?"
- "What platform was Super Mario 64 launched on?"
- "What is Rockstar Games working on right now?"

The first three can be answered from the local dataset of 15 games. The last one can't, so the agent has to search the web.

The agent should:

- Try to answer from internal knowledge (the local dataset)
- Search the web if the information isn't found or confidence is low
- Produce a clean, structured answer that cites its source
- Remember earlier questions within a session (conversation state)

Persistent long-term memory across sessions is an optional extension.

## Specifications

The agent answers questions about:

- Game titles and their details
- Release dates and platforms
- Descriptions and genres
- Publishers

It uses a two-tier retrieval system:

- **Primary:** RAG over the local game dataset
- **Secondary:** web search with the Tavily API when internal knowledge is insufficient

It evaluates what it retrieves:

- Assesses the quality of the retrieved information
- Decides when to fall back to web search
- Gives a confidence level with each answer

Its responses:

- Cite their sources
- Combine information from multiple sources when needed
- Read naturally
