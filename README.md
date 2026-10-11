# AI Resume Analyzer

A Streamlit application that compares a candidate's resume with a job description and creates an AI-assisted recruitment brief. It reports an ATS-style score, job fit, skills gaps, project relevance, resume feedback, rewrite suggestions, interview preparation, a learning roadmap, career recommendations, and a hiring recommendation.

The app accepts resume text or PDF, DOCX, and TXT uploads. It uses either Anthropic Claude or an OpenRouter model to generate the analysis and provides downloadable Markdown and JSON reports.

## Features

- Resume input by pasted text or PDF, DOCX, and TXT upload
- Job description comparison and structured candidate analysis
- Skills matching, gaps, and project relevance
- Resume improvement suggestions, interview questions, and learning roadmap
- Interactive Streamlit report with charts
- Downloadable Markdown and JSON output
- Configurable Anthropic or OpenRouter model provider

## Requirements

- Python 3.9 or newer
- An API key for Anthropic or OpenRouter

## Setup

From the project directory, create and activate a virtual environment:

```bash
python -m venv .venv
```

Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

macOS/Linux:

```bash
source .venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Copy `.env.example` to `.env` and set the provider and API key. For example, with OpenRouter:

```env
LLM_PROVIDER=openrouter
OPENROUTER_API_KEY=your_openrouter_api_key
OPENROUTER_MODEL=deepseek/deepseek-chat-v3-0324
```

Or use Anthropic:

```env
LLM_PROVIDER=anthropic
ANTHROPIC_API_KEY=your_anthropic_api_key
CLAUDE_MODEL=claude-sonnet-4-6
```

Never commit real API keys. The `.env` file is ignored by Git; `.env.example` contains placeholders only.

## Run

```bash
streamlit run streamlit_app.py
```

Streamlit will print a local URL, typically `http://localhost:8501`.

## Usage

1. Choose an LLM provider and model in the sidebar and provide its API key through `.env` or the sidebar.
2. Paste a target job description.
3. Paste resume text or upload a PDF, DOCX, or TXT file.
4. Select **Run Full Analysis**.
5. Review the report sections and download Markdown or JSON as needed.

## Project layout

```text
streamlit_app.py             Streamlit interface and application flow
requirements.txt             Python dependencies
.env.example                 Environment variable template
.streamlit/config.toml       Streamlit theme and configuration
prompts/analysis_prompt.py   Structured analysis prompt
utils/llm_client.py          Anthropic and OpenRouter clients
utils/file_extractor.py      Resume file text extraction
utils/report_export.py       Markdown report generation
components/sections.py       Report section renderers
components/charts.py         Plotly chart builders
```

## Notes

This application provides AI-assisted analysis based on the supplied resume and job description. Its scores and recommendations are estimates, can contain errors, and should support human review rather than replace it in hiring decisions.
