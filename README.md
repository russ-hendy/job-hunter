# Job Hunter Agent

Can I automate a job search while learning about multi-agent orchestration using LangGraph? This project - done in tandem with Google's Antigravity - is an attempt to find out!

A **Local Agent** that helps organise a job search, tailors applications, and (cautiously) automates interactions.

The plan is to build a few separate agents that do different things:

- **Link Collector**: Parses job alert emails (does NOT scrape LinkedIn search).
- **Job Analyser**: Evaluates job descriptions against a stored profile.
- **Cover Letter Generator**: Generates cover letters and answers.
- **Application Navigator**: Automates the form filling (with meat-sack supervision, at least for now).


## Architecture

- **Orchestrator**: Python (FastAPI) + LangGraph
- **Frontend**: Vue 3 + Tailwind (Dashboard)
- **Browser Automation**: Playwright (Local Headed Mode)
- **Data**: Local JSON + Vector Store (ChromaDB)

## Data Privacy & Setup

This project uses a **Template Pattern** to keep personal data safe.

1.  **Copy the template**:
    ```bash
    cp data/bio.example.json data/bio.json
    ```
2.  **Edit `data/bio.json`**: Fill in your real details (Phone, Address, paths to different CVs).
3.  **Git Safety**: `data/bio.json` is ignored by git. **Do not** remove it from `.gitignore`.

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
