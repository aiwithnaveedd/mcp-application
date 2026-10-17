# LangGraph Multi-Server MCP Agent

An interactive AI agent built with **LangGraph** and **LangChain** that seamlessly connects to multiple **Model Context Protocol (MCP)** servers. This setup allows the agent to dynamically access and query external tools across both remote HTTP and local stdio integrations.

## 🚀 Overview

This application configures a ReAct (Reasoning + Acting) AI agent capable of using multiple MCP tools simultaneously:

- **Context7 MCP Server (`streamable_http`):** Fetch live library documentation and modern code references.
- **Met Museum MCP Server (`stdio`):** Search and retrieve artwork metadata from The Metropolitan Museum of Art collection using `npx metmuseum-mcp`.

The agent maintains conversational context across turns using an in-memory checkpointer (`InMemorySaver`).

---

## 🛠️ Architecture & Features

- **Multi-Server MCP Adapter:** Uses `MultiServerMCPClient` from `langchain-mcp-adapters` to unify HTTP and `stdio` tools into a single toolset.
- **LangGraph ReAct Agent:** Built with `create_react_agent` powered by OpenAI's `gpt-5-nano` model.
- **Stateful Memory:** Persists thread state across user prompts via `InMemorySaver`.
- **Interactive CLI:** Terminal menu for continuous back-and-forth interactions with full context retention.

---

## 📋 Prerequisites

- **Python:** `3.10` or higher
- **Node.js & npx:** Installed on your system (required to execute the `metmuseum-mcp` stdio transport)
- **OpenAI API Key:** Active key with access to OpenAI chat models

---

## 📦 Installation & Setup

1. **Clone the Repository**
 git clone 
2. Install Dependencies

Bash
pip install langchain-mcp-adapters langgraph langchain-openai
Set Up Environment Variables
Export your OpenAI API Key:

Bash
# On macOS/Linux:
export OPENAI_API_KEY="your-openai-api-key"

# On Windows (Command Prompt):
set OPENAI_API_KEY=your-openai-api-key

# On Windows (PowerShell):
$env:OPENAI_API_KEY="your-openai-api-key"
🏃 Running the Application
Execute the Python script:

Bash
python main.py
Script Execution Flow
Initializes MultiServerMCPClient and establishes connections to Context7 and met-museum.

Fetches all registered tools dynamically.

Automatically triggers an introductory prompt to outline agent capabilities.

Drops into an interactive CLI loop:

Option 1: Ask questions (e.g., query code docs or museum artwork).

Option 2: Exit the interactive shell.

📂 Code Reference
Python
# Key configuration snippet
client = MultiServerMCPClient(
    {
        "context7": {
            "url": "[https://mcp.context7.com/mcp](https://mcp.context7.com/mcp)",
            "transport": "streamable_http",
        },
        "met-museum": {
            "command": "npx",
            "args": ["-y", "metmuseum-mcp"],
            "transport": "stdio",
        }
    }
)
📄 License
Distributed under the MIT License. See LICENSE for more information.


---

<ElicitationsGroup message="Next options for your GitHub setup:">
  <Elicitation label="Add an MIT License file content" query="Generate a standard MIT License file for my GitHub repository."/>
  <Elicitation label="Create a requirements.txt file" query="Generate a complete requirements.txt file for this Python MCP project."/>
</ElicitationsGroup>
   ```bash
   git clone [https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git](https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git)
   cd YOUR_REPOSITORY_NAME
