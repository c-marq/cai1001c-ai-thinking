# HANDOFF — Finish the *Mind the Machine* Textbook

**Paste this whole document as the first message of a new chat to finish the book with full consistency.** Then say: *"Read this handoff, then read `constraints.md`, `chapters/ch01-age-of-ai.md`, and `chapters/ch07-generative-media.md` in full before writing anything."*

---

## 1. What this project is

*Mind the Machine* is the textbook for **CAI1001C — AI Thinking**, Miami Dade College, by **Professor Carlos Marquez**. It is a ground-up rebuild of an older 15-chapter book into a new **8-chapter** book — one chapter per concept, each featuring a current AI tool, built around the professor's loop: **demystify the hype → show how the tech works → apply it → analyze the process.**

- **Repo:** `https://github.com/c-marq/cai1001c-ai-thinking` · **Live site:** `https://c-marq.github.io/cai1001c-ai-thinking/`
- **Local working copy:** `C:\Users\cmarq\Downloads\BookBuilder\books\cai1001c-ai-thinking`
- **Built with:** MyST Markdown (the `book-writer` skill at `C:\Users\cmarq\.claude\skills\book-writer`).
- **The governing spec is `constraints.md` in the repo root. Read it first — it is authoritative.**

## 2. Current state — done vs. remaining

**DONE — written, committed, deployed, live (chapters 1–7):**

| Ch | File | Featured tool |
|----|------|---------------|
| 1 | `chapters/ch01-age-of-ai.md` | Gemini |
| 2 | `chapters/ch02-digital-literacy-data.md` | NotebookLM |
| 3 | `chapters/ch03-working-with-data.md` | Datawrapper (+ AI Studio demo) |
| 4 | `chapters/ch04-machine-learning.md` | Teachable Machine + TF Playground (+ Colab lab) |
| 5 | `chapters/ch05-computer-vision.md` | Hugging Face Spaces (+ Nano Banana demo) |
| 6 | `chapters/ch06-language-conversation.md` | Gemini Gems (+ Colab lab) |
| 7 | `chapters/ch07-generative-media.md` | Hugging Face Spaces (Veo named as paid example) |

Also done: book cover, `myst.yml` with full ToC, two Colab notebooks (`notebooks/ch04-train-a-classifier.ipynb`, `notebooks/ch06-build-a-chatbot.ipynb`).

**REMAINING — all currently exist as one-paragraph STUB pages:**

1. **`chapters/ch08-ai-real-world.md`** — Chapter 8, the final chapter. (Spec in §8 below.)
2. **`front-matter/dedication.md`, `foreword.md`, `how-to-use.md`** — front matter.
3. **`addenda/addendum-a-course-map.md`** through **`addendum-e-tool-reference.md`** — Addenda A–E.
4. **`index.md`** — currently has the cover + a minimal welcome; needs a full landing-page polish.
5. The **capstone rubric** — the professor will upload last semester's rubric + project description to revise.

All remaining files are already registered in `myst.yml`'s ToC — you replace stub content, you do not add ToC entries.

## 3. First steps for the new chat

1. Read `constraints.md` (repo root) — the authoritative spec.
2. Read `chapters/ch01-age-of-ai.md` and `chapters/ch07-generative-media.md` in full — absorb the exact voice, structure, and formatting. **Match them precisely.**
3. Confirm the local preview still works (§5) and skim two or three live chapters.
4. Build Chapter 8 (§8), then the front matter and addenda (§9), then polish `index.md` (§9).

## 4. The environment and tools

- **OS:** Windows. Shell for scripts: Git Bash via the Bash tool. Working directory: `C:\Users\cmarq\Downloads\BookBuilder` (the *workspace root*, the parent of `books/`).
- **`book-writer` skill scripts** (`C:\Users\cmarq\.claude\skills\book-writer\scripts\`):
  - `generate-image.js` — image generation (Nano Banana Pro via OpenRouter; key is in the skill's `.env`).
  - `validate-chapter.js` — pre-commit validation.
- **No `gh` CLI and no GitHub token in the environment.** Git pushes and GitHub API calls use the Windows Git Credential Manager's cached token — see §6.

## 5. Operational playbook

### Generating a figure
Run from the **workspace root** (`C:\Users\cmarq\Downloads\BookBuilder`). The Bash working directory can drift if you `cd` — always reset it or use this exact form:
```
cd /c/Users/cmarq/Downloads/BookBuilder && node "C:/Users/cmarq/.claude/skills/book-writer/scripts/generate-image.js" "books/cai1001c-ai-thinking/images/ch08/fig-8-1-slug.png" "$(cat .fig-prompt.txt)" --aspect-ratio landscape --reference "books/cai1001c-ai-thinking/images/ch01/fig-1-1-age-of-ai.png"
```
Write each long prompt to a temp `.txt` file at the workspace root first (avoids shell-quoting problems), then `cat` it in. The script prints JSON with `"success": true`. **Then VIEW the generated PNG with the Read tool and proofread it** — correct spelling, no garbled text, no content copied from the reference image, on-palette. Regenerate any figure that fails. The professor is meticulous about figures.

### Validating a chapter
```
node "C:/Users/cmarq/.claude/skills/book-writer/scripts/validate-chapter.js" "books/cai1001c-ai-thinking" "chapters/ch08-ai-real-world.md"
```
Require `"errors": 0`. The word-count warning ("target: 12,000+") is the skill's default and is **not** our target — ignore it. Our target is 5,500–7,000 words/chapter.

### Local preview
`.claude/launch.json` (in the workspace root, NOT the book repo) has a config named **`ai-thinking-book`** (`npx mystmd start --port 3001`, cwd `books/cai1001c-ai-thinking`). Start it with the preview tooling (`preview_start` name `ai-thinking-book`). Site: `http://localhost:3001`. **Chapter URLs are flat** — MyST drops the `chapters/` folder, so Chapter 8 is `http://localhost:3001/ch08-ai-real-world`. After editing `myst.yml`, stop and restart the preview server (it does not hot-reload project config). After writing a chapter, verify on localhost: exactly one `<h1>`, clean section numbering, all figures load (no broken images), Mermaid diagrams render.

### Git, credentials, and pushing
There is no `gh` CLI and no token in env. Extract the cached token when you need the GitHub API (never print it):
```
CRED=$(printf 'protocol=https\nhost=github.com\n\n' | GCM_INTERACTIVE=never GIT_TERMINAL_PROMPT=0 git credential fill 2>/dev/null)
GH_TOKEN=$(printf '%s\n' "$CRED" | sed -n 's/^password=//p')
```
Plain `git push` works directly via the credential manager.

**The professor pushes to the remote between your commits** (a separate session-materials workstream — see §10). **Always `git fetch origin main` before pushing.** If the remote moved: `git -C books/cai1001c-ai-thinking rebase origin/main` (the files differ, so it is a clean rebase), then push. **Never force-push.**

Commit form (the `-c` flags set the author; the trailer is required):
```
git -C books/cai1001c-ai-thinking -c user.name="c-marq" -c user.email="cmarq2k8@gmail.com" commit -m "Chapter 8: AI in the Real World" -m "<body>" -m "Co-Authored-By: Claude Opus 4.7 (1M context) <noreply@anthropic.com>"
```
**Commit only when the professor approves the chapter.** The professor reviews each chapter on localhost first.

### Deploy
Pushing to `main` triggers the "MyST GitHub Pages Deploy" GitHub Action. Monitor the run via the API (`/repos/c-marq/cai1001c-ai-thinking/actions/runs`) with `$GH_TOKEN` until `completed / success`, then confirm the live page returns HTTP 200.

## 6. Per-chapter workflow (follow this for Chapter 8)

1. **Currency-check** the chapter's tools with fresh web research (a `constraints.md` rule — AI products change monthly). For Ch 8: the capstone build tool (proposed **Gemini Canvas**), **Code.org "AI for Oceans"**, and current robotics / autonomous-vehicle facts.
2. **Write the prose** matching the format spec in §7 exactly.
3. **Generate 4 figures**, proofread each, regenerate flaws (§7, §8).
4. **Verify on localhost.**
5. **Present to the professor for review.** Do not commit yet.
6. **On approval:** validate → `git fetch` → rebase if needed → commit → push → monitor deploy → confirm live.

## 7. Chapter format spec — MATCH THIS EXACTLY

Every chapter 1–7 follows this; Chapter 8 must too.

- **Frontmatter:** `title: "Chapter 8: AI in the Real World"`, `subtitle:`, `short_title: "8 · AI in the Real World"`, `description:`, `label: ch-08-ai-real-world`, `tags: [...]`.
- **NO `# H1` heading in the body.** MyST renders the frontmatter `title` as the page H1. A body `# Heading` creates a *duplicate* title and pushes every other heading down a level. (This bug hit Chapters 1 and 4 and was fixed.) The body starts with the figure, then the banner, then prose.
- **Order after frontmatter:** (a) an HTML comment holding the fig-8-1 generation prompt; (b) the `:::{figure}` directive for the opening master infographic; (c) a banner line — `**Chapter 8 of 8 · The Big Picture**` (Ch 1–3 used "· Foundations", Ch 4–7 "· The Technologies"); (d) intro paragraphs that *demystify* — open on a hype headline/myth and take it apart; (e) `## Learning Objectives` (4–5, numbered); (f) `## How This Chapter Moves` (one paragraph); (g) numbered `## 8.1`, `## 8.2`, … sections; (h) `## Chapter Summary` with `### Key Takeaways` and `### Key Terms`; (i) a closing `### Bridge ...` (Ch 8 bridges to the capstone and addenda, not a Ch 9); (j) `## Apply and Analyze` — the fixed end-of-chapter block.
- **Section numbering is MANUAL** ("8.1", "8.2" written into the headings; "Figure 8.1", "Diagram 8.1" written into captions). MyST auto-numbering is OFF in `myst.yml` — do not turn it back on.
- **Signature callouts** — MyST admonitions with these exact titles and classes:
  - `:::{admonition} 🔍 Myth vs. Reality` / `:class: warning`
  - `:::{admonition} ✋ Try This` / `:class: tip`
  - `:::{admonition} 🛠️ In Practice: …` / `:class: note`
  - `:::{admonition} ⚠️ Watch Out: …` / `:class: caution`
  - `:::{admonition} ⚖️ Ethics Check: …` / `:class: important`
  - `:::{dropdown} 🔎 Going Deeper: …` for an optional deep-dive.
- **Fixed end-of-chapter block** under `## Apply and Analyze`: a lead sentence noting the §8.x walkthrough was the demo; then `### Review Questions` (5, multiple-choice/true-false) with a `:::{dropdown} Answer Key`; `### Discussion Question` (1); `### Breakout Lab: …` (groups of 3–4, ~35–45 min, low-stakes, with a "Submit:" line); `### Optional Take-Home: Going Deeper` (*assigned at instructor's discretion*, an ~300-word reflection that adds ethics/bias). If a chapter has a Colab lab, an `### Optional Advanced Lab` section with the "Open in Colab" badge sits before the take-home — **Chapter 8 does not need a Colab lab** (the reproduce-in-Python competencies, C4 and C6.2, are already covered by the Ch4 and Ch6 notebooks).
- **MyST quirks:** escape every `$` before a digit as `\$` in body text. Mermaid uses a fenced ` ```{mermaid} ` block; caption it manually as *Diagram 8.X*.
- **Voice:** the "Demystify & Apply" style — anti-hype, plain, warm, second person, no assumed knowledge, discipline-rotating examples (business, healthcare, trades, students, everyday life), honest about limits. Word target **5,500–7,000**; aim for the upper half (see §11).

## 8. Figure system spec

- **4 generated master infographics per chapter**, plus 1–2 Mermaid diagrams where structural.
- **Style:** dense, flat, ai4educators-style "master infographic" — deep **teal** ink + warm **coral** accent, white/pale-blue background, faint circuit-board motif in the margins only, soft shadows, bold uppercase sans-serif labels. 16:9 landscape.
- **Generate** with `generate-image.js`, always passing `--reference books/cai1001c-ai-thinking/images/ch01/fig-1-1-age-of-ai.png` (the locked style anchor). Every prompt must say: short correctly-spelled labels only, no garbled text, and **do not copy any text/content from the reference image**.
- **Composition must be NEW for the Chapter 8 opener.** Compositions already used for openers: Ch1 hub-with-side-panels · Ch2 left-to-right journey · Ch3 ascending staircase · Ch4 roster (three zones) · Ch5 two-territory split · Ch6 four stacked bands · Ch7 one-prompt-to-three-columns. Pick something distinct for Ch8 (e.g., a concentric/orbit map, a 2×2 quadrant, a layered cross-section).
- **Files:** `images/ch08/fig-8-1-slug.png` … `fig-8-4-slug.png`. Above each `:::{figure}` directive keep an HTML comment with the generation prompt. Figure directive pattern (opener `:width: 100%`, inner figures `:width: 90%`):
  ```
  :::{figure} ../images/ch08/fig-8-1-slug.png
  :label: fig-8-1
  :alt: One sentence describing the image.
  :width: 100%
  :align: center

  **Figure 8.1.** *Short title.* One-sentence caption.
  :::
  ```
- **Proofread every generated image by viewing it.** Regenerate any with garbled/misspelled text or reference-leak.

## 9. Chapter 8 — detailed spec

**`chapters/ch08-ai-real-world.md` — "AI in the Real World: From Idea to Application."** The final chapter; it must also feel like the book's synthesis. Competencies **C1.5** (enterprise applications / implementation readiness), **C7** (robotics), **C2** (ethics — its dedicated synthesis). Banner: *Chapter 8 of 8 · The Big Picture*.

Suggested sections (confirm with the professor):
- **8.1 — How Organizations Adopt AI.** AI readiness; computing scalability (cloud vs. on-prem); technical trade-offs; data pipelines; why most of the AI project cycle (Ch 1) is organizational, not technical. (C1.5)
- **8.2 — Robotics and Autonomous Systems.** Robots as AI in the physical world; the sense–think–act loop; sensors; human–robot interaction; navigation and path-planning; reinforcement learning revisited; autonomous vehicles and their ethics. (C7)
- **8.3 — The Ethics of AI: A Synthesis.** Pull together the ethics thread from every chapter — training-data bias, privacy, algorithmic fairness, accountability ("the algorithm decided" is never an answer), human-in-the-loop, provenance. (C2)
- **8.4 — From Idea to Application: Your Capstone.** Frame and launch the capstone — students design and build a small AI-powered app that solves a real problem.

**Featured hands-on:** the **capstone project** itself, plus **Code.org "AI for Oceans"** (`code.org/oceans` — free, no account, any age) as a hands-on bias lesson supporting §8.3. The capstone build tool should be **free and age-open** — proposed: **Gemini Canvas** (free, 13+; builds simple interactive apps from a prompt). **Verify Gemini Canvas's current state before writing**, and **ask the professor to upload the existing capstone rubric and project description from last semester** — revise them to the free/age-open tool and a simplified scope, and deliver a clean rubric.

## 10. Remaining deliverables after Chapter 8

- **Front matter** — `front-matter/dedication.md` (short; ask the professor whether to write it or leave space for him), `foreword.md` (an opening note on why the book exists and who it is for; offer a draft for his approval), `how-to-use.md` (explain the chapter rhythm, the callout types, the end-of-chapter block, the optional Colab labs, the tools, and the age note).
- **Addendum A — Course Map:** a table mapping each chapter to the seven CAI1001C competencies and the four gen-ed PLOs (the mapping is in `constraints.md` §5 and §7).
- **Addendum B — Glossary & Concept Index:** compile every chapter's "Key Terms" into one alphabetical glossary, noting the chapter each term is introduced in.
- **Addendum C — Grading Scale & Point Distribution:** ask the professor for the grading breakdown (the session files reference point values, e.g. group lab 4 pts, take-home 30 pts).
- **Addendum D — Academic Integrity & AI Disclosure Policy:** a real policy — chapters already cite "Addendum D" for when and how to disclose AI use.
- **Addendum E — Tool Quick-Reference:** one card per tool — name, URL, cost, minimum-age policy, and a "verified as of" date. Use §11.
- **`index.md` — final landing page:** keep the cover (already at `:width: 100%`, first element); add the value proposition, the audience, what students learn, and a chapter grid. The `book-writer` skill's Workflow E describes this.

## 11. Verified tool facts (as of May 2026 — re-verify before use)

For Addendum E and for accuracy. **Student-required tools must be free and usable by a 16–17-year-old on a personal account.** Under-18 dual-enrollment students are in the class.

| Tool | Access | Age | Notes |
|------|--------|-----|-------|
| Gemini (app) | Free, Google account | 13+ | Gemini 3 / 3.1; paid tiers Google AI Plus/Pro/Ultra |
| NotebookLM | Free | 13+ | Source-grounded research; Audio/Video Overviews |
| Gemini Gems | Free | 13+ | Custom assistants; created on web |
| Gemini Canvas | Free | 13+ | Builds simple interactive apps — proposed capstone tool |
| Google AI Studio | Free | **18+** | Instructor-demo only |
| Nano Banana (image gen) | Free | **18+** on personal accounts | Instructor-demo only; SynthID watermark |
| Veo (video gen) | **Paid** plan | **18+** | Instructor mention only; Veo 3.1 (re-check for Veo 4) |
| Teachable Machine | Free, no account | any | No-code model trainer |
| TensorFlow Playground | Free, no account | any | Neural-net visualizer |
| Hugging Face Spaces | Free, public Spaces no account | any to use | Use only pre-vetted Spaces |
| Datawrapper | Free tier, no sign-up to start | any | Charts |
| Code.org "AI for Oceans" | Free, no account | any | Bias lesson |

**Age-safety rule:** 18+ apps (AI Studio, Nano Banana, Veo) are **instructor-demo only, never a required student task**; students always apply a free, age-open tool. Excluded entirely: Perspective API (being sunset).

## 12. Coordination notes

- **The professor runs a separate workstream** building per-session course-delivery files — `sessions/sessionXX.md` plus `guided-demos/gdXX.html`, `group-labs/grpXX.html`, `homeworks/ngXX.html` — in their own chats. **The book-finishing chat should stay on the textbook** (`chapters/`, `front-matter/`, `addenda/`, `index.md`, `myst.yml`, `notebooks/`) and not touch the session/demo/lab/homework folders. Because of this parallel workstream, **always fetch and rebase before pushing** (§5).
- **Known issue — chapter length.** By `validate-chapter.js`'s strict count the chapters have run under the 5,500–7,000 target and trended down (Ch1 ≈5,900 → Ch7 ≈4,400; the validator strips HTML comments and directives, so the reader-facing length is somewhat higher). **Write Chapter 8 fuller — aim for ≈6,000+ by the validator.** The professor is aware; he may later want a depth pass on the earlier chapters — offer it.
- The professor reviews every chapter and is terse in approvals ("good", "move on", "done"). He is meticulous about figures — no garbled text, varied compositions, on-style.

---

*Handoff written May 2026, after Chapters 1–7 were completed, deployed, and approved. The book is one chapter plus front matter, addenda, and a landing page away from finished.*
