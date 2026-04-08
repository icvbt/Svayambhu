# 🕉️ Svayambhu

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python Version](https://img.shields.io/badge/python-3.9%2B-blue.svg)](https://www.python.org/)
[![Google Cloud](https://img.shields.io/badge/Google%20Cloud-Datastore-blue?logo=google-cloud)](https://cloud.google.com/datastore)
[![FastAPI](https://img.shields.io/badge/FastAPI-005571?logo=fastapi)](https://fastapi.tiangolo.com/)

**Svayambhu** (Sanskrit for *Self-born*) is an autonomous Workspace Executive Assistant. It uses a multi-agent orchestration layer to manage tasks and notes for **Taksshak**, powered by Gemini 1.5 and the Model Context Protocol (MCP).

---

## 📖 Project Overview

Unlike simple chatbots, Svayambhu is an **agentic system**. It uses a hierarchical workflow to process user intent, maintain state across different sub-agents, and interact directly with Google Cloud Datastore to persist workspace data.

### 🧠 Core Intelligence
* **Orchestration:** Built using the `google.adk` (Agent Development Kit).
* **Protocol:** Implements `FastMCP` for standardized tool definition and execution.
* **Workflow:** Uses a `SequentialAgent` pattern to hand off control from input processing to task execution.

---

## 🏗️ Agent Architecture

The system follows a three-tier logic flow to ensure reliability and context retention:

1.  **Root Agent:** The entry point. It captures raw user input and bridges it into the `ToolContext` state.
2.  **Workflow Agent:** A sequential manager that guides the process toward the workspace logic.
3.  **Workspace Agent:** The "Executive Assistant." It has the persona of a professional assistant and holds the "keys" to the database tools.

---

## 🛠️ Integrated Tools

The assistant is equipped with the following capabilities via the **WorkspaceTools** MCP server:

| Tool | Description |
| :--- | :--- |
| `add_task` | Creates a new task entity in Datastore with a timestamp. |
| `list_tasks` | Retrieves and formats all pending and completed tasks. |
| `complete_task` | Marks a specific task as done using its numeric ID. |
| `add_note` | Saves long-form detailed notes for future reference. |

---

## 🚀 Setup & Installation

### Prerequisites
* Python 3.9+
* A Google Cloud Project with **Datastore Mode** enabled.
* Application Default Credentials (ADC) configured locally.

### 1. Clone the Repository
bash
git clone [https://github.com/icvbt/Svayambhu.git](https://github.com/icvbt/Svayambhu.git)
cd Svayambhu****

### 2. Environment Configuration
Create a .env file in the root directory:

Code snippet
MODEL=gemini-1.5-flash
PORT=8080

### 3. Install Dependencies
Bash
pip install -r requirements.txt

### 4. Run the Server
Bash
python main.py
