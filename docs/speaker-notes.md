# Speaker Notes — LLM Agents & Claude Desktop

**Presenter:** Edward Kisller · Ariel University · ~60 min including live demo + Q&A

---

## Slide 1 — Title

- "Level Up: LLM Agents & Claude Desktop" — set the energy, this is hands-on, not theory.
- Subtitle: automating day-to-day CS workflow with Skills, Plugins, and MCP.
- Quick housekeeping: 60 minutes, live demo in the middle, save questions or drop them as we go.

→ Let's start with who's talking to you for the next hour.

---

## Slide 2 — About Me

- Edward Kisller — Senior Solutions Developer, business automation advocate.
- BSc Mathematics & CS — right here at Ariel.
- Also: professional sport climbing instructor, and dad of two little Tasmanian devils.
- Point: this is practical stuff I use daily, not academic theory.

→ So why are you here today? Let's frame the shift we're making.

---

## Slide 3 — Why You're Here (hook + agenda)

- Hook: "You already use ChatGPT to explain recursion. Today you'll make Claude build tools for you."
- The shift: from asking questions → to delegating work.
- Agenda = three acts: Foundations, Skills Live, Power-Ups.
- By the end you'll have built and run a real skill yourself (well — watched me build one live).

→ Before we go agentic, let's map the landscape of LLM tools you already half-know.

---

## Slide 4 — The LLM Tool Landscape

- Three tiers: Web UIs (ChatGPT, Claude, Gemini — chatting); IDE copilots (Copilot, Cursor — autocomplete); Agentic apps (Claude Desktop, Claude Code — files, terminal, browser, plugins).
- Each tier does more than the last — agentic apps act in your environment, not just respond.
- Tagline: "Conversational AI answers. Agentic AI *does*."

→ To talk about agentic apps properly we need shared vocabulary — let's get the jargon out of the way.

---

## Slide 5 — The Wider Landscape (tool catalog)

- The wider ecosystem beyond chat — five flavors: chats, media generators, vibe-coding app builders, automation platforms, coding agents.
- Land the ones they may not know yet: Lovable & Base44 (prompt → a working web app), n8n (wire tools into workflows), Antigravity & Claude Code (agents that work in your codebase).
- Throughline: same pattern everywhere — you describe the outcome, the model does the work. Slide 4 was the *concept* (chat → delegate); this is the *catalog*.

→ You've seen the tools — now let's get the vocabulary straight: tokens, context, sessions.

---

## Slide 6 — Jargon I: Tokens, Context, Sessions

- Tokens = sub-word units (~4 chars) — the "machine word" of LLMs.
- Context window = the model's RAM — ~200K tokens on modern Claude models.
- Session = a process: when it exits, its memory is gone.
- Plant the seed: that "amnesia" is exactly what Act III's memory plugins fix.

→ Round two of jargon — agents, sub-agents, and the protocol that ties everything together.

---

## Slide 7 — Jargon II: Agents, Sub-agents, MCP

- Agent = LLM + tools + a loop: plan → act → observe → repeat.
- Sub-agents = child processes spawned with fresh, clean context.
- MCP = one open standard connecting the model to terminal, browser, Telegram, anything — think "USB-C for AI".
- This is the plumbing that makes everything in Act II and III possible.

→ With agents and MCP defined, here's how Claude actually packages capabilities — plugins and skills.

---

## Slide 8 — Plugins vs Skills

- Skill = a folder with SKILL.md teaching Claude one job, loaded on demand.
- Plugin = the package that ships skills (+ MCP servers, hooks).
- CS analogy: skill = function, plugin = the npm package.
- Payoff: stop re-typing giant prompts — invoke expertise instead.

→ So how do you actually install and invoke these things? One keystroke.

---

## Slide 9 — The "/" Command Palette

- Typing `/` opens the command dropdown — your gateway to everything.
- Two commands to remember: `/plugin marketplace add` and `/plugin install`.
- Works the same in Claude Desktop and Claude Code.
- This is the on-ramp for every install command you'll see for the rest of the talk.

→ Foundations done — time to switch gears into Act II: skills, live.

---

## Slide — Divider A (Act II)

- We're moving from "what is this stuff" to "watch me build something real."
- Act II is ~22 minutes, anchored by one live demo.
- Set expectations: a skill that builds skills, then we look under the hood, then we run it live.

→ First up — the meta tool: a skill that builds other skills.

---

## Slide 10 — skill-creator: The Skill That Builds Skills

- Describe the job in plain English → Claude drafts, tests, and packages it.
- "The factory that builds the tools."
- Install command: `/plugin install skill-creator@claude-plugins-official`.
- This is the tool we'll use in the live demo in a few minutes.

→ Before we run it live, let's open up a skill and see what's actually inside.

---

## Slide 11 — Anatomy of a Skill

- Annotated SKILL.md: frontmatter `name` + `description` (the trigger) — that's what Claude scans.
- Then the instruction body, plus optional scripts.
- Key concept: progressive disclosure — only the one-line description sits in context until triggered.
- Consequence: installing 50 skills is essentially free on context budget. This makes the live demo legible.

→ Now let's see skill-creator build one of these from scratch — live.

---

## Slide 12 — LIVE DEMO

**[Full runbook below — read before presenting]**

