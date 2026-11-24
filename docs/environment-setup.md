# Environment Setup

## Requirements

Python 3.11 or later, with:

```bash
pip install "chromadb>=1.0.4" "openai>=1.73.0" "pydantic>=2.11.3" "python-dotenv>=1.1.0" "tavily-python>=0.5.4" "pdfplumber>=0.11.6"
```

The `pysqlite3` cell at the top of each notebook is only needed on hosts with an old system SQLite. Elsewhere it does nothing, so it can stay.

## API keys

Create a [Tavily](https://app.tavily.com/home) account for web search (the free tier covers 1,000 requests) and copy your API key.

Create a file named exactly `.env` in the `starter/` folder (the folder that holds both notebooks):

```
OPENAI_API_KEY="<your-openai-key>"
OPENAI_BASE_URL="<your-openai-base-url>"
TAVILY_API_KEY="<your-tavily-key>"
```

At the top of each notebook, load `.env` and check that all three variables are set:

```python
import os
from dotenv import load_dotenv, find_dotenv

# find_dotenv() finds the .env file in this folder (or a parent folder);
# override=True makes the values in .env win over anything already set.
load_dotenv(find_dotenv(), override=True)

assert os.getenv("OPENAI_API_KEY"), "OPENAI_API_KEY is not set"
assert os.getenv("OPENAI_BASE_URL"), "OPENAI_BASE_URL is not set"
assert os.getenv("TAVILY_API_KEY"), "TAVILY_API_KEY is not set"
```

## Embedding function

ChromaDB's `OpenAIEmbeddingFunction` looks for its key in `CHROMA_OPENAI_API_KEY` by default. Point it at the existing key instead:

```python
embedding_fn = embedding_functions.OpenAIEmbeddingFunction(
    api_key_env_var="OPENAI_API_KEY",
    api_base=os.getenv("OPENAI_BASE_URL"),
)
```

Part 1 creates the collection with this function, and Part 2 rebuilds the same function when it loads the collection, so both need the same `.env`.

ChromaDB may log `Failed to send telemetry event … capture() takes 1 positional argument but 3 were given`. It's harmless.
