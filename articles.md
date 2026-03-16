# Google Antigravity IDE — Article Summaries

---

## Article 1: Google Developers Blog — "Build with Google Antigravity, our new agentic development platform"
**Source:** https://developers.googleblog.com/build-with-google-antigravity-our-new-agentic-development-platform/

Google introduced Antigravity as an AI-powered development platform that positions autonomous agents as the primary workers, not the developer. The platform features a **dual-interface design**:

- **Editor View**: A conventional AI-powered IDE with tab completion and inline commands for synchronous coding.
- **Manager Surface**: A dedicated orchestration dashboard for running multiple agents asynchronously across different workspaces.

Agents can autonomously plan, execute, and verify complex tasks across the editor, terminal, and browser. Instead of raw logs, agents generate tangible **Artifacts** — screenshots, recordings, task lists, and implementation plans — that developers can annotate with inline feedback similar to document comments. A **Knowledge Base** feature retains context and code snippets for improved future performance.

**Availability:** Public preview launched November 20, 2025. Free for individuals on macOS, Windows, and Linux. Supported models include Gemini 3 Pro (primary), Claude Sonnet 4.5, and GPT-OSS.

---

## Article 2: InfoWorld — "A first look at Google's new Antigravity IDE"
**Source:** https://www.infoworld.com/article/4096113/a-first-look-at-googles-new-antigravity-ide.html

InfoWorld's hands-on review describes Antigravity as a VS Code fork focused on developer-AI agent collaboration. Developers can switch between **Planning Mode** (deliberate, with oversight artifacts) and **Fast Mode** (direct command execution), controlling how often they review each step.

The IDE supports multiple AI models: **Gemini 3 Pro** (high/low), **Claude Sonnet 4.5** (including a "thinking" variant), and **GPT-OSS 120B Medium**. Agents generate task lists and plans that developers can annotate like a Word document; **Knowledge Items** persist patterns across sessions.

Google's **Nano Banana** service handles image/mockup generation, and a Chrome browser extension enables full browser automation with fallback capabilities.

**Notable limitations:**
- Moving project directories can silently break Knowledge Item retention.
- Agent outputs are not always predictable.
- A security vulnerability regarding potential backdoor attacks was disclosed by researcher Mindgard (Google working on a fix).

**Competitive note:** Unlike AWS Kiro (Claude-only), Antigravity offers model variety but lacks Kiro's workflow execution hooks.

---

## Article 3: Chrome Unboxed — "Google launches Antigravity, a new AI-powered IDE for autonomous agentic coding"
**Source:** https://chromeunboxed.com/google-launches-antigravity-a-new-ai-powered-ide-for-autonomous-agentic-coding/

Chrome Unboxed frames Antigravity as a fundamental shift — AI is no longer a sidebar chatbot but an **autonomous developer collaborator**. The platform grants agents access to three critical tools: the **Code Editor**, the **Terminal**, and the **Browser**, enabling them to write code, run servers, and test functionality in a real Chrome instance without human intervention at each step.

Agents produce **Artifacts** including screen recordings that prove the code actually works in a browser — functioning as a form of automated QA. The **Manager Surface** dashboard lets developers orchestrate multiple parallel agents, enabling simultaneous work on backend fixes and frontend prototypes.

**Technical foundation:** Built on a fork of Microsoft's open-source VS Code, ensuring compatibility with existing extensions and a familiar user interface. Available free in public preview for macOS, Windows, and Linux.

---

## Article 4: DevRadar — "Google Antigravity vs Windsurf 2026: Which IDE to Choose"
**Source:** https://devradar.dev/compare/google-antigravity-vs-windsurf-2026

This comparison article pits Antigravity against Windsurf (by Codeium), two competing visions for AI-native development.

| | **Google Antigravity** | **Windsurf** |
|---|---|---|
| **Approach** | Agent-first, autonomous task execution | AI-enhanced traditional editor |
| **AI Engine** | Gemini 3 Pro + multi-model | Cascade engine, Flow awareness |
| **Strengths** | Hands-off automation, parallel agents, VS Code base | Enterprise readiness, full-stack debugging, data privacy |
| **Weaknesses** | Early-stage instability, IT policy conflicts | Resource-heavy indexing, escalating costs |
| **Best for** | Frontend prototyping, rapid autonomous dev | Complex refactoring, enterprise environments |

Both offer free tiers. The article recommends **Antigravity for solo developers and startups** wanting rapid prototyping, and **Windsurf for enterprises** requiring data privacy and stable multi-file refactoring.

---

## Article 5: Google Codelabs — "Getting Started with Google Antigravity"
**Source:** https://codelabs.developers.google.com/getting-started-google-antigravity

Google's official getting-started guide walks through setup and core concepts. Installation involves downloading the app, authenticating with a Gmail account, and installing the Chrome extension.

Key concepts covered:
- **Agent Manager ("Mission Control")**: Spawn and monitor multiple autonomous agents in parallel, replacing linear chatbot interaction.
- **Rules & Workflows**: System-level guidelines and saved prompts that shape agent behavior per workspace or globally.
- **Security Framework**: Granular terminal allow/deny lists and browser URL allowlisting protect against prompt injection and unauthorized access.
- **Skills**: Domain-specific knowledge modules that load conditionally to specialize agent behavior.
- **Artifacts**: Structured outputs (task lists, code diffs, screenshots, recordings) that developers review and approve before acceptance.

Developers interact by defining high-level objectives, providing Google Docs-style comments on agent plans, and toggling between the Agent Manager and traditional Editor views.
