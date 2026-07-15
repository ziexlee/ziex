<div align="center">
  <img src="assets/ziex-logo.png" alt="zieX Logo" width="160" />
</div>

<h1 align="center">zieX · Your All-in-One Local AI Agent</h1>

<p align="center">Website: <a href="http://42.194.243.206">http://42.194.243.206</a> · Version v1.0.0 · OpenAI / domestic models supported</p>

<p align="center">
  🌐 <a href="read.md">简体中文</a> · <b>English</b> · <a href="read.ko.md">한국어</a> · <a href="read.ja.md">日本語</a>
</p>

zieX isn't just a chatbot. It reads your code repositories, analyzes Excel data, generates professional documents and charts, and runs command-line tools — **everything actually happens on your machine**, rather than merely "appearing" to happen.

It's a Codex-style local desktop agent (a native macOS window + a built-in local service) that brings threaded conversations, model settings, streaming output, workspace context, and real tool execution together in a single window — with a built-in Feishu (Lark) bot so you can drive it to work with a single sentence, anytime, anywhere.

<div align="center">
  <img src="assets/showcase-1.jpg" alt="zieX interface preview" width="760" />
</div>

> Above: a preview of the zieX main interface — threaded conversations, real-time tool cards, streaming output, and workspace context all integrated in the same window.

---

## 1. Core Capabilities

From daily office work to professional development, zieX covers all of your productivity scenarios with a single Agent system:

| Capability | Description |
| --- | --- |
| **Real Code Execution** | Not just chat. It can read, write, and modify code files in the workspace, run builds and tests, and complete a full development loop. |
| **Local Privacy First** | The Agent runs on your machine; file operations and command execution all happen locally. Your code and data never leave the device. |
| **Smart Intent Routing** | Built-in Planner, Review, Artifact and other specialized Agents automatically detect intent, break down tasks, and select the optimal toolchain. |
| **Deep File Understanding** | Supports analyzing PDF, Word, Excel, PPT, CSV, images, code repositories and more. Auto Excel statistics, image visual recognition, code call-chain tracing. |
| **Multimodal Creation** | Generates images, SVG charts, posters, document reports, educational problems and illustrations. From requirement to finished product in a single sentence. |
| **Web Research** | Integrates Web Search and URL fetching to gather real-time information, market data, and technical docs, cross-verified for reliable analysis. |
| **Feishu Bot** | Connects to Feishu conversations; @-mention the bot to trigger execution, with results and files sent straight back to Feishu. Mobile work can drive your local Agent too. |

---

## 2. Workflow

Every zieX task follows a closed loop from requirement to finished product:

1. **Describe your need** — Tell zieX in natural language what you want: write code, analyze data, generate a report, search for information — any task.
2. **Agent auto-plans** — The Planner Agent analyzes the intent, breaks the task into steps, and picks the most suitable tools and Agent branches to execute.
3. **Real execution & verification** — Read files, run commands, search the web, generate artifacts… each step runs locally for real and is automatically verified.
4. **Deliver complete results** — Code that builds successfully, files generated to the specified paths, analysis with data sources attached — you get finished products, not drafts.

---

## 3. Agent Toolset

zieX's "ability to act" comes from a set of tools that actually execute locally. Inside a bounded loop, the Agent **decides ↔ observes** and calls them one by one:

- **File**: `read_file` read a file · `write_file` write a file · `inspect_file` analyze a file · `analyze_spreadsheet` Excel data statistics
- **Command**: `shell` run a command line · `git_status` read Git status
- **Search**: `search` local search · `web_search` web search · `fetch_url` fetch a web page
- **Multimodal**: `screenshot_page` page screenshot · `crop_image` image crop · `create_image` generate an image
- **Creation**: `create_document` generate docs/reports/posters · `create_image` generate charts and illustrations
- **Orchestration & safety**: `parallel` parallel execution · `permission` permission check · `snapshot` pre-write snapshot · `context` context loading

> Every action is shown in real time as a "tool card" in the UI — you can see exactly what it is doing.

---

## 4. Security & Protection

An Agent that can write files and run commands must be controllable. zieX has defense-in-depth built in:

- **Tiered permission gating**: actions are allowed or blocked by `read / write / dangerousCommand / externalSend`; dangerous commands are denied by default.
- **Pre-write snapshot**: an automatic backup is taken before every write/modify, with one-click rollback.
- **Workspace sandbox**: all path operations are pinned inside the working directory; boundary crossing and `..` traversal are forbidden.
- **Post-execution self-check + bounded recovery**: after the model says "done," it verifies whether artifacts actually landed on disk and whether the code actually runs; if not, it retries a bounded number of times and reports honestly if it still fails — it never "pretends to be done."
- **Privacy protection**: outputs are scanned for keys/sensitive information; configuration and keys are stored only on your machine and never uploaded to zieX or platform servers.

---

## 5. Supported Models

zieX connects to OpenAI-compatible `/chat/completions` endpoints and lets you configure **reasoning / vision / image generation** models separately, auto-routing by task type. Built-in presets for domestic models:

- **DeepSeek**
- **Tongyi Qwen / DashScope-compatible mode**
- **Zhipu GLM** (incl. GLM-4V vision, CogView text-to-image)
- **Custom** — any OpenAI-compatible endpoint (self-hosted or private deployment both work)
---

## 6. Usage

### 1. Launch

```bash
cd /Users/zieli/Desktop/ziex
npm start          # build Ziex.app and open it
```

`npm start` compiles the native shell `Ziex.app` with clang and launches it. The app bundles a local service at `127.0.0.1:18765`.

Browser mode (fallback):

```bash
npm run server     # start only the local service and access it via a browser
```

### 2. Configure Models

Open **Settings → Model Settings** and, under the Reasoning / Vision / Image Generation tabs respectively, fill in:
- Full API URL (full endpoint)
- Model (model name)
- API Key

To connect the Feishu bot, switch to the **Feishu Bot** tab and enter the App ID and App Secret.

### 3. Start a Task

- Click **New chat** in the top-left to start a thread;
- Describe your need in natural language in the input box at the bottom, e.g. "Analyze this sales Excel and generate a charted weekly report";
- Type `/` to reference local files, or `@` to invoke saved **Skills**;
- After sending, the Agent will auto-plan, execute, verify, and deliver the result. You can use **Stop** to abort mid-run.

### 4. Skills

Skills are reusable task templates (e.g. a fixed-format weekly report, a fixed code-review flow). The **skills** menu on the left lets you view, create, and reuse them, turning repetitive work into a single sentence.

### 5. Feishu Bot

After configuring the App ID / App Secret in the Feishu app, a Feishu bot conversation appears in your conversation list. `@zieX` in Feishu to send a task; it runs locally for real, and the execution results and generated files are sent straight back to Feishu — drive your Agent even on business trips, commutes, or in meetings.

---

## 7. Website & Download

- **Website**: <http://42.194.243.206>
- **Current version**: v1.0.0
- **Supported platforms**: macOS (the Windows installer `ziex-setup.exe` is also provided)
- **Download**: visit the website to download it for free and run your private AI Agent on your computer within minutes.

> Whether you are a developer, a data analyst, or a content creator, zieX can be your capable AI assistant.