**Before the lecture**
- Rehearse once end-to-end with a timer.
- Bump Claude Desktop font size; enable Do Not Disturb; close personal windows.
- A `linkedin-job-scraper` skill already exists in Edward's environment (earlier experiment). Decision: keep it installed as the live fallback; phrase the demo prompt so skill-creator builds a fresh, differently-named skill.

**The demos (~12–15 min, hard stop) — two quick ones**

*Demo 1 — a skill (skill-creator):*
1. Invoke skill-creator.
2. Prompt: *"Create a skill that searches for open software engineering positions on LinkedIn."*
3. Narrate the clarifying questions; show the generated folder + SKILL.md — callback to slide 11's anatomy; run the new skill once.

*Demo 2 — software, one-shot (coding agent):*
4. Fresh prompt: *"Create a software coding example."* (give Claude a concrete task live — e.g. a small web app, a script, or an algorithm visualizer.)
5. Let Claude write it in one go, then run or show the result. This is the "Claude writes real, working software" beat — a different muscle from Demo 1's skill-building.

**Failure playbook**
- Demo 1 — LinkedIn/wifi misbehaves → the lesson is the *skill creation*: show the generated SKILL.md, skip the run. Build stalls → run the pre-existing `linkedin-job-scraper` skill instead. Claude Desktop down → hidden slides 12a/12b tell the story in screenshots.
- Demo 2 — if it misbehaves → just show the generated code (the point is Claude produced working software), or fall back to a pre-made version.

→ If everything went well — that's a skill *and* a working app, built live. If it didn't, here's the same story in pictures (jump to 12a/12b only on failure).

---

## Slide 12a — Hidden Fallback (skill-creator conversation)

- Navigation: press **B** on the LIVE DEMO slide to jump here. Arrows move between 12a/12b; **B** or **Esc** returns to slide 12. Normal arrow flow never shows these.
- Pre-baked screenshots of the skill-creator conversation + the generated file tree.
- Use only if the live demo fails before the run step.
- Walk through it exactly as if it just happened live — same callback to slide 11's anatomy.

→ And here's what it looks like once that skill actually runs.

---

## Slide 12b — Hidden Fallback (skill running)

- Pre-baked screenshots of the skill running with real job results.
- Use only if the live demo failed at or after the run step.
- Land the same punchline as a successful live run: this is what "the factory built a tool" looks like in practice.

→ Demo done (live or fallback) — Act III is about leveling up further with community power-ups.

---

## Slide — Divider B (Act III)

- Transition from "here's the platform" to "here's how to make it work *for you*, daily."
- Act III is ~13 minutes, five power-ups, then the cheat-sheet and close.
- Frame: these are the plugins Edward actually runs.

→ First power-up: discipline for Claude itself — superpowers.

---

## Slide 13 — superpowers

- Discipline for Claude: brainstorm → plan → test-first → two-stage review.
- "Makes Claude work like a senior engineer, not an eager intern."
- Meta-beat: this very lecture was planned with it.
- Install: `/plugin install superpowers@claude-plugins-official`.

→ Discipline helps one session — but what happens when sessions get *long*? That's GSD.

---

## Slide 14 — GSD (get-shit-done)

- Context rot: long sessions degrade — as the chat history grows, the model's focus dilutes.
- GSD spawns fresh sub-agents per task, each with clean context.
- Adds quality gates and an autonomous mode on top.
- Install: `npx get-shit-done-cc --claude --global`.

→ Fresh context per task is great — but what about memory *across* sessions? That's the amnesia problem from slide 6.

---

## Slide 15 — Fixing the Amnesia

- **claude-mem**: auto-captures each session into a local searchable DB, injects relevant memories into new sessions.
  - `/plugin marketplace add thedotmack/claude-mem` + `/plugin install claude-mem`.
- **context-mode**: keeps the *current* session lean — sandboxes noisy tool output, session snapshots survive compaction.
  - `/plugin marketplace add mksglu/context-mode` + `/plugin install context-mode@context-mode`.
- Important distinction: context-mode is about context-window *hygiene*, not about switching between project contexts.
- Pacing: ~90 sec here — land the distinction (memory across sessions vs context hygiene now) before moving on.

→ Memory and hygiene sorted — last two power-ups are about polish and safety.

---

## Slide 16 — Polish & Safety Nets

- **frontend-design**: official skill, stops UI output looking AI-generated — "this deck used its sibling."
  - `/plugin install frontend-design@claude-plugins-official`.
- Built-in code review in Claude Code: `/code-review` — fast, local.
- Ultra mode: cloud fleet of reviewer agents, bugs verified before they're reported.

→ Seven plugins, seven commands — let's put them all in one place you can photograph.

---

## Slide 17 — The Cheat-Sheet

- "Take a photo of this slide" — say it explicitly, pause for phones.
- One terminal-style block with all seven install commands from today.
- QR code placeholder for the same list online (if no QR URL was provided, just show the terminal block — the commands are the payoff).
- This is the slide people actually act on after the talk — give it a beat.

→ Last slide — let's zoom out to the one idea I want you to leave with.

---

## Slide 18 — Closing

- "AI augments your fundamentals — it doesn't replace them."
- The fundamentals are how you check its work.
- Open the floor: Q&A.
- Contact info on screen — LinkedIn / GitHub / email — for follow-up questions.

→ (End of deck — open Q&A.)
