# F.A.I.T.H
### Fast Autonomous Intelligence Terminal Host

> A fully local, privacy-first AI agent that sees your screen, controls your computer, and executes complex tasks — all without sending a single byte to the cloud unless *you* allow it.

---

## ⚠️ Pre-Launch Notice

FAITH is currently in **development** A public release is planned for **Linux** **July 2026**.

- 🐧 **Linux** — Available for beta testing on July 2026
- 🪟 **Windows** — Coming after Linux stabilization
- Bugs and glitches are expected. Contributions and bug reports are welcome!

---

## What is FAITH?

FAITH is a local-first AI agent designed to autonomously control your computer, execute multi-step tasks, and interact with any application — all through a simple instruction interface.

Unlike cloud-based AI assistants, FAITH runs entirely on your machine. It only connects to the internet when you explicitly grant it permission. Your data never leaves your device by default.

FAITH is not a chatbot. It is a fully autonomous agent that can **see**, **think**, and **act** on your computer in real time.

---

## Features

- 🔒 **Privacy-First Architecture** — Fully local by default. Internet access is disabled unless you enable it.
- 👁️ **Screen Vision** — FAITH can see and understand your screen using a vision model.
- 🖱️ **Full Computer Control** — Clicks, types, scrolls, and interacts with any application automatically.
- 🧠 **Intelligent Brain** — Powered by local LLMs for reasoning, planning, and decision-making.
- 🎙️ **Voice Control** — Give instructions by voice; FAITH listens and executes.
- 💾 **Persistent Memory** — FAITH remembers context across sessions.
- 📄 **Document & PDF Generation** — Automatically creates reports, PDFs, and other documents.
- 🔍 **Research Agent** — Opens browser, reads pages, and compiles summaries autonomously.
- 📧 **Email & WhatsApp Automation** — Automates messaging workflows on your behalf.
- 💻 **Built-in Editor & Terminal** — A VS Code-style editor with an integrated terminal, built right in.
- 🧩 **Skill File System** — Teach FAITH any new application or workflow by writing a `.md` skill file.
- 🔌 **MCP Support** — Extend FAITH with external tools, APIs, and context via MCP servers.
- 🌐 **Auto Software Installer** — FAITH can search, download, and install required tools automatically. Administrator permission is always required manually for security.

---

## Architecture

FAITH is built on a modular, multi-model architecture. Each component has a specific role:

```
┌─────────────────────────────────────────────────┐
│                     F.A.I.T.H                   │
├──────────────┬──────────────┬───────────────────┤
│   🧠 Brain   │   👁️ Eyes    │    🖱️ Hands       │
│   GLM / LLM  │  Qwen Vision │   PyAutoGUI       │
│  Reasoning   │ Screen Read  │ Clicks & Typing   │
│  Planning    │ UI Detection │ App Interaction   │
├──────────────┴──────────────┴───────────────────┤
│              📄 Skill File System               │
│     .md instructions for any app or workflow    │
├─────────────────────────────────────────────────┤
│              🔌 MCP Integration                 │
│    External tools, APIs, and context sources    │
├─────────────────────────────────────────────────┤
│           🔒 Permission Layer                   │
│  Internet OFF by default — manual enable only   │
└─────────────────────────────────────────────────┘
```

### How a Task Works

1. You give FAITH an instruction (text or voice).
2. The **Brain (LLM)** plans the steps required.
3. The **Eyes (Qwen Vision)** reads the screen to understand the current state.
4. The **Hands (PyAutoGUI)** execute the required actions.
5. If a skill file exists for the target application, FAITH follows it precisely.
6. If an external tool or context is needed, FAITH uses **MCP**.
7. Output is generated — document, report, message, or any other result.

---

## System Requirements

FAITH supports three configuration tiers depending on your hardware:

### 🟢 Low-End Configuration
> Minimum viable setup for basic tasks

| Component | Requirement |
|-----------|-------------|
| RAM | 8 GB (12 GB recommended) |
| Storage | ~20 GB after installation |
| Python | 3.12+ |
| Default Brain Model | DeepSeek R1 (6B, ~5 GB) |

### 🟡 Mid-Range Configuration
> Balanced performance for most tasks

| Component | Requirement |
|-----------|-------------|
| RAM | 16–20 GB (24 GB recommended) |
| Storage | ~48 GB after installation |
| Python | 3.12+ |
| Brain Model | Mid-tier LLM combination |

### 🔴 Full Power Configuration
> Maximum capability — not for the faint of heart

