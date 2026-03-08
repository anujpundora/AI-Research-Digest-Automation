# 🤖 AI Research Digest Automation

### n8n + Gemini + arXiv

An **AI-powered automation workflow** that monitors newly published Artificial Intelligence research papers from **arXiv**, generates **bullet-point insights using Google Gemini**, and stores them in **Google Sheets** as a continuously updating research digest.

This project demonstrates how **LLMs can be integrated with workflow automation tools to build real-world AI pipelines.**

---

# 🚀 Project Overview

The system automatically:

✅ Fetches the **latest AI research papers** from the arXiv API
✅ Extracts the **paper title and abstract**
✅ Generates a structured **LLM prompt**
✅ Uses **Google Gemini** to produce **3 concise bullet-point insights**
✅ Stores results in **Google Sheets**
✅ Prevents duplicate processing using workflow logic

The workflow runs on a **scheduled trigger**, acting as a lightweight **AI research monitoring system**.

---

# 🧠 System Architecture

```
Schedule Trigger
      │
      ▼
arXiv API
      │
      ▼
XML → JSON Conversion
      │
      ▼
Prompt Generation
      │
      ▼
Google Sheets Lookup
      │
      ▼
IF Node
 ├─ Paper Exists → Skip
 └─ New Paper
       │
       ▼
   Gemini AI
       │
       ▼
  Format Output
       │
       ▼
Store in Google Sheets
```

---

# 🛠 Workflow (n8n)

![Workflow](media/workflow.png)

The pipeline is orchestrated using **n8n**, which integrates APIs, automation, and AI models into a single workflow.

---

# 📊 Example Output

![Example Output](media/output-example.png)

Generated research insights are stored as a structured dataset.

| Date       | Title                                                        | Insights                                                                                                                       |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| 2026-03-01 | RoboPocket: Improve Robot Policies Instantly with Your Phone | • Smartphone-based robot policy training system • Uses AR to visualize predicted robot trajectories • Improves data efficiency |

---

# ⚙️ Workflow Logic

The automation includes **decision logic** to ensure only new papers are processed.

---

## Scenario 1 — New Research Paper

```
Title NOT found in Google Sheets
```

Flow:

```
arXiv → Prompt → IF(False)
               ↓
            Gemini
               ↓
           Store Output
```

Result:

✔ Bullet-point insights generated
✔ Entry added to research digest

---

## Scenario 2 — Duplicate Paper

```
Title FOUND in Google Sheets
```

Flow:

```
arXiv → Prompt → IF(True)
               ↓
              Skip
```

Result:

✔ Gemini API not called
✔ Duplicate entries prevented

---

## Scenario 3 — No Paper Returned

```
arXiv returns empty result
```

Result:

✔ Workflow exits gracefully
✔ No unnecessary API calls

---

# 📅 Sample Data (7-Day Usage)

This workflow has been used **personally for 7 days**, automatically collecting AI research insights.

| Date       | Title                                                        | Insights                                                                                                             |
| ---------- | ------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------- |
| 2026-03-01 | RoboPocket: Improve Robot Policies Instantly with Your Phone | • AR visual foresight for robot policies • Smartphone-based data collection • Improves imitation learning efficiency |
| 2026-03-02 | Efficient Transformer Architectures                          | • Long-context transformer architecture • Reduced compute cost • Improved reasoning benchmarks                       |
| 2026-03-03 | Multi-Agent Collaboration with LLM Planning                  | • LLM planning for distributed agents • Improved collaboration frameworks • Higher task success rates                |
| 2026-03-04 | Self-Supervised Visual Transformers                          | • Self-supervised training pipeline • Reduced labeled data requirements • Competitive vision benchmarks              |
| 2026-03-05 | Reinforcement Learning for Robot Manipulation                | • Simulation-based RL training • Improved manipulation robustness • Faster policy training                           |
| 2026-03-06 | Retrieval-Augmented Generation for Science                   | • Combines RAG with research databases • Improves factual responses • Reduces hallucinations                         |
| 2026-03-07 | Multi-Modal AI for Autonomous Driving                        | • Vision + LiDAR fusion model • Improved perception accuracy • Safer decision-making                                 |

---

# 🧰 Tech Stack

### Automation

* **n8n**

### AI

* **Google Gemini API**

### Data Source

* **arXiv API**

### Storage

* **Google Sheets API**

### Integration

* REST APIs
* JSON
* HTTP Requests

---

# 🧩 Concepts Demonstrated

This project demonstrates:

• Workflow orchestration
• LLM integration into real pipelines
• Prompt engineering
• API orchestration
• Conditional automation logic
• Automated knowledge ingestion

---

# ⚡ Setup

### 1️⃣ Install n8n

```
npm install n8n -g
```

### 2️⃣ Import Workflow

Import:

```
workflow.json
```

### 3️⃣ Configure Credentials

Add:

```
Gemini API key
Google Sheets credentials
```

### 4️⃣ Activate Schedule

Enable the trigger to start generating **daily AI research insights automatically**.

---

# 🔮 Future Improvements

Planned extensions:

• Summarize **full research PDFs** instead of abstracts
• Send daily digest via **email or Slack**
• Build a **RAG-based research assistant** on top of stored papers
• Store research in a **vector database for semantic search**

---

# 👨‍💻 Author

Built as a learning project exploring:

**AI automation • workflow orchestration • LLM-powered pipelines**

---

