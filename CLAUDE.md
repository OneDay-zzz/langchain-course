# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the project

```bash
python main.py
```

Requires Ollama running locally:

```bash
ollama serve          # start the Ollama daemon
ollama pull llama3.2  # pull the model used in main.py
```

## Dependencies

Installed via pip. Key packages:

- `langchain`, `langchain-core` — base LangChain primitives
- `langchain-ollama` — `ChatOllama` integration for local models
- `langchain-anthropic` — `ChatAnthropic` integration
- `python-dotenv` — loads `.env` for API keys (e.g. `ANTHROPIC_API_KEY`)

## Architecture

This is a course/sandbox project. `main.py` is the single entry point — each lesson or experiment lives there. The pattern is:

1. Instantiate a chat model (`ChatOllama`, `ChatAnthropic`, etc.)
2. Build a list of `SystemMessage` / `HumanMessage` objects from `langchain_core.messages`
3. Call `model.invoke(messages)` and read `.content` from the returned `AIMessage`

Environment variables are loaded from `.env` at startup via `python-dotenv`.