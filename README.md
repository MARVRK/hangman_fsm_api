# Hangman FSM API

Word-guessing game built around a Finite State Machine engine,
exposed via FastAPI REST API with CLI interface.

## Architecture

- **FSM core** (`fsm.py`) — enforces valid state transitions: IDLE → PLAYING → WON / LOST
- **Repository pattern** (`repo.py` / `repoimpl.py`) — decoupled storage layer
- **REST API** (`web.py`) — FastAPI endpoints for game session management  
- **CLI** (`cli.py`) — terminal interface using the same core engine
- **Schemas** (`schemas.py`) — Pydantic request/response validation

## Tech Stack

- Python, FastAPI, Pydantic, Uvicorn
- pytest

## Run locally
```bash
uv sync
uv run uvicorn web:app --reload
```

```

## Key design decisions

- FSM pattern makes illegal state transitions impossible by design
- Repository abstraction decouples game logic from storage — DB can be swapped without touching the engine
- Same FSM core powers both REST API and CLI — no logic duplication