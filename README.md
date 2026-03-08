AI Research Digest Automation (n8n + Gemini)

An automated AI-powered workflow that monitors newly published Artificial Intelligence research papers from arXiv, generates concise bullet-point insights using Google Gemini, and stores them in Google Sheets as a continuously updating research digest.

This project demonstrates how LLMs can be integrated with workflow automation tools to build real-world AI data pipelines.

Project Overview

The system automatically:

• Fetches the latest AI research paper from the arXiv API
• Extracts the title and abstract
• Generates a structured prompt
• Uses Google Gemini to generate 3 bullet-point insights
• Stores the output in Google Sheets
• Prevents duplicate processing using workflow logic

The workflow runs on a scheduled trigger, acting as a lightweight AI research monitoring system.

Architecture
Schedule Trigger
      ↓
arXiv API
      ↓
XML → JSON Conversion
      ↓
Prompt Generation
      ↓
Google Sheets Lookup
      ↓
IF Node
   ├ Existing Paper → Skip
   └ New Paper
         ↓
     Gemini Summarizer
         ↓
     Format Output
         ↓
     Append Row to Google Sheets
Workflow Overview




The automation pipeline is orchestrated using n8n, which connects external APIs, AI models, and storage services.

Example Output




Generated research insights are stored in Google Sheets.

Example structure:

Date	Title	Insights
2026-03-01	RoboPocket: Improve Robot Policies Instantly with Your Phone	• Smartphone-based system for robot policy improvement • Uses AR to visualize predicted robot trajectories • Improves data efficiency compared to offline imitation learning
IF Logic Scenarios

The workflow includes decision logic to ensure only new research papers are processed.

Scenario 1 — New Paper
Title NOT found in Google Sheets

Flow:

arXiv → Prompt → IF (False)
              ↓
          Gemini
              ↓
         Store result

Outcome:

• Bullet-point insights generated
• Paper added to research digest

Scenario 2 — Duplicate Paper
Title FOUND in Google Sheets

Flow:

arXiv → Prompt → IF (True)
              ↓
             Skip

Outcome:

• Gemini API not called
• Duplicate entry avoided

Scenario 3 — No Data Returned

If arXiv returns no entries:

Workflow exits gracefully

No unnecessary API calls are made.

Sample Data (7-Day Usage)

The workflow has been used for 7 consecutive days to automatically build a small AI research digest.

Date	Title	Insights
2026-03-01	RoboPocket: Improve Robot Policies Instantly with Your Phone	• Smartphone-based robot policy training system • Uses AR visual foresight • Improves imitation learning data efficiency
2026-03-02	Efficient Transformer Architectures for Long Context Reasoning	• Introduces long-context transformer architecture • Reduces computational cost • Improves reasoning performance
2026-03-03	Autonomous Multi-Agent Collaboration using LLM Planning	• Framework for LLM-driven agent collaboration • Enables distributed task execution • Improves planning success rate
2026-03-04	Self-Supervised Visual Transformers	• Self-supervised training for vision transformers • Reduces dependency on labeled datasets • Competitive performance on vision benchmarks
2026-03-05	Reinforcement Learning for Scalable Robot Manipulation	• RL-based robot manipulation pipeline • Uses simulation for faster training • Improves real-world robustness
2026-03-06	Retrieval-Augmented Generation for Scientific Knowledge	• Combines RAG with structured research databases • Improves factual accuracy • Reduces hallucinations
2026-03-07	Multi-Modal AI for Autonomous Driving	• Integrates vision, LiDAR and textual reasoning • Improves perception accuracy • Enhances decision-making safety
Tech Stack

Automation

n8n

AI

Google Gemini API

Data Source

arXiv API

Storage

Google Sheets API

Integration

REST APIs

JSON

HTTP requests

Key Concepts Demonstrated

• Workflow automation
• LLM integration into pipelines
• API orchestration
• Prompt engineering
• Conditional workflow logic
• Automated knowledge ingestion

Setup Instructions

Install n8n

Import the workflow

workflow.json

Add credentials

Gemini API key
Google Sheets access

Configure schedule trigger

Activate workflow

The system will begin generating a daily AI research digest automatically.

Future Improvements

Possible extensions:

• Summarize full research PDFs instead of abstracts
• Send daily research digest via email or Slack
• Build a RAG-based research assistant on top of collected papers
• Store research data in a vector database for semantic search

Author
Anuj Pundora

Built as a learning project exploring AI automation, workflow orchestration, and LLM-powered data pipelines.


