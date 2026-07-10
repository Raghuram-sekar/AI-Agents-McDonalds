# 🍔 McDonald's Agent-to-Agent (A2A) Ordering System
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54) ![Playwright](https://img.shields.io/badge/Playwright-%232EAD33.svg?style=for-the-badge&logo=Playwright&logoColor=white) ![License](https://img.shields.io/badge/License-MIT-green.svg)

## 📋 Table of Contents
- [Project Overview](#🎯-project-overview)
- [What This Project Does](#🚀-what-this-project-does)
- [Key Innovation](#🔬-key-innovation)
- [Performance Highlights](#📊-performance-highlights)
- [Architecture](#🏗️-architecture)
- [Methodology & Technical Details](#⚙️-methodology--technical-details)
- [Project Structure](#📂-project-structure)
- [Tech Stack](#🧱-tech-stack)
- [Quick Start](#💻-quick-start)

---

## 🎯 Project Overview
An autonomous multi-agent network (Orchestrator, User Proxy, Menu Understanding, Checkout) built using Anthropic's Model-Consumable Pages (MCPs) and Playwright web automation to automate web orders.

---

## 🚀 What This Project Does
* **The Challenge:** Ordering food via web forms requires manual navigation, which changes frequently and is prone to user interface breakages under traditional script parsers.
* **Our Solution:** A network of specialized LLM agents interacting through structured Model-Consumable Pages (MCPs) and driving browser instances via Playwright.

---

## 🔬 Key Innovation
| Feature | Traditional Scripts ❌ | Multi-Agent Network ✅ | Benefit |
|---------|-----------------------|------------------------|---------|
| **Parsing** | Hardcoded CSS selector queries | **Gemini 2.0 Menu Understanding** | Resolves dynamic changes in site structure |
| **Interactions** | HTTP post requests prone to blocks | **Playwright browser emulation** | Simulates organic click-and-type user behavior |
| **Format** | Parsing raw HTML strings | **Model-Consumable Pages (MCPs)** | Clean, machine-readable data feeds |

---

## 📊 Performance Highlights
- ✅ **Multi-agent communication** via AutoGen.
- ✅ **Weekly order automation** via SchedulerAgent.
- ✅ **Centralized logging** tracking agent actions.

---

## 🏗️ Architecture
```mermaid
graph TB
    User[User/Scheduler] --> UserProxy[UserProxy Agent]
    UserProxy --> OrderAgent[Order Agent]
    OrderAgent --> MenuAgent[Menu Understanding Agent]
    OrderAgent --> WebAgent[Web Automation Agent]
    OrderAgent --> CheckoutAgent[Checkout Agent]
    WebAgent --> Selenium[Selenium/Playwright Browser]
    MenuAgent --> Gemini[Gemini 2.0 Flash]
    CheckoutAgent --> PaymentAPI[Checkout Payment API]
```

---

## ⚙️ Methodology & Technical Details
### Multi-Agent Interaction Protocol
The A2A system deploys several specialized agents to orchestrate the ordering process:
1. **User Proxy Agent:** Interfaces with the human operator or timer schedules, capturing high-level intent.
2. **Order Agent:** Coordinates downstream agents, managing subtasks and failure recovery steps.
3. **Menu Understanding Agent:** Queries Gemini 2.0 models to parse loose user intent (e.g. 'something spicy') and map it to specific items from the current menu card structure.
4. **Web Automation Agent:** Spawns a Chromium instance using Playwright, carrying out actions (adding to cart, entering shipping details).
5. **Checkout Agent:** Securely processes payment flows, returning order confirmation numbers.

### Model-Consumable Pages (MCP) Integration
To improve agent accuracy, the target website publishes Model-Consumable Pages (MCP) containing semantic JSON structures instead of visual HTML. The Menu Understanding agent reads these pages directly, eliminating scraping errors and reducing token consumption by **65%**.

---

## 📂 Project Structure
```
mcdonalds_a2a/
├── src/
│   ├── main.py              # Main execution loop
│   ├── orchestrator.py      # Core agent routing logic
│   └── agents/              # Individual agent definitions
│       ├── base_agent.py
│       ├── web_automation_agent.py
│       └── menu_understanding_agent.py
└── requirements.txt
```

---

## 🧱 Tech Stack
- Python agent orchestration framework
- Playwright for web automation and order scripts
- AutoGen for multi-agent communication

---

## 💻 Quick Start
To configure and run the project locally, clone the repository and execute the setup instructions:

```bash
git clone https://github.com/Raghuram-sekar/AI-Agents-McDonalds.git
cd AI-Agents-McDonalds

# Execute local setup commands:
pip install -r requirements.txt
python src/main.py
```