| Component | Requirement |
|-----------|-------------|
| RAM | 30 GB minimum (40 GB recommended) |
| Storage | ~70 GB after installation |
| Python | 3.12+ |
| Brain Model | GLM 4.7 (~30 GB) |

> ⚠️ **Warning:** Do not attempt the Full Power configuration if you have less than 30 GB of RAM.

---

## Installation

> 🚧 Detailed installation scripts are being finalized before the July launch. The steps below reflect the expected setup process.

### Prerequisites

- Python 3.12 or higher
- Git
- Linux (Windows support coming soon)
- Sufficient RAM and storage for your chosen configuration tier (see above)

### Steps

```bash
# 1. Clone the repository
git clone https://github.com/bhooleop-droid/FAITH.git
cd FAITH

# 2. Install Python dependencies
pip install -r requirements.txt

# 3. Download your chosen models
# Instructions for each configuration tier are in /docs/models.md

# 4. Run FAITH
python main.py
```

> Administrator/sudo permission will be required during certain install steps for security reasons. FAITH will prompt you when needed and will never request elevated permissions silently.

---

## Skill File System

The Skill File System is what makes FAITH infinitely extensible. A skill file is a plain `.md` (Markdown) file that explains to FAITH how to use a specific application or complete a specific workflow — end to end.

### How It Works

1. Create a `.md` file inside the `/skills` directory.
2. Write step-by-step instructions in plain English (or JavaScript for programmatic flows).
3. FAITH reads the skill file and follows the instructions when working with that application.

### Example: Blender Skill File

```markdown
# Blender Skill

## Opening Blender
Launch Blender from the applications menu or terminal using `blender`.

## Creating a Basic 3D Object
1. Click "General" on the splash screen to create a new project.
2. Press A to select all, then Delete to clear the default scene.
3. Press Shift+A > Mesh > Cube to add a new cube.

## Exporting as .glb
1. Go to File > Export > glTF 2.0.
2. Choose your output path and click Export.
```

That's it. FAITH will now know how to work in Blender.

### Tips for Writing Skill Files

- Be specific and step-by-step.
- Include keyboard shortcuts where possible.
- Mention exact UI element names (button labels, menu paths).
- You can also use an LLM to generate skill files for you — just describe the workflow.

---

## MCP Integration

FAITH supports the **Model Context Protocol (MCP)** for connecting to external tools, APIs, databases, and context sources.

Use MCP when:
- FAITH needs real-time data (e.g., live search results, API responses)
- You want to connect FAITH to a specific service or database
- A task requires context that cannot be captured in a skill file alone

MCP servers can be configured in `/config/mcp.json`. Documentation for setting up MCP integrations will be available in `/docs/mcp.md` at launch.

---

## Internet & Privacy

FAITH is **offline by default**. It does not make any network requests without your explicit permission.

Internet access is only enabled when:
- You manually toggle internet permission ON in settings
- A specific task requires it and you approve it at runtime

Actions that may use the internet:
- Web search (Research Agent)
- File uploads
- MCP server connections
- Auto software download/installation

You are always in control.

---

## Contributing

FAITH is open source and contributions are welcome — especially from the Linux community. 🐧

### How to Contribute

1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature-name`
3. Make your changes
4. Commit: `git commit -m "Add: your feature description"`
5. Push: `git push origin feature/your-feature-name`
6. Open a Pull Request

### What We Need Help With

- Bug reports and reproducible issue descriptions
- Skill files for popular applications
- Model configuration guides for different hardware setups
- Windows compatibility testing (post-Linux stabilization)
- Documentation improvements
- Performance optimizations

### Reporting Bugs

Please open a GitHub Issue with:
- Your configuration tier (Low / Mid / Full)
- Your Linux distribution and version
- Steps to reproduce the bug
- Any relevant logs or screenshots

---

## Roadmap

- [x] Core agent loop (Brain + Eyes + Hands)
- [x] Voice control
- [x] Memory system
- [x] Skill file system
- [x] MCP integration
- [x] Built-in editor and terminal
- [x] Research agent
- [x] Email and WhatsApp automation
- [x] Document and PDF generation
- [ ] Public Linux beta release (July 2025)
- [ ] Windows support
- [ ] GUI installer
- [ ] Community skill file repository

---

## License

This project is open source. License details will be included at the time of public release.

---

## Disclaimer

FAITH is a powerful tool that can control your computer autonomously. Always review what you are asking it to do. The developers are not responsible for any unintended actions taken by the agent. Use responsibly.
