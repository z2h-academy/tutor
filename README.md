**English** | [Español](README.es.md)

<p align="center">
  <img src="logo.svg" alt="TUTOR — Z2H Academy" width="520">
</p>

<p align="center">
  <strong>Stop watching courses. Build with AI.</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/stable-0.10.0-ffd300?style=flat-square" alt="stable 0.10.0">
  <img src="https://img.shields.io/badge/pre--release-0.10.2--rc.2-2f81f7?style=flat-square" alt="pre-release 0.10.2-rc.2">
  <img src="https://img.shields.io/badge/license-Proprietary-0b0b10?style=flat-square" alt="proprietary license">
  <img src="https://img.shields.io/badge/node-%3E%3D22-2fe08a?style=flat-square" alt="node 22 or higher">
  <a href="https://discord.gg/ycy9zkUreX"><img src="https://img.shields.io/badge/discord-join-5865F2?style=flat-square&amp;logo=discord&amp;logoColor=white" alt="join the Z2H Academy Discord"></a>
</p>

<p align="center">
  <a href="#what-it-is">what it is</a> ·
  <a href="#why-tutor">why</a> ·
  <a href="#the-flow">flow</a> ·
  <a href="#content-roadmaps-and-projects">content</a> ·
  <a href="#quick-start">quick start</a> ·
  <a href="#what-your-agent-can-do">capabilities</a> ·
  <a href="#execution-modes">modes</a> ·
  <a href="#troubleshooting">troubleshooting</a>
</p>

**TUTOR** connects your terminal agent —**OpenCode, Codex or Claude Code**— to the Roadmaps, Developer Docs and Labs of Z2H Academy. You build in your own environment. The harness directs and validates.

---

## What it is

Tutor is not a chatbot. It is the harness that connects the agent to Z2H Academy.

An AI agent knows how to run commands and solve problems, but it does not know the teaching structure of the academy. **Tutor is the piece that connects both.**

> The agent executes.
> Tutor connects and orchestrates.
> The harness directs and validates.
> The Developer Docs hold the knowledge.

The agent can change —OpenCode, Codex or Claude Code— without the learning logic depending on a specific model.

Tutor is not a chatbot either, and it is not the AI agent itself. **The agent is what talks to you, reasons and acts on your machine.**

A second thing Tutor is not: a place where the model grades you. **The academy validates each step.** The agent does not decide whether you did it right.

## Why Tutor

The traditional model optimizes consumption: videos, guided exercises, certificates. Tutor trains the technical judgment you need to build real systems.

| The traditional model | With Tutor |
|---|---|
| Recorded videos, identical for everyone. | Living Developer Docs, like real technical documentation. |
| Labs you copy without understanding. | Labs you run in your own environment, with your agent. |
| Nobody checks whether you actually did it. | The academy validates every step: the agent does not decide if it is right. |
| Progress is lost between sessions. | Your agent remembers where you left off. |
| You finish with a certificate. | You finish with something you can show. |

## The flow

`Roadmap → Theory → Plan → Mode → Lab → Evidence`

| Step | What happens |
|---|---|
| **1. Discover** | The agent lists the roadmaps, levels and sections available for your account. |
| **2. Understand** | It presents the theoretical base of the level and a checkpoint to confirm you understood it. |
| **3. Plan** | It builds the plan for the level: each step with its rationale, the command, the expected output and the closing evidence. |
| **4. Choose a mode** | It asks whether you prefer automatic mode (the agent runs it) or manual mode (you run it). |
| **5. Execute** | It runs the lab in your environment; if something fails, it helps you fix it. |
| **6. Validate** | The academy validates each step with evidence. It is not the agent that decides if it is right. |

The theory step is not optional. You cannot jump straight to the lab: without the theoretical base and a passed checkpoint, no command runs.

## Content: roadmaps and projects

Z2H Academy ships two kinds of content, and TUTOR handles both.

