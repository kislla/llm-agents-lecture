# LLM Agents Lecture Deck Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Build the offline-ready, 21-slide animated HTML deck for Edward's 60-minute "LLM Agents & Claude Desktop" lecture, plus printable speaker notes.

**Architecture:** Single self-contained `index.html` at the repo root (all CSS/JS/fonts inlined or vendored under `assets/`), generated with the frontend-slides skill following the approved design. Content lands act-by-act with a commit and render-check after each act. Speaker notes live in `docs/speaker-notes.md`.

**Tech Stack:** Plain HTML/CSS/JS (no build step), frontend-slides skill for generation, git.

**Source of truth:** `docs/plans/2026-06-12-llm-agents-lecture-deck-design.md` (approved 2026-06-12) — per-slide content, visual system, demo runbook. If this plan and the design disagree, the design wins.

**Note for executor:** Tasks 4–7 invoke the frontend-slides skill and need Edward's eyes for aesthetic approval — run them in the main session, not in a fire-and-forget subagent. Tasks 1–3 and 8–9 are mechanical.

---

### Task 1: Repo scaffolding

**Files:**
- Create: `README.md`
- Create: `.gitignore`
- Create: `assets/reference/.gitkeep`, `assets/fallback/.gitkeep`

**Step 1: Create the structure**

```bash
cd /Users/ekisller/WebstormProjects/llm-agents-lecture
mkdir -p assets/reference assets/fallback
touch assets/reference/.gitkeep assets/fallback/.gitkeep
```

**Step 2: Write `README.md`**

```markdown
# LLM Agents & Claude Desktop — lecture deck

60-minute lecture for CS BSc undergrads, Ariel University. Presenter: Edward Kisller.

- Deck: `index.html` — open in a browser, press F for fullscreen, arrows to navigate.
- Design: `docs/plans/2026-06-12-llm-agents-lecture-deck-design.md`
- Speaker notes + demo runbook: `docs/speaker-notes.md`

## Before presenting (Edward's checklist)
- [ ] Add headshot to `assets/headshot.jpg` (slide 2)
- [ ] Fill contact links on slide 17
- [ ] Rehearse the demo once; screenshot the build + the result into `assets/fallback/` and swap into hidden slides 11a/11b
- [ ] Walk the whole deck with wifi OFF
```

**Step 3: Write `.gitignore`**

```
.DS_Store
.idea/
```

**Step 4: Commit**

```bash
git add -A && git commit -m "chore: scaffold repo (assets, README, gitignore)"
```

Expected: clean `git status` afterwards.

---

### Task 2: Speaker notes

**Files:**
- Create: `docs/speaker-notes.md`

**Step 1: Write the skeleton**

One `## Slide N — <title>` section per slide (1–8, divider A, 9–11, 11a, 11b, divider B, 12–17). Under each: 2–4 talking-point bullets distilled from the matching slide section in the design doc (Part 1), plus a "transition line" into the next slide.

**Step 2: Paste the demo runbook**

Copy the design doc's "Part 2 — Live demo runbook" section verbatim into the `## Slide 11` section (before-lecture checklist, 5 demo steps, failure playbook).

**Step 3: Verify completeness**

```bash
grep -c '^## Slide' docs/speaker-notes.md
```

Expected: `21`.

**Step 4: Commit**

```bash
git add docs/speaker-notes.md && git commit -m "docs: speaker notes with demo runbook"
```

---

### Task 3: Presenter inputs (non-blocking)

**Step 1: Ask Edward for the three inputs**

1. Headshot image → save as `assets/headshot.jpg`
2. LinkedIn / GitHub / email for slide 17
3. Optional QR target URL for slide 16

**Step 2: Handle what's missing**

Build with styled placeholders for anything not provided and keep the README checklist items unchecked. Do not block the build on these.

**Step 3: If the QR URL was provided, generate the code locally**

```bash
npx --yes qrcode "<URL>" -o assets/qr.png
```

Expected: `assets/qr.png` exists (offline asset, no live QR service).

**Step 4: Commit** (only if any asset landed)

```bash
git add assets && git commit -m "assets: presenter inputs"
```

---

### Task 4: Aesthetic lock via frontend-slides

**Files:**
- Create: `index.html` (first version: title slide + one diagram slide only)

**Step 1: Invoke the frontend-slides skill** (`frontend-slides:frontend-slides`)

Feed it: the design doc's "Part 2 — Visual system" (palette, eight reference traits, legibility constraints) and ask Edward to re-paste his five reference screenshots if the skill's exploration step wants them. Remix, never copy 1:1.

