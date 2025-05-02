# MCP Demo Project

This project demonstrates how to use Model Context Protocol (MCP) agents with browser automation and search tools, powered by Playwright, Airbnb, and DuckDuckGo integrations. It features an interactive chat interface with memory, using OpenAI or Groq LLMs.

---

## Table of Contents
- [Project Overview](#project-overview)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Environment Variables](#environment-variables)
- [Running the Project](#running-the-project)
- [How to Use](#how-to-use)
- [MCP Server Configuration](#mcp-server-configuration)
- [Troubleshooting](#troubleshooting)

---

## Project Overview
This project allows you to:
- Chat with an AI agent that can use browser automation and search tools.
- Automate browser actions (search, click, fill, etc.) using Playwright.
- Search for hotels and listings using Airbnb and DuckDuckGo integrations.
- Use memory-enabled conversations for context-aware chat.

---

## Prerequisites
- **Python >=3.13**
- **Node.js 16+** (for Playwright and MCP servers)
- **npm** (Node.js package manager)
- **Git** (recommended)

---

## Installation
1. **Clone the repository:**
   ```sh
   git clone https://github.com/AnupCloud/MCP.git
   cd mcp_demo
   ```

2. **Create a Python virtual environment (recommended):**
   ```sh
   uv venv 
   source .venv/bin/activate
   ```

3. **Install Python dependencies:**
   ```sh
   uv add -r requirements.txt
   # If requirements.txt is missing, install manually:
   uv add python-dotenv
   ```

4. **Install Node.js dependencies (for Playwright):**
   ```sh
   npm install playwright
   # Optionally, install MCP servers globally if needed:
   sudo npm install -g @playwright/mcp @openbnb/mcp-server-airbnb duckduckgo-mcp-server
   ```
5. **If you do not have a package.json yet**
   ```sh
   # To create one.
   npm init -y
   # Then, install your dependencies If you know which packages you need (e.g., zod, @playwright/mcp, etc.), install them:
   npm install zod @playwright/mcp @modelcontextprotocol/sdk
   ```

---

## Environment Variables
Create a `.env` file in the project root with your API keys:

```
OPENAI_API_KEY=your-openai-api-key
GROQ_API_KEY=your-groq-api-key  # (optional, if using Groq)
```

---

## Running the Project
1. **Start the MCP servers (optional, usually auto-started):**
   - The configuration in `browser_mcp.json` will auto-launch the required MCP servers for Playwright, Airbnb, and DuckDuckGo.

2. **Run the main chat application:**
   ```sh
   uv run app.py
   ```

---

## How to Use
- When you run `uv run app.py`, you'll enter an interactive chat.
- Type your queries (e.g., "Find hotels in Hyderabad on 10th May 2025 ").
- The agent will use the configured tools to answer your queries.
- Type `exit` or `quit` to end the chat.
- Type `clear` to clear the conversation history.

---

## MCP Server Configuration
- MCP servers are configured in `browser_mcp.json`.
- Example:
  ```json
  {
    "mcpServers": {
      "playwright": { "command": "npx", "args": ["@playwright/mcp@latest"] },
      "airbnb": { "command": "npx", "args": ["-y", "@openbnb/mcp-server-airbnb", "--ignore-robots-txt"] },
      "duckduckgo-search": { "command": "npx", "args": ["-y", "duckduckgo-mcp-server"] }
    }
  }
  ```
- You can add or modify servers as needed.

---

## Troubleshooting
- **Permission errors with npm:** Use `sudo` for global installs or set up a user-local npm directory.
- **Module not found errors:** Ensure all dependencies are installed and your virtual environment is activated.
- **API errors:** Check your `.env` file for correct API keys.
- **Playwright browser issues:** Run `npx playwright install` to ensure browsers are installed.
- **Robots.txt/Access errors:** Some APIs (like Airbnb) may restrict automated access. Use browser automation as a workaround.

---

Enjoy automating with MCP and AI! If you have any questions or need further help, just ask.
