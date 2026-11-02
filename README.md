## Rubber Duck

The classic programmer Rubber Duck, reimagined for AI coding agents.

Rubber Duck gives Claude Code and Codex a structured way to reason through stubborn bugs by explaining the code, tracing its logic, and reviewing how its components interact.

How It Works

When debugging attempts repeatedly fail or make things worse, the agent can ask whether you'd like to consult the Rubber Duck.

If approved, it creates or updates "rubberduckdebug.md", documenting:

- **Bug** — A short summary of the problem.
- **RubberDuck** — An in-depth explanation of the code's logic and what is going wrong.
- **Review** — Findings, potential improvements, and fixes made or planned.

The agent then reviews its reasoning, identifies potential issues, and attempts to fix the underlying problem.

## Philosophy

Sometimes the best way to solve a problem is to explain it out loud.

Even if your Rubber Duck happens to be a `.md` file.

---
