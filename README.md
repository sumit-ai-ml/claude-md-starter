# claude-md-starter

> An opinionated Claude Code setup, distributed as a reusable `CLAUDE.md`.

This repo is not an application. It is a single file worth copying: **`CLAUDE.md`**, a layered set of behavioral rules that make Claude Code plan before it codes, keep changes small, verify against a real definition of "done", and run autonomously only when the work is programmatically checkable. There is no build step and no runtime dependencies. It stands on two excellent open-source projects and adds project-specific harness and autonomy rules on top.

## What's inside CLAUDE.md

`CLAUDE.md` lives at the repo root, so Claude Code reads it automatically when you start a session here. It is organized in layers, and each layer has a clear origin:

| Section | What it does | Origin |
| --- | --- | --- |
| 1. Think Before Coding | Surface assumptions, ask, do not silently pick | andrej-karpathy-skills |
| 2. Simplicity First | Minimum code, no speculative abstractions | andrej-karpathy-skills |
| 3. Surgical Changes | Touch only what the task requires | andrej-karpathy-skills |
| 4. Goal-Driven Execution | Turn tasks into verifiable goals | andrej-karpathy-skills |
| 5. Harness | The exact commands that define "done" | this repo (concept: harness engineering) |
| 6. Loops & Autonomy | When and how to run `/goal`, `/loop`, `/batch` | this repo (concept: Ralph loop) |
| Text | House style for human-readable output | this repo |
| gstack skills | Role-based slash commands (`/office-hours`, `/ship`, `/review`, ...) | gstack |

Sections 1 to 4 are based on the four principles from **andrej-karpathy-skills**, themselves derived from Andrej Karpathy's public observations on where LLMs go wrong when coding. The slash commands come from **gstack**. Sections 5, 6, and Text are original to this repo, though Harness and Loops & Autonomy build on the harness-engineering and Ralph-loop ideas credited below.

## Requirements

- [Claude Code](https://github.com/anthropics/claude-code), Anthropic's CLI coding agent
- git

## Quick start

Three steps. The first two set it up; the third makes it yours.

**Step 1: Install gstack.** Open Claude Code and paste `install gstack`. That gives you the workflow slash commands (`/office-hours`, `/ship`, `/review`, and the rest). For the exact install command, see the [gstack repo](https://github.com/garrytan/gstack).

**Step 2: Add the CLAUDE.md.** Copy the `CLAUDE.md` from this repo into your project's root folder. Claude Code reads it automatically when you start a session there.

**Step 3: Make it yours.** Edit two sections in that `CLAUDE.md`:

- **Project**: what you are working on, how to run it, where things live.
- **5. Harness**: what you want Claude Code to follow strictly, such as your test, lint, and build commands (or "renders in a browser and the HTML is valid" if there is no tooling yet).

Sections 1 to 4 (the Karpathy principles) and Section 6 (Loops & Autonomy) work as-is, with nothing to configure.

## Using it

- Day to day, just code. The principles steer Claude toward small, verified changes and away from silent assumptions.
- For mechanical, programmatically verifiable work, prefer the built-in autonomy commands over typing "continue": `/goal <end state>`, `/loop <interval, or until: condition>`, and `/batch <one change across many files>`. See Section 6 for the rules.
- For the role-based workflow (product interrogation, plan review, code review, shipping, QA), use the gstack slash commands. A good first move on any new idea is `/office-hours`.

## Credits

This project is a remix and would not exist without the work below.

**Embedded or required**

- **andrej-karpathy-skills** by multica-ai ([repo](https://github.com/multica-ai/andrej-karpathy-skills)) for the four-principle CLAUDE.md that Sections 1 to 4 are based on. Derived from **Andrej Karpathy** ([@karpathy](https://github.com/karpathy)) and his observations on LLM coding pitfalls.
- **gstack** by **Garry Tan** ([@garrytan](https://github.com/garrytan), [repo](https://github.com/garrytan/gstack)) for the role-based workflow slash commands.

**Concepts behind the custom sections**

- **Section 5, Harness** draws on *harness engineering*: the early-2026 framing that an agent is the model plus everything around it (Agent = Model + Harness), made reliable through deterministic checks and feedback loops rather than prompts. Attribution is contested. **Mitchell Hashimoto** is most often credited with naming and popularizing it, and **Viv Trivedy** ("Anatomy of an Agent Harness") with coining it and the Model + Harness formula. The underlying test-harness idea is older.
- **Section 6, Loops & Autonomy** draws on the *Ralph Wiggum loop* by **Geoffrey Huntley** (mid-2025): a loop that re-runs an agent until it meets your exit conditions, with progress living in git rather than the context window. The general definition of an agent as something that "runs tools in a loop to achieve a goal" is **Simon Willison's**.

Please respect the licenses of the embedded or required projects when redistributing.

## License

The custom sections (Harness, Loops & Autonomy, Text, Project) are original to this repo and released under the [MIT License](LICENSE). The embedded principles and the referenced gstack commands belong to their respective authors above; check their licenses before relicensing any copied portions.

---

Built by Sumit Pandey ([@sumit-ai-ml](https://github.com/sumit-ai-ml)).
