# AI Research Digest Automation (n8n + Gemini)

An automated AI pipeline that monitors new Artificial Intelligence research papers from arXiv, summarizes them using Google's Gemini model, and stores structured summaries in Google Sheets.

## Overview

This project demonstrates how LLMs can be integrated with workflow automation tools to build a real-world AI data pipeline.

The system automatically:

• Fetches the latest AI research paper from arXiv
• Extracts the paper title and abstract
• Generates a structured prompt
• Summarizes the research using Gemini AI
• Stores results in Google Sheets
• Prevents duplicate summaries using a lookup check

The workflow runs on a scheduled trigger and acts as a lightweight AI research monitoring agent.

---

## Architecture

```
Schedule Trigger
      ↓
arXiv API
      ↓
XML → JSON Conversion
      ↓
Prompt Generation
      ↓
Duplicate Check (Google Sheets)
      ↓
IF Node
   ├ Existing Paper → Stop
   └ New Paper
         ↓
     Gemini Summarizer
         ↓
     Data Formatting
         ↓
     Store in Google Sheets
```

---

## Tech Stack

* **n8n** – Workflow automation
* **Google Gemini API** – LLM summarization
* **arXiv API** – Research paper data source
* **Google Sheets API** – Data storage
* **JSON / HTTP APIs**

---

## Example Output

| Date       | Title                                                        | Summary                    |
| ---------- | ------------------------------------------------------------ | -------------------------- |
| 2026-03-07 | RoboPocket: Improve Robot Policies Instantly with Your Phone | • Introduces RoboPocket... |

---

## Key Features

* Automated AI research monitoring
* LLM-powered summarization
* API orchestration using n8n
* Duplicate detection logic
* Scheduled pipeline execution

---

## Setup

1. Install **n8n**
2. Import `workflow.json`
3. Add your **Gemini API key**
4. Configure **Google Sheets credentials**
5. Activate the schedule trigger

---

## Use Cases

• AI research tracking
• Knowledge digest automation
• LLM workflow orchestration examples
• Learning project for AI agents and automation

---

## Future Improvements

* Summarize full research PDFs
* Send summaries via email or Slack
* Vector database for research search
* RAG-based paper querying

---

## Author

Built as a learning project exploring AI agents, LLM workflows, and automation.
