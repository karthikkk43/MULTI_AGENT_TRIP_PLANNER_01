
# VoyageAI — Multi-Agent AI Travel Planner

VoyageAI is a stateful multi-agent AI application that simplifies travel planning by coordinating specialized agents to generate personalized itineraries.

## Key Features

- **Multi-Agent Orchestration:** LangGraph supervisor dynamically routes tasks across five specialized agents.
- **MCP Integration:** Tavily, AviationStack, and OpenWeatherMap provide external travel information.
- **AI Guardrails:** Validates travel-related requests before execution.
- **Human-in-the-Loop:** Users can approve or request changes to generated itineraries.
- **Persistent State:** PostgreSQL checkpointing maintains workflow state.
- **Observability:** LangSmith traces agent execution and LLM calls.
- **FastAPI Backend:** REST APIs with an interactive web interface and PDF export.

## Architecture

User → FastAPI → Input Guardrail → LangGraph Supervisor  
→ Flight / Hotel / Weather / Budget / Itinerary Agents  
→ Human Approval → Final Travel Plan

**Supporting Services:** MCP Tools | Groq LLM | PostgreSQL | LangSmith

## Tech Stack

Python | LangGraph | LangChain | MCP | Groq | FastAPI | PostgreSQL | LangSmith

## Getting Started

```bash
git clone https://github.com/karthikkk43/MULTI_AGENT_TRIP_PLANNER_01.git
cd MULTI_AGENT_TRIP_PLANNER_01

python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

Create a `.env` file:

```env
GROQ_API_KEY=your_key
TAVILY_API_KEY=your_key
AVIATION_STACK_API_KEY=your_key
OPENWEATHER_API_KEY=your_key
DATABASE_URL=your_postgresql_url

LANGSMITH_TRACING=true
LANGSMITH_API_KEY=your_key
LANGSMITH_PROJECT=VoyageAI
```

Install `uv` to enable the AviationStack MCP server (`uvx`).

## Run Locally

```bash
uvicorn app:app --reload
```

Open http://127.0.0.1:8000

## Limitations

Flight fares and budget estimates are approximate and should be verified with booking providers. The application does not book flights or hotels.

## Author

**Pavan Karthik Potanagari**

GitHub: https://github.com/karthikkk43