**Step 2: Produce a two-slide probe**

Slide 1 (title) + slide 9 (skill-creator, includes a terminal card) — these two exercise most of the component kit: glow title, edge-lit panel, glass card, pill badge, window chrome, monospace commands.

**Step 3: Get Edward's approval on the probe**

Open `index.html` in the browser; iterate until Edward approves the look. This gate prevents restyling 21 finished slides later.

**Step 4: Commit**

```bash
git add index.html && git commit -m "feat: visual system locked via two-slide probe"
```

---

### Task 5: Build Act I (slides 1–8)

**Files:**
- Modify: `index.html`

**Step 1: Build slides 1–8** per design doc Part 1 (Act I sections). Slide 2 uses `assets/headshot.jpg` or its placeholder.

**Step 2: Render check**

```bash
open /Users/ekisller/WebstormProjects/llm-agents-lecture/index.html
```

Checklist against the design doc: every slide title matches; ≤5 bullets per slide; body text ≥28px; arrows navigate 1→8 in order.

**Step 3: Commit**

```bash
git add -A && git commit -m "feat: act I foundation slides (1-8)"
```

---

### Task 6: Build Act II (divider, 9–11, hidden 11a/11b)

**Files:**
- Modify: `index.html`

**Step 1: Build** divider A, slides 9–11, and hidden slides 11a/11b (placeholder frames captioned for the fallback screenshots).

**Step 2: Implement hidden-slide navigation**

11a/11b must be skipped by normal arrow flow and reachable only by a deliberate jump (e.g. pressing `B` on slide 11). Slide 12 follows slide 11 on arrow-right.

**Step 3: Verify navigation**

Arrow-walk the whole deck: 11 → divider B with no fallback slides shown. Then press the jump key on slide 11: 11a/11b appear, and a key returns to 11.

**Step 4: Commit**

```bash
git add -A && git commit -m "feat: act II skills slides with hidden demo fallbacks"
```

---

### Task 7: Build Act III (divider, 12–17)

**Files:**
- Modify: `index.html`

**Step 1: Build** divider B and slides 12–17 per design doc Part 1, using the homage map from Part 2 (superpowers pipeline, reviewer hexes, numbered cheat-sheet rows).

**Step 2: Verify the cheat-sheet verbatim**

Slide 16 must contain exactly these seven commands, copy-paste-safe:

```
/plugin install skill-creator@claude-plugins-official
/plugin install superpowers@claude-plugins-official
npx get-shit-done-cc --claude --global
/plugin marketplace add mksglu/context-mode
/plugin install context-mode@context-mode
/plugin marketplace add thedotmack/claude-mem
/plugin install claude-mem
/plugin install frontend-design@claude-plugins-official
```

(Eight lines — the two memory plugins each need their marketplace line.)

**Step 3: Render check** — full walkthrough, all 21 slides reachable, act dividers land before slides 9 and 12.

**Step 4: Commit**

```bash
git add -A && git commit -m "feat: act III power-up slides and cheat-sheet"
```

---

### Task 8: Offline self-containment

**Files:**
- Modify: `index.html`; Create: `assets/fonts/*` (if fonts are remote)

**Step 1: Inventory external references**

```bash
grep -nE '(src|href)="https?://|url\(.?https?://' index.html
```

**Step 2: Vendor everything that loads a resource**

Fonts → download into `assets/fonts/` + local `@font-face`; CSS/JS libs → inline into `index.html`. Outbound anchor links (contact links on slide 17) may stay.

**Step 3: Re-run the grep**

Expected: only `<a href="https://...">` matches remain — zero `<script src>`, `<link href>`, `<img src>`, or `url()` pointing at the network.

**Step 4: The real test**

Turn wifi off. Open `index.html`. Walk all 21 slides — identical rendering, fonts included.

**Step 5: Commit**

```bash
git add -A && git commit -m "feat: fully self-contained offline deck"
```

---

### Task 9: Final verification and tag

**Step 1: Full pass against the design doc** — slide count (21), per-slide content matches Part 1, accuracy corrections present (modern context-window phrasing, correct context-mode description, `/code-review` naming).

**Step 2: Update speaker notes** with any slide numbering or jump-key details that changed during the build.

**Step 3: Tag**

```bash
git add -A && git commit -m "docs: final speaker notes" && git tag v1.0
```

**Step 4: Hand Edward the README checklist** — headshot/contacts if still placeholders, fallback screenshots after rehearsal, and the wifi-off walkthrough before the lecture.
