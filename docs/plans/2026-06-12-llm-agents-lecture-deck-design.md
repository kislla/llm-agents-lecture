# LLM Agents Lecture — Slide Deck Design

**Status: APPROVED (2026-06-12).** Companion implementation plan to follow in `docs/plans/`.

- Date: 2026-06-12
- Presenter: Edward Kisller
- Audience: CS BSc undergraduates, Ariel University
- Duration: ~60 minutes including live demo and Q&A
- Language: English
- Presentation tech: self-contained HTML deck (built with the frontend-slides skill), presented from a browser; must work offline

## Decisions so far

| Decision | Choice |
|---|---|
| Structure | "Three-act enhanced" — 21 HTML slides: 17 content + 2 act dividers + 2 hidden fallbacks |
| Project home | `~/WebstormProjects/llm-agents-lecture` (this repo) |
| Visual style | "Edge-lit glass" language derived from Edward's five reference screenshots (see Part 2) — inspiration to remix, explicitly NOT a 1:1 copy. |

## Act I — Foundations (~15 min, slides 1–8)

### 1 · Title
- **Content:** "Level Up: LLM Agents & Claude Desktop" / subtitle "Automating your day-to-day CS workflow with Skills, Plugins, and MCP" / footer: Edward Kisller · Ariel University.
- **Visual:** Dark background, deep-green/cyan radial gradient, animated glowing node-network graphic.

### 2 · About Me
- **Content:** Edward Kisller. Four facts with icons: 👔 Senior Solutions Developer — business automation advocate; 🎓 BSc Mathematics & CS — "right here at Ariel"; 🧗 professional sport climbing instructor; 🌪️ dad of two little Tasmanian devils.
- **Visual:** Headshot in a glowing rounded cyan frame + 2×2 icon card grid.

### 3 · Why You're Here (hook + agenda)
- **Content:** Hook: *"You already use ChatGPT to explain recursion. Today you'll make Claude build tools for you."* Frames the shift from asking questions to delegating work. Agenda: the three acts.
- **Visual:** Three glowing act cards with mini-icons.

### 4 · The LLM Tool Landscape
- **Content:** Three tiers — Web UIs (ChatGPT, Claude, Gemini → chatting); IDE copilots (Copilot, Cursor → autocomplete); Agentic apps (Claude Desktop, Claude Code → files, terminal, browser, plugins). Tagline: "Conversational AI answers. Agentic AI *does*."
- **Visual:** Three-tier card grid; the agentic card glows brightest.

### 5 · Jargon I: Tokens, Context, Sessions
- **Content:** Tokens = sub-word units (~4 chars), the "machine word" of LLMs. Context window = the model's RAM (~200K tokens on modern Claude models). Session = a process: when it exits, its memory is gone (plants the seed for Act III's memory plugins).
- **Visual:** Sentence splitting into glowing token chips; RAM bar filling up.

### 6 · Jargon II: Agents, Sub-agents, MCP
- **Content:** Agent = LLM + tools + a loop (plan → act → observe → repeat). Sub-agents = child processes with fresh, clean context. MCP = "USB-C for AI": one open standard connecting the model to terminal, browser, Jira, anything.
- **Visual:** Circular agent-loop diagram; MCP drawn as a glowing bridge between brain and tool icons.

### 7 · Plugins vs Skills
- **Content:** Skill = a folder with SKILL.md teaching Claude one job, loaded on demand. Plugin = the package that ships skills (+ MCP servers, hooks). CS analogy: *skill = function, plugin = the npm package*. Payoff: "Stop re-typing giant prompts. Invoke expertise."
- **Visual:** Nesting diagram — plugin box containing skill / MCP / hooks chips.

### 8 · The "/" Command Palette
- **Content:** Typing `/` opens the command dropdown. `/plugin marketplace add`, `/plugin install`. Works in Claude Desktop and Claude Code.
- **Visual:** Mockup of the Claude Desktop input with glowing dropdown.

## ⚡ Divider → Act II — Skills, Live (~22 min, slides 9–11 + hidden fallbacks)

### 9 · skill-creator: The Skill That Builds Skills
- **Content:** Describe the job in plain English → Claude drafts, tests, packages it. "The factory that builds the tools." Command: `/plugin install skill-creator@claude-plugins-official`.
- **Visual:** Assembly line stamping out skill cards; terminal-style command card.

