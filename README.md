# ⚡ BeamLab CLI

**A production-grade, autonomous AI coding agent for your terminal.**

BeamLab is a high-performance CLI agent designed to live in your codebase. It doesn't just chat—it searches, reads, reasons, and executes code changes with surgical precision. Powered by a multi-provider "cascade" (LongCat, Gemini, Ollama), it ensures you always have a brain online, even when APIs are down.

---

## 🚀 Quick Start

### 1. Installation
Install directly via pip:
```bash
pip install beamlab
```

### 2. Configure Your Keys
BeamLab uses environment variables for security. Add these to your shell profile (`.zshrc`, `.bashrc`, or PowerShell `$PROFILE`):

```bash
export LONGCAT_API_KEY="your-key-here"
export GEMINI_API_KEY="your-key-here"
```

### 3. Launch
Navigate to any project directory and start the session:
```bash
beamlab
```

---

## 🧠 Functional Overview

BeamLab operates as a **Stateful Agentic Loop**. When you give it a task, it follows a rigorous internal cycle:
1.  **Context Retrieval**: It perform semantic searches across your repo using a local **FAISS** vector store.
2.  **Reasoning**: It uses "Thinking" models (like `LongCat-Flash-Thinking`) to architect a solution.
3.  **Tool Execution**: It uses specialized tools for file I/O, code searching, shell commands, and web research.
4.  **Verification**: It can run tests and verify its own changes before handing the reins back to you.

---

## 🛠️ Interactive Slash Commands

While in the BeamLab REPL, you can use `/` commands to manage your session:

| Command | Description | Usage |
| :--- | :--- | :--- |
| `/help` | List all available commands | `/help` |
| `/sessions` | List all stored sessions for this project | `/sessions` |
| `/new` | Start a fresh named session | `/new "Fixing Bug"` |
| `/switch` | Switch to a different session by ID or number | `/switch 2` |
| `/model` | Show or change the active LLM | `/model longcat:vision` |
| `/provider` | Switch between LongCat, Gemini, and Ollama | `/provider gemini` |
| `/add` | Manually pin a file to the context | `/add src/main.py` |
| `/undo` | Roll back the last file modification | `/undo` |
| `/clear` | Wipe the current chat history | `/clear` |

---

## ⚙️ Configuration (`.agent.toml`)

BeamLab looks for a `.agent.toml` file in your project root for local overrides.

```toml
[model]
primary     = "LongCat-Flash-Lite"
fallback    = "gemini-2.5-pro"
temperature = 0.1

[safety]
require_approval_for_writes = true   # Set to false for full autonomy
require_approval_for_shell  = true

[indexing]
exclude = [".git", "node_modules", "dist"]
```

### 📎 Context Shortcuts
- **@File Reference**: Mention any file with `@` (e.g., "Explain how @main.py works") to instantly feed that file's content into the agent's context.

---

## 🛡️ Safety First
BeamLab is built with a **Security-First** mindset:
- **Write Guard**: Every file modification requires your explicit approval by default.
- **Shell Guard**: No `rm -rf` or arbitrary commands run without a "Y/N" confirmation.
- **Path Restricted**: The agent is restricted to working within your project root unless specified otherwise.

---

## 👤 Author
**Muhammad Yasir (devxyasir)**  
Email: [jamyasir0535@gmail.com](mailto:jamyasir0535@gmail.com)  
GitHub: [devxyasir/beamlab](https://github.com/devxyasir/beamlab)

---
*Developed with love for the Python community. ⚡🚀*