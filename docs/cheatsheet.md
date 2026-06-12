# Claude skills & plugins — install cheat-sheet

From the lecture **"Level Up: LLM Agents & Claude Desktop"** — Edward Kisller, Ariel University.

Run these inside Claude Code / Claude Desktop:

```
/plugin install skill-creator@claude-plugins-official
/plugin install superpowers@claude-plugins-official
/plugin marketplace add mksglu/context-mode
/plugin install context-mode@context-mode
/plugin marketplace add thedotmack/claude-mem
/plugin install claude-mem
/plugin install frontend-design@claude-plugins-official
```

And this one in your terminal:

```
npx get-shit-done-cc --claude --global
```

Built in, no install needed: `/code-review` — fast local code review; ultra mode spins up a cloud fleet of reviewer agents.

What each one does:

| Tool | One-liner |
|---|---|
| skill-creator | The skill that builds skills — describe a job in plain English, get a reusable skill |
| superpowers | Makes Claude work like a senior engineer: brainstorm → plan → test-first → review |
| get-shit-done (GSD) | Fights context rot: fresh sub-agents per task, quality gates, autonomous mode |
| context-mode | Keeps the current session lean — sandboxes noisy tool output, snapshots survive compaction |
| claude-mem | Memory across sessions — auto-captures work into a local searchable DB |
| frontend-design | Official Anthropic skill — UI output stops looking AI-generated |