| Content type | Structure | Example |
|---|---|---|
| **Roadmap** | Levels, and sections inside each level | `data-engineering` → `nivel-0` → `1-section` |
| **Project** | A single track made of phases | `analytics-starter` → `fase-0`, `fase-1`, … |

Both are read as complete units, not as loose pages:

* A **level** or a **phase** is taught in three stages: theoretical base, lab plan and execution.
* Each stage closes with evidence before moving on.
* In projects the level is optional: the project itself is the unit.

Roadmaps cover data engineering, AI, DevOps, Python, PySpark and SQL. Projects take you through a full build from first phase to last.

## Who it is for

TUTOR is for **active Z2H Academy students**.

Access is controlled by a whitelist: if your GitHub account email is enabled, you can authenticate and start. If it is not, contact the administrator.

## Requirements

Before installing Tutor you need:

* **Node.js 22 or 24** (recommended: 24 LTS), installed through nvm.
* **A GitHub account** whose email is included in the Z2H Academy whitelist.
* **A terminal agent with MCP support**.
* **Git** (to clone repos and work with codespaces).
* **Docker** (for labs that start services on your machine; if it is missing, the agent guides you through installing it).
* **GitHub CLI (`gh`)** (only for Codespaces labs — see https://cli.github.com).

Supported agents include **OpenCode**, **Codex** and **Claude Code**.

OpenCode is the officially supported client. **Tutor 0.10.x requires OpenCode 2**: if you are still on OpenCode 1, stay on Tutor 0.8.0.

---

## Quick Start

### 1. Install nvm + Node.js (Linux)

If you do not have Node.js yet, install it through nvm:

```bash
# Install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash

# Load nvm in the current session (or restart the terminal)
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"

# Install and use Node.js 24 LTS
nvm install 24
nvm use 24
nvm alias default 24
```

Verify the installation:

```bash
node --version   # should print v24.x.x
npm --version    # should print 10.x or 11.x
```

> **Correct versions:** Node.js **22 or 24** (24 LTS recommended). npm ships with Node.js and is not installed separately. Do not use Node.js 20 or lower — Tutor needs modern JavaScript features.

### 2. Install OpenCode

Install the OpenCode agent with the official installer:

```bash
curl -fsSL https://opencode.ai/install | bash
```

Verify the installation (restart the terminal first if needed):

```bash
opencode --version   # should print 2.x
```

> If the command is not found, add `~/.opencode/bin` to your `PATH` or restart the terminal.

> **Version requirement:** Tutor 0.10.x requires OpenCode 2. If you are still on OpenCode 1, stay on Tutor 0.8.0.

### 3. Install Tutor

Install the Tutor CLI globally from the stable release:

```bash
npm install -g https://github.com/z2h-academy/tutor/releases/latest/download/z2h-academy-tutor.tgz
```

You do not need to configure anything by hand: the next step takes care of it.

To pin a specific version, replace `latest` with the tag:

```bash
npm install -g https://github.com/z2h-academy/tutor/releases/download/v0.10.0/z2h-academy-tutor-0.10.0.tgz
```

> **Pre-release channel.** To test the 0.10.x pre-release, install the rc build directly. Note that its asset can change before it is promoted to stable:
>
> ```bash
> npm install -g https://github.com/z2h-academy/tutor/releases/download/v0.10.2-rc.2/z2h-academy-tutor-0.10.2-rc.2.tgz
> ```

### 4. Authenticate

Authentication happens once:

```bash
tutor login
```

Tutor starts the GitHub login and shows a URL and a verification code:

```
Open this URL in your browser and authorize access:

  https://github.com/login/device

Your verification code: XXXX-XXXX

(expires in 15 min)
```

Open the URL, enter the code and authorize **Z2H Academy** with your GitHub account.

During this process Tutor checks that your email is enabled in the academy whitelist.

Once authorized, Tutor leaves your agent connected and ready to use: the connection to the academy, the TUTOR visual theme and **Tutor Memory**, your memory across sessions.

Local credentials are stored at `~/.config/z2h/tutor.env` with `600` permissions, so only you can read the file.

### 5. Verify the installation

From OpenCode, ask the agent:

```text
tell me which roadmaps I have access to
```

If it returns the roadmaps, levels and sections enabled for your account, the installation is complete.

You can also check that the connection is active:

```bash
opencode mcp list
```

The Tutor connection should appear as connected:

```
●  ✓ tutor  connected
```

### 6. Update to the latest version

Updating takes two steps. First install the new version:

```bash
npm install -g https://github.com/z2h-academy/tutor/releases/latest/download/z2h-academy-tutor.tgz
```

Then apply the configuration to your agent:

```bash
tutor setup
```

Restart OpenCode when you are done.

> Reinstalling the package alone does not update your local configuration: `tutor setup` is the step that brings it up to date. It is idempotent and does not touch your other MCP servers.

---

## Tutor Memory

**Your progress is not lost: it is remembered.**

Tutor includes **Tutor Memory**, the memory of your learning. It comes enabled from installation: no accounts, no extra steps.

* **Your agent remembers.** Where you left off, what you decided and summaries of your previous sessions. You never start from zero.
* **Each project remembers its own.** Memory belongs to your project, not to you as a person: every repo has its own history.
* **It travels with you.** Your progress can travel inside your repository: take it from your PC to your Codespace (or the other way around) and continue where you were.
* **Private by design.** It is stored in your working environment and never mixed with anyone else's. Nothing is sent to the harness.

Ask for it like this:

| What you want | Example phrase |
|---|---|
| Resume where you left off | *"where did we leave off last session?"* |
| Save your progress | *"remember that I finished section 2 of level 0"* |
| Save a decision | *"remember that we decided to use Docker for the labs and why"* |
| Recall something from the past | *"what had we decided about the data model?"* |
| Close with context | *"give me a session summary so I can continue tomorrow"* |
| Move your progress to another machine | *"save my progress in the repo so I can continue from the Codespace"* |

Prefer the terminal? Memory is also managed through the CLI:

```bash
tutor-memory status
tutor-memory save --project my-project --type decision --title "Use Docker" --content "Chosen for the labs."
tutor-memory search --query "data model"
tutor-memory export
tutor-memory import
```

> `init`, `status`, `doctor`, `save`, `search`, `repair`, `export`, `import` and `migrate` are available. `tutor-memory --help` prints the full usage. The database lives on your machine at `~/.local/share/z2h/tutor/memory.db` with `600` permissions, and `<private>…</private>` tags are stripped before anything is stored.

## What your agent can do

Tutor teaches your agent how to work with the academy. It is not a list of commands: it understands where you are and adapts the answer. You can ask in your own words and it discovers the real content before replying.

**Discover your content.** Ask what is available and it shows the roadmaps and projects with their structure live, with no fixed catalog.

```text
list the roadmaps
```

**Understand a project before starting.** It gives you the big picture, what you will learn and how it is organized, without opening any files yourself.

```text
let's build the analytics-starter project.
give me a summary of what I will learn.
```

```text
give me a strategic summary of analytics-starter phase-0
```

**Move forward in order.** If you ask for the next step, it picks up where you left off and tells you what comes next in the roadmap or project.

```text
what comes after phase-0?
```

**Study a complete unit.** A project phase or a roadmap level is taught in three stages: theoretical base, lab plan and execution. You cannot skip the theory to jump straight into the lab.

```text
start analytics-starter phase-1
```

**Run your labs.** In local or in a Codespace, in manual or automatic mode.

```text
run the analytics-starter lab in Codespaces
```

**Validate each step.** Against the academy criteria, not against the model's opinion.

```text
is it right the way I loaded the data?
```

**Go deeper.** On any topic already covered, you can ask for examples, clarifications or a different explanation.

```text
explain the fact table grain again with an example
```

**Diagnose when something fails.** Report the error as it appears and Tutor finds the cause instead of guessing.

```text
I get this error when loading the data: <paste the error>
```

> Tutor works only with the course material and your session state. If something is not in the docs, it tells you instead of making it up.

## Execution modes

The mode is chosen once, inside the plan, and is not changed halfway unless you ask for it.

| Mode | What happens |
|---|---|
| **Manual** | The agent prepares the commands and you run them. It verifies the result with you. |
| **Automatic** | The agent runs the steps one by one and verifies each one. Destructive commands still require explicit confirmation. |
| **Single command** | You insist on one command without the theory. You get the action, a two-line rationale and the expected evidence. The checkpoint stays pending, the unit does not close and it does not count as progress. |

In single-command mode only one lab action is allowed per turn, plus positioning in the workspace and activating an environment the material already declares. Preparation, inspection and verification are not allowed in the same turn.

## Local theory export

From the local MCP you can export the theory of a unit as a document:

```text
export the theory of this unit
```

* One unit at a time; there is no "export everything".
* The renderer is fixed and the output goes through a sanitizer that blocks internal terms.
* Export state is tracked, so an edited export is never overwritten without asking you.

> The export is **local only**. It is not available in the hosted harness, so do not expect it from the web version.

## Two ways to use it

* **Local** — in your terminal: install Tutor, authenticate and open your agent. It works on your PC, in a Codespace or in a container.
* **Web** — in the browser: go to [tutor.z2h-academy.com](https://tutor.z2h-academy.com), sign in with GitHub and use OpenCode with your own cloud environment.

> `tutor runtime` starts the runtime daemon behind the web mode: it boots OpenCode locally and connects it to the academy. You do not normally run it by hand.

---

## Troubleshooting

| Problem | Solution |
|---|---|
| `email not in pre_enrollment whitelist` | Your email is not enabled. Contact the Z2H Academy administrator. |
| `grant user:email scope` | Make sure you authorized the `user:email` scope during the GitHub login. |
| `AccessDenied` when reading content | Your content access expired or was revoked. Run `tutor login` again. |
| After updating, changes are not visible | Run `tutor setup` and restart OpenCode. |
| The login says the command is interactive | Run `tutor login` yourself in your terminal, with the browser at hand. Do not launch it from the agent. |
| A roadmap that should be enabled does not appear | Run `tutor login` again to refresh your access. |
| The Tutor connection does not appear in OpenCode | Check that Tutor is installed, run `tutor setup` and restart OpenCode. |
| `no email available` | GitHub is not providing an email for your account. Check your GitHub email settings. |
| `gh: command not found` | Install GitHub CLI from https://cli.github.com (needed for Codespaces labs). |
| `You are not logged into any GitHub hosts` | Run `gh auth login` and complete the authentication flow. |
| You are on OpenCode 1 | Tutor 0.10.x requires OpenCode 2. Update OpenCode or stay on Tutor 0.8.0. |

---

## Community

**Building is better accompanied.**

The Z2H Academy Discord brings together students from every roadmap:

* **Unblock yourself.** When a lab is stuck or something is unclear, ask in the right channel.
* **Share your progress.** Show what you built, ask for feedback and see what others are building.
* **Hear it first.** New roadmaps, labs and Tutor updates are announced on Discord.

<p align="center">
  <a href="https://discord.gg/ycy9zkUreX"><strong>→ Join the Z2H Academy Discord</strong></a>
</p>

---

## Support

For issues related to access, authentication, Tutor configuration, agent connection, Roadmaps or labs, contact the Z2H Academy administrator.

---

## License

Tutor is intended exclusively for use by active Z2H Academy students.

See the `LICENSE` file included in the project for the full terms of use.

---

<p align="center">
  <sub>The agent executes · Tutor connects and orchestrates · the harness directs and validates</sub>
</p>

<p align="center">
  <a href="https://discord.gg/ycy9zkUreX"><img src="https://cdn.simpleicons.org/discord/5865F2" alt="Discord" width="20" height="20"> Join the community on Discord</a>
</p>
