# AI Risk Repository MCP Server

Disclaimer: I am in no part affiliated with the MIT AI Risk Repository, and all credit for creating, maintaining, and updating the database goes to the team outlined at [airisk.mit.edu](https://airisk.mit.edu/).

This project is a Python-based MCP (Model Context Protocol) server that exposes the MIT AI Risk Repository to LLM agents. The server allows agents to retrieve AI risk entries by keyword, domain, or causal factors via a standardized interface.

---

## Overview

The server parses and serves a structured dataset of AI risks sourced from academic and regulatory documents, annotated with domain and causal taxonomy labels. LLM agents can query the data through defined tools to assist with tasks such as AI safety analysis, risk explanation, or scenario exploration.

---

## Features

* Retrieve AI risks by keyword in the description.
* Retrieve AI risks by domain or subdomain.
* Retrieve AI risks by causal taxonomy: Entity, Intent, Timing.
* Get detailed information on specific risk entries.
* Framework-agnostic, designed for integration with any MCP-compatible agent architecture.

---

## Technologies

* Python 3.10+
* FastAPI
* Pandas
* Openpyxl
* Pydantic (for data modeling)
* Uvicorn (ASGI server)

---

## (Suggested) Directory Structure

```
ai-risk-mcp-server/
├── data/
│   └── ai_risk_repository.xlsx         # MIT Risk Database
├── app/
│   ├── main.py                         # FastAPI server
│   ├── tools.py                        # MCP tool implementations
│   ├── models.py                       # Data models (RiskItem, Evidence, etc.)
│   └── loader.py                       # Data ingestion logic
├── tests/
│   └── test_tools.py                   # Unit tests for tool logic
├── README.md                           # This file
└── requirements.txt                    # Python dependencies
```

---

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/ai-risk-mcp-server.git
cd ai-risk-mcp-server
```

### 2. Install Dependencies

```bash
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
```

### 3. Add Data File

Download the latest AI Risk Repository Excel file from [airisk.mit.edu](https://airisk.mit.edu/) and place it in the `data/` folder.

### 4. Run the Server

```bash
uvicorn app.main:app --reload
```

The server will start at `http://127.0.0.1:8000/`

---

## Available Tools (via MCP)

* `find_risks_by_keyword` – Search risks by description text.
* `find_risks_by_domain` – Filter risks by domain or subdomain.
* `find_risks_by_cause` – Retrieve risks by cause (Entity, Intent, Timing).
* `get_risk_details` – Fetch detailed info for a specific risk ID.

---

## Updating the Dataset

Replace the Excel file in the `data/` folder with the latest version from MIT and restart the server. An automated sync script will be added in future versions.

---

## Future Features

* Risk simulation tools
* Scenario-based assessment tools
* Full-text search indexing
* Multi-cause filtering support

---

## License

MIT License

---

## Acknowledgments

Based on the AI Risk Repository curated by MIT, available under CC BY 4.0.
