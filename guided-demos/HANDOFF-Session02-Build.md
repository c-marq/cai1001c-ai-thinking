# HANDOFF — CAI1001C Session 02 File Set Build

Paste this as the first message in a new chat to continue the build with full context.

---

## What I need built

Four cross-linked files for **Session 2** of CAI1001C (Wednesday May 20, 2026 — the NotebookLM class), ready to push to the book repo as four folders. All four are described in detail below. Build all four; cross-link them with absolute URLs.

1. `sessions/session02.md` — the session page (MyST markdown)
2. `guided-demos/gd02.html` — instructor demo guide (standalone HTML)
3. `group-labs/grp02.html` — breakout lab worksheet (standalone HTML, fillable)
4. `homeworks/ng02.html` — optional take-home / NG02 (standalone HTML, fillable)

---

## Course context (everything you need to know)

**Course:** CAI1001C — AI Thinking, Miami Dade College, Summer 2026. 6-week accelerated section, Mon/Wed 6:00–9:20 PM, 11 sessions, term 5/11–6/19/2026. Instructor: Professor Carlos Marquez.

**The textbook** is *Mind the Machine* — a MyST-built book hosted at `https://c-marq.github.io/cai1001c-ai-thinking/`. The whole course revolves around the book. 8 chapters. Each chapter has a featured hands-on tool and ends with five review questions, a discussion question, an instructor-led walkthrough, a breakout-group lab, and an optional take-home that adds ethics/bias.

**Session 2 = Chapter 2: Digital Literacy and Data.** Featured tool: **NotebookLM**. The full Chapter 2 source is attached to this message (`ch02-digital-literacy-data.md`) — read it first; everything must align to the actual chapter content.

**Session structure (two blocks):**
- Block A (~90 min): welcome, lecture, live NotebookLM walkthrough
- Long break (~15 min)
- Block B (~90 min): use-case discussion, then breakout lab

**The instructor's demo plan for tonight:** demo NotebookLM for research; show all Studio features (videos, podcasts/Audio Overview, slides, mind maps); how to prompt the Studio apps; the outputs-to-notes-to-source loop. Then discuss other use cases and ideas, then students go to breakout rooms.

---

## Repo structure (locked)

```
cai1001c-ai-thinking/   (book repo root)
├── ch02-digital-literacy-data        ← chapter, live MyST page
├── sessions/
│   └── session02.md
├── guided-demos/
│   └── gd02.html
├── group-labs/
│   └── grp02.html
└── homeworks/
    └── ng02.html
```

Folder names (lowercase, hyphenated): `sessions`, `guided-demos`, `group-labs`, `homeworks`.
File naming: `session02.md`, `gd02.html`, `grp02.html`, `ng02.html` (no underscores, two-digit numbers).

---

## The four links — use ABSOLUTE URLs only

The session page must contain **exactly four links, nothing else**:

1. Chapter: `https://c-marq.github.io/cai1001c-ai-thinking/ch02-digital-literacy-data/`
2. Guided demo: `https://c-marq.github.io/cai1001c-ai-thinking/guided-demos/gd02.html`
3. Group lab: `https://c-marq.github.io/cai1001c-ai-thinking/group-labs/grp02.html`
4. Homework: `https://c-marq.github.io/cai1001c-ai-thinking/homeworks/ng02.html`

Use absolute URLs everywhere, not relative `../` paths — the repo's nested folders make relative paths fragile. The demo/lab/homework files don't exist yet; building them in this set is why all four links will resolve once pushed.

---

## What each file should be

### `session02.md` — KEEP IT MINIMAL
The previous draft had too many links. The session page is a lightweight hub: session metadata (course, session 2 of 11, Wed May 20, Week 2, Chapter 2), a short "what we're doing today," the two-block table, a "before class" checklist, brief Block A / Block B descriptions, a wrap-up checklist. **Only the four links above** — one to the chapter, one to the guided demo, one to the group lab, one to the homework. No in-chapter section anchors, no extra navigation. MyST markdown; it will be registered in `myst.yml` under a "Course Sessions" group.

### `gd02.html` — instructor guided demo guide
Standalone HTML, instructor-facing reference for the live NotebookLM walkthrough. Follow the format of the earlier GP demo guides: numbered tool/step cards, navy headers, running clock, color-coded boxes (green = do on screen, blue = say, yellow = warning). Content = the NotebookLM walkthrough from Chapter 2 Section 2.6 plus the instructor's demo plan: create notebook, add curated sources, ask questions + click citations, Studio panel (briefing, flashcards, quiz, mind map, Audio Overview, video, slides), how to prompt Studio apps, outputs-to-notes-to-source loop, what NotebookLM won't do. Print-friendly.

### `grp02.html` — group lab worksheet
Standalone HTML, fillable (expandable textareas, screenshot paste-in boxes, print-to-PDF). This is Chapter 2's "Breakout Lab: Build a Grounded Notebook" turned into a worksheet: group members + roles, pick a research question, curate 4–6 sources running each through the chapter's five-question source test, build the NotebookLM notebook, test what it does when asked something outside its sources, share-out prep. Blue theme (group work). Submit-as-PDF instructions. 4 points.

### `ng02.html` — homework / optional take-home
Standalone HTML, fillable, same format family. This is Chapter 2's "Optional Take-Home: Going Deeper": deliberately add one weak source to the notebook, observe what happens to the answers, then a ~300-word reflection on whether grounding made the answer trustworthy, whose judgment was responsible, and how a curated source set could still be biased. Purple theme (individual work). 30 points. Due Sunday.

---

## Style reference (from prior work in this course)

- Color-coded instructional boxes: green `#D5F5E3`/`#27AE60` (action), blue `#D6EAF8`/`#2E86C1` (context), yellow `#FEF9E7`/`#F1C40F` (warning), red `#FADBD8`/`#E74C3C` (checkpoint).
- Worksheets: blue theme for group labs, purple `#6C3483` theme for individual homework.
- Fillable worksheets use expandable `<textarea>` elements with auto-grow JS, `contenteditable` divs for screenshot paste, and a `@media print` block + `beforeprint` handler so nothing clips in the PDF.
- Demo guides: navy `#16213E` headers, orange `#F39C12` accent, numbered cards with a running clock.
- Group lab roles: Lead Driver, Data Interpreter, Presenter, QA Reviewer.
- Worksheets submit via browser File → Print → Save as PDF, uploaded to the matching Canvas assignment.

---

## First steps for the new chat

1. Read the attached `ch02-digital-literacy-data.md` in full.
2. Build all four files, cross-linked with the absolute URLs above.
3. Deliver them ready to drop into the four repo folders.

**Attach `ch02-digital-literacy-data.md` to the first message of the new chat.**
