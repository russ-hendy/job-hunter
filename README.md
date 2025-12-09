# Job Hunter Agent 🕵️‍♂️💼

A **Local "Sidecar" Agent** that helps you organize your job search, tailor applications, and (cautiously) automate interactions.

## Architecture

- **Orchestrator**: Python (FastAPI) + LangGraph
- **Frontend**: Vue 3 + Tailwind (Dashboard)
- **Browser Automation**: Playwright (Local Headed Mode)
- **Data**: Local JSON + Vector Store (ChromaDB)

## Getting Started

### Prerequisites

- Python 3.10+
- Node.js 20+
- Docker (optional, for running specialized services later)

### Setup

1. **Backend**:
   ```bash
   cd backend
   python -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   python -m app.main
   ```

2. **Frontend**:
   ```bash
   cd frontend
   npm install
   npm run dev
   ```

## Workflow

1. **Link Collection**: Parses your job alert emails (does NOT scrape LinkedIn search).
2. **Analysis**: Evaluates JDs against your `bio.json` profile.
3. **Drafting**: Generates cover letters and answers.
4. **Human Review**: You approve everything via the Dashboard.
5. **Application**: The `Navigator` agent automates the form filling (with your supervision).

## Warnings

- **DO NOT** run this in "Headless" mode against LinkedIn.
- **DO NOT** share your `data/bio.json` or `.env` files.