### 10 · Anatomy of a Skill
- **Content:** Annotated SKILL.md: frontmatter `name` + `description` (the trigger), instruction body, optional scripts. Key concept: **progressive disclosure** — only the one-line description sits in context until triggered, so installing 50 skills is ~free. Makes the demo legible.
- **Visual:** Annotated code panel with callout lines.

### 11 · 🔴 LIVE DEMO
- **Content:** Near-black slide, huge neon "LIVE DEMO", red pulse dot, one small line with the demo prompt. Full runbook lives in speaker notes (Part 2).
- **Demo:** Build a LinkedIn job-search skill with skill-creator.

### 11a / 11b · Hidden Fallback Slides
- **Content:** Pre-baked screenshots — (a) skill-creator conversation + generated file tree; (b) the skill running with real job results. Jumped to only if the live demo fails.

## ⚡ Divider → Act III — Power-Ups (~13 min, slides 12–17)

### 12 · superpowers
- **Content:** Discipline for Claude: brainstorm → plan → test-first → two-stage review. "Makes Claude work like a senior engineer, not an eager intern." Meta-beat: *this very lecture was planned with it.* Command: `/plugin install superpowers@claude-plugins-official`.
- **Visual:** Pipeline diagram (tests → brainstorm → review → spec match / code quality).

### 13 · GSD (get-shit-done)
- **Content:** Context rot: long sessions degrade. GSD spawns fresh sub-agents per task with clean context + quality gates + autonomous mode. Command: `npx get-shit-done-cc --claude --global`.
- **Visual:** Degrading context bar vs a row of fresh sub-agent bars.

### 14 · Fixing the Amnesia
- **Content:** **claude-mem** — auto-captures each session into a local searchable DB, injects relevant memories into new sessions (`/plugin marketplace add thedotmack/claude-mem` + `/plugin install claude-mem`). **context-mode** — keeps the *current* session lean: sandboxes noisy tool output, session snapshots survive compaction (`/plugin marketplace add mksglu/context-mode` + `/plugin install context-mode@context-mode`).
- **Visual:** Split card: brain + infinity loop.

### 15 · Polish & Safety Nets
- **Content:** **frontend-design** — official skill; UI output stops looking AI-generated; "this deck used its sibling" (`/plugin install frontend-design@claude-plugins-official`). Built-in code review in Claude Code: `/code-review` (fast, local) and ultra mode (cloud fleet of reviewer agents; bugs verified before reported).
- **Visual:** Split card: glowing gear + UI wireframe.

### 16 · 📸 The Cheat-Sheet
- **Content:** "Take a photo of this slide." One terminal-style block with all seven install commands + QR placeholder (target URL TBD).
- **Visual:** Single large terminal card.

### 17 · Closing
- **Content:** "AI augments your fundamentals — it doesn't replace them. The fundamentals are how you check its work." Q&A. Contact placeholders: LinkedIn / GitHub / email.
- **Visual:** Glowing question-mark node network.

## Accuracy corrections baked into the content

- Context window: say "~200K tokens on modern Claude models" — not "Claude 3.5's 200k" (outdated reference from the source video).
- context-mode: it is context-window hygiene (sandboxed tool output + session snapshots) — not "switching between project contexts" as the draft template said.
- Code review commands: current naming is `/code-review` (with an ultra effort mode) rather than `/re` / `/ultrareview`.
- GSD: spelled out once as "get-shit-done" (the actual npm package name).
- Dropped unverifiable claims from the source video (e.g., GitHub star counts).

## Inputs needed from Edward before implementation

1. Headshot photo for slide 2.
2. LinkedIn / GitHub / contact links for slide 17.
3. Optional: target URL for the cheat-sheet QR code (gist/repo with the commands).
4. ✅ Style reference screenshots — provided 2026-06-12, distilled into Part 2 below. Optionally drop the original PNGs into `assets/reference/` for the build session.

## Part 2 — Visual system

### Reference language (from Edward's five screenshots, 2026-06-12)

Remix these traits; do **not** copy layouts 1:1:

1. **Stage:** near-black, slightly green-tinted background with soft teal radial glows and faint elliptical light rings at the edges.
2. **Edge-lit panels:** large rounded-rectangle containers with thin teal borders that brighten toward corners, like back-lit glass — the main frame for diagram slides.
3. **Glass cards:** frosted teal-tinted translucent cards, thin cyan border, subtle top-left light streak; oversized translucent numerals for numbered lists.
4. **Pill badges:** icon + letterspaced all-caps label pills titling each diagram (PLUGIN / SKILL style).
5. **Hex nodes:** hexagons for skills and agents; layered hex shadows behind the "hero" node.
6. **Dashed connectors:** thin white/teal dashed lines between nodes.
7. **Window chrome:** macOS traffic-light window frames for terminal cards and app mockups.
8. **Glow titles:** big, letterspaced, soft-glow headlines for dividers and the LIVE DEMO slide.

### Working palette (frontend-slides exploration may refine)

- Background base `#05090A` family; glow layers: teal radial gradients at 4–8% opacity.
- Accent ramp: `#5EEAD4` (bright cyan) · `#2DD4BF` (primary teal) · `#0D9488` (deep teal).
- Text: `#E8F4F2` primary; desaturated teal-gray secondary.
- Semantic red reserved for the LIVE pulse dot.
- Type: geometric sans for headlines (wide letterspacing), monospace for all commands.

### Slide-to-visual homage map

| Slide | Visual | Remixes |
|---|---|---|
| 7 Plugins vs Skills | PLUGIN pill → container holding skill hexes + hooks + MCP server folders | Screenshot 2 |
| 10 Anatomy of a skill | SKILL pill → markdown file → Claude capabilities panel | Screenshot 5 |
| 12 superpowers | tests → brainstorm → review → spec match / code quality pipeline in a window frame | Screenshot 4 |
| 15 Code review (ultra) | your branch → Claude sandbox → four reviewer hexes: logic, security, performance, edge cases | Screenshot 3 |
| 16 Cheat-sheet | numbered glass rows with oversized translucent numerals | Screenshot 1 |

All other slides reuse the same component kit (glass cards, edge-lit panels, hex nodes, dashed connectors, window chrome).

### Legibility constraints (override prettiness)

Body text ≥28px equivalent; ≤5 bullets per slide; high contrast; glow stays subtle — must survive a washed-out 1080p projector.

## Part 2 — Live demo runbook (speaker notes for slide 11)

**Before the lecture**
- Rehearse once end-to-end with a timer.
- Bump Claude Desktop font size; enable Do Not Disturb; close personal windows.
- A `linkedin-job-scraper` skill already exists in Edward's environment (earlier experiment). Decision: keep it installed as the live fallback; phrase the demo prompt so skill-creator builds a fresh, differently-named skill.

**The demo (~10–12 min, hard stop)**
1. Invoke skill-creator.
2. Prompt: *"Create a skill that searches for open software engineering positions on LinkedIn."*
3. Narrate skill-creator's clarifying questions as they appear.
4. Show the generated folder + SKILL.md — callback to slide 10's anatomy.
5. Run the new skill once.

**Failure playbook**
- LinkedIn/wifi misbehaves → the lesson is the *skill creation*: show the generated SKILL.md, skip the run.
- Build stalls → run the pre-existing `linkedin-job-scraper` skill instead.
- Claude Desktop down → hidden slides 11a/11b tell the story in screenshots.

## Part 2 — Implementation & verification

- **Repo:** `~/WebstormProjects/llm-agents-lecture` — git-initialized; `docs/plans/` (design + implementation plan), `assets/` (headshot, fallback screenshots, optional reference stills), deck at repo root.
- **Build:** via the frontend-slides skill — animated HTML deck with keyboard navigation.
- **Offline-first:** final deck fully self-contained (fonts/CSS/JS inlined or local). Venue wifi is trusted only for the live demo, never for the slides.
- **Speaker notes:** `docs/speaker-notes.md` — per-slide talking points + the demo runbook, printable.
- **Hidden slides:** 11a/11b sit outside the normal arrow-key flow, reachable only by a deliberate jump, so an accidental forward-arrow never reveals them.
- **Verification before presenting:** open the deck with wifi off and walk all 21 slides; legibility check from ~3 m; one timed demo rehearsal.
