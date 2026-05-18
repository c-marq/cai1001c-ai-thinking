# Constraints — AI Thinking (CAI1001C)

> The governing specification for the rebuilt **AI Thinking** course textbook.
> This file supersedes any other `constraints.md` in the workspace. The PL-300
> Power BI `constraints.md` governs a different course and audience and does
> **NOT** apply here.

---

## 1. Course & Book Identity

- **Course:** CAI1001C — Artificial Intelligence (AI) Thinking. 3.00 credits. Miami Dade College.
- **Author:** Professor Carlos Marquez. (Course materials co-credited with Ernesto Lee.)
- **Project:** a ground-up rebuild of the existing 15-chapter book into a new
  **8-chapter** book — one chapter per week of an 8-week term.
- **Prerequisites:** CGS1060C and MAT1033 recommended, **not required**. No prior
  programming experience assumed.
- **The professor's stated goal (the spine of the book):**
  *"Demystify the AI hype, show how the tech works, how to apply it, have them
  apply it, then have them analyze their process."*

---

## 2. Audience

Open-enrollment survey course. The audience is genuinely mixed:

- Dual-enrollment high-school students (**some are under 18**)
- Recent high-school graduates
- Returning working professionals
- Self-taught analysts and programmers
- Students across all degree programs and stages

Fewer than 25% are in computing programs (cyber, data analytics, AI). Many are
business, nursing, and other disciplines.

**Design implications:**
- Must be genuinely clear to a 16-year-old and to a returning adult with zero
  CS background — without boring a self-taught programmer.
- Depth is *optional and layered*: technical detail lives in `Going Deeper`
  dropdowns and in optional "Open in Colab" labs, never as a wall in the body.
- **Age constraint (critical):** some students are under 18 and signing in with
  **personal Google accounts**. This governs every tool decision — see §8.

---

## 3. Style & Voice — the "Demystify & Apply" profile

This book uses neither the neurodivergent-friendly style of the PL-300 book nor
an advanced industry-track style. It is its own profile.

- **Anti-hype, plain-spoken, warm.** Direct second person ("you"). A professor
  who has taught this ten times. No hype, no jargon walls, no condescension, no
  academic stiffness.
- **The 9th-grader-and-the-returning-nurse test.** Every core concept gets a
  plain-language explanation both could follow — not dumbed down, genuinely
  clear. Pattern: familiar anchor → build the bridge → name the concept → one
  honest sentence on where the analogy breaks → why it matters in the real world.
- **No assumed knowledge.** Every technical term is defined on first use.
- **Layered depth.** Use `:::{dropdown} Going Deeper` for technical detail so
  advanced readers get more and beginners are never lost.
- **Discipline-rotating examples.** Draw from business, healthcare/nursing,
  education, creative work, skilled trades, and everyday life. No CS-centric
  defaults. Every student should see their field somewhere.
- **No recurring cast. No South Florida / Miami theme.** Both are stripped
  entirely (they were structural in the old book). Examples are varied,
  current, and placeless.
- **Banned:** uncritical hype words ("revolutionary," "game-changer,"
  "unleash," "supercharge," "magic"), and "just" used to minimize difficulty.
  Acknowledge AI's limits and failures honestly — that *is* the demystifying.
- **Length:** 5,500–7,000 words per chapter.

---

## 4. Pedagogical Model

Every chapter runs the professor's loop:

1. **Demystify** — open on a real hype headline or myth, then cut through it.
2. **How the tech works** — the theory of the concept, explained plainly.
3. **How to capitalize on it** — an instructor-led walkthrough of a real app
   that demonstrates the concept (interface, features, customizing
   instructions, sample prompts).
4. **Apply it** — students use a free, age-open tool on their *own* use case
   (the breakout-group lab).
5. **Analyze your process** — students reflect on how they applied the tool,
   what it got right and wrong, and the ethics/bias at play (take-home).

**The chapter's focus is always the CONCEPT, never the app.** The competency /
technology category is the constant; apps are interchangeable vehicles. The app
the instructor demos and the app students use **may be two different apps**
serving the same concept — this is by design (see §8). Chapter *titles* lead
with the concept, not the app.

---

## 5. Competencies & Program Learning Outcomes

Extracted from the official CAI1001C syllabus (updated Fall 2025).

**Competencies**
- **C1** — Examine the field of AI and ML: digital literacy, data sources & IoT,
  history of AI, the AI project cycle, supervised vs. unsupervised learning and
  neural networks, enterprise applications and implementation readiness.
- **C2** — Ethical and legal considerations: computing-ethics vocabulary
  (algorithmic privacy, algorithmic fairness); ethics issues at the
  development, implementation, and administration levels.
- **C3** — Explore datasets: data, data acquisition, visualization,
  transformation; data sources; using datasets to train models.
- **C4** — Classification algorithms: linear classifiers, SVMs, quadratic
  classifiers, k-NN, decision trees, neural networks; **reproducing** them in
  Python.
- **C5** — Computer vision and facial recognition: image segmentation, object
  and motion detection, object classification.
- **C6** — Natural Language Processing: machine translation, sentiment
  analysis, deep learning for NLP, speech recognition/synthesis;
  **reproducing** chatbots in Python.
- **C7** — Robotic sensing and manipulation: robotics, sensing, human-robot
  interaction, navigation and path planning, reinforcement learning,
  autonomous vehicles.

**Gen-Ed PLOs**
- **PLO1** — Use quantitative analytical skills to evaluate and process numerical data.
- **PLO2** — Solve problems using critical and creative thinking and scientific reasoning.
- **PLO3** — Demonstrate knowledge of ethical thinking and its application to society.
- **PLO4** — Use computer and emerging technologies effectively.

> **C4 / C6.2 note.** The "reproducing … using Python" requirement is satisfied
> by **optional "Open in Colab" take-home labs**, not by hand-coded Python in
> the chapter body. The chapters teach the concepts and the app application;
> the Colab labs carry the Python reproduction.

---

## 6. Book Structure

Structural inspiration: Dr. Ernesto Lee's *AI Thinking for Educators* — adopted
as an idea, not copied.

**Front matter:** Cover · Dedication · Foreword · How to Use This Book.

**8 chapters**, one per week of an 8-week term, with evocative two-part,
concept-first titles.

**Addenda:**
- **A — Course Map:** chapter ↔ competency ↔ PLO alignment.
- **B — Glossary & Concept Index.**
- **C — Grading Scale & Point Distribution.**
- **D — Academic Integrity & AI Disclosure Policy.**
- **E — Tool Quick-Reference:** a living appendix listing every tool, its URL,
  cost, age policy, and "verified as of" date — because the apps change fast.

---

## 7. Chapter Map

The chapter focus is the concept. The instructor-demo app and the student
hands-on tool are vehicles; for age-gated apps they differ (see §8).

| Ch | Title | Concept focus | Instructor-demo app | Student hands-on tool (free, age-open) | Competencies | PLOs |
|----|-------|---------------|---------------------|----------------------------------------|--------------|------|
| 1 | Welcome to the Age of AI — Cutting Through the Hype | What AI/ML/DL is; history; supervised vs. unsupervised; the AI project cycle | **Gemini** (13+) | Gemini · Quick Draw hook | C1 | 2, 4 |
| 2 | Digital Literacy & Data — Where Knowledge Comes From | Digital literacy, curating information, evaluating sources, data sources, IoT, data acquisition | **NotebookLM** (13+) | NotebookLM | C1, C3 | 1, 2, 4 |
| 3 | Working with Data — Turning Numbers Into Insight | Data exploration, transformation, visualization; the ML workflow | **Google AI Studio** (demo only, 18+) | **Datawrapper** (no account) | C3 | 1, 2, 4 |
| 4 | Machine Learning — Teaching Machines to Decide | Classification: linear classifiers, SVMs, k-NN, decision trees, neural networks; training & evaluating | **Teachable Machine + TF Playground** (no account) | same — students train & visualize directly | C4, C1 | 1, 2, 4 |
| 5 | Computer Vision — How Machines See and Create | Image representation, classification, object/motion detection, segmentation, facial recognition; image generation | **Nano Banana** (demo only, 18+) | **Hugging Face Spaces** image demo (no account) | C5 | 2, 3, 4 |
| 6 | Language & Conversation — How Machines Understand Us | NLP: tokenization, sentiment, translation, speech, LLMs & transformers; chatbots | **Gemini Gems** (13+) | Gemini Gems | C6 | 2, 4 |
| 7 | Generative Media — Creating Sound, Image, and Video with AI | Generative video & multimodal AI; how generative models work and their limits | Free no-account video tool (**Hugging Face Spaces**); Veo named as paid state-of-the-art | Hugging Face Spaces video/animation demo | C5, C1 | 2, 3, 4 |
| 8 | AI in the Real World — From Idea to Application | Enterprise AI & implementation readiness; robotics, sensing, autonomous systems; ethics synthesis; the capstone | Capstone build tool (proposed: **Gemini Canvas**, 13+) | Capstone app-builder project · Code.org "AI for Oceans" bias lesson | C1, C2, C7 | 2, 3, 4 |

- All six required Google-app lessons are present (Gemini, NotebookLM, AI
  Studio, Nano Banana, Gemini Gems, Veo). Veo is **swapped as a featured app**
  (paid) per the professor's instruction — video generation is still a full
  lesson, taught with a free tool, Veo covered as the paid leading example.
- **Ethics (C2)** is woven into every chapter and synthesized in Chapter 8.
- App build order, each building on the prior: Gemini → NotebookLM → AI Studio
  → Teachable Machine/TF Playground → Nano Banana → Gems → generative media →
  capstone. Integrations are explicit (e.g., NotebookLM research feeding Gemini
  outlines; instruction-writing skills reused to author a Gem).

---

## 8. Tools & the Age-Safety Rule (NON-NEGOTIABLE)

The class includes students under 18 on **personal Google accounts**. Therefore:

- **Every tool a student is required to use must be free and usable by a
  16–17-year-old on a personal account** — in practice, free and no-account, or
  free and 13+.
- **Age-verified tool tiers (as of May 2026 — re-verify per §13):**
  - **Free, all students may use:** Gemini app (13+), Gemini Gems standard
    (13+), NotebookLM core (13+).
  - **Free, no account, any age:** Teachable Machine, TensorFlow Playground,
    Hugging Face Spaces (public Spaces), Datawrapper (basic), Quick Draw,
    Code.org "AI for Oceans."
  - **18+ — INSTRUCTOR-DEMO ONLY, never a required student task:** Google AI
    Studio, Nano Banana image generation, Veo.
- **Veo** additionally requires a **paid** plan → dropped as a featured app.
- **The demo / hands-on split:** the instructor (an adult) may demonstrate an
  18+ app; students always apply a free, age-open tool to their own use case.
  **No student is ever excluded from a lab.**
- **Hugging Face Spaces:** use only specific, pre-vetted, tested Spaces. Record
  the exact URL in the chapter and in Addendum E. Never tell students to browse
  Spaces freely (the platform is unmoderated).
- **Currency stamp:** every tool walkthrough carries a "Verified as of <date>" line.
- **Excluded tool:** Perspective API — Google is sunsetting it (service ends
  Dec 31, 2026). Not used.

---

## 9. Fixed End-of-Chapter Block (every chapter, no exceptions)

1. **Five questions** — multiple-choice / true-false, with an answer key.
2. **One discussion question** — thought-provoking, not recall-based.
3. **Instructor-led use-case walkthrough** of the chapter's app(s) — interface,
   features, customizing instructions, sample prompts. *(Placed where it
   teaches best — in the application section — not literally after the quiz.)*
4. **Breakout-group lab** — groups of 3–4, the same app (or the age-safe
   equivalent), students' own use case. Low-stakes, due end of class.
5. **Optional take-home assignment** — a deeper dive into the same group
   project, adding ethics-and-bias considerations to the reflection questions.
   Marked optional; assigned at the instructor's discretion based on the
   class's assignment cadence.

> This block overrides the book-writer skill's default "no quizzes in the
> chapter file" rule. The professor's handoff governs.

---

## 10. Per-Chapter Skeleton

1. Opening master infographic (chapter overview) + HTML-comment prompt block.
2. Chapter title and "Chapter X of 8" banner.
3. Hook — a hype headline or myth to demystify.
4. Learning objectives (3–5), tied to the chapter's competencies.
5. Chapter roadmap (one paragraph).
6. **How the tech works** — theory sections; plain-language concept
   explanations; analogies; `Going Deeper` dropdowns; Mermaid where structural.
7. **How to capitalize on it** — the featured technology and an instructor-led
   app walkthrough.
8. Other use cases — discussion of where else the technology applies.
9. Ethics & bias — woven in at the natural moment.
10. Fixed end-of-chapter block (§9).
11. Key takeaways · vocabulary · bridge to the next chapter.
12. Optional "Open in Colab" Python lab (for C4 / C6.2 chapters).

**Signature callouts** (a light set — not the ND five-box system):
`Myth vs. Reality`, `Try This`, `In Practice`, `Watch Out`, `Ethics Check`.

---

## 11. Capstone Project

- The course capstone is a **simplified AI app-builder project**: students
  build a small, working AI-powered app or tool that solves a real problem of
  their choosing, integrating concepts from across the course.
- Built with a **free, age-open** tool — proposed: **Gemini Canvas** (free,
  13+, builds working mini-apps from a prompt). Verify currency before Ch 8.
- The existing repo's AI-Studio-based final project must be **re-tooled** — AI
  Studio is 18+ and fails the free/age-open bar.
- Requirements are **simplified and scoped**; the professor finalizes the
  rubric. Framed and launched in Chapter 8. The reflection includes ethics/bias
  and a process analysis.

---

## 12. Figures & Visual Identity

- **Style:** dense, richly illustrated **master infographics** in the
  ai4educators.net style, retinted to the AI Thinking palette. Each *depicts*
  its concept with real objects, mini-diagrams, annotations, and arrows — not
  sparse labelled shapes.
- **Palette:** distinct from the PL-300 navy/gold. **Proposed: deep teal +
  warm coral on white / pale background.** Finalize at scaffold time.
- **Per chapter:** one opening master infographic + concept infographics;
  varied compositions, no two openers repeating a layout.
- **Generation:** Nano Banana Pro via `generate-image.js`. PNG only. MyST
  `:::{figure}` directives only — never markdown image syntax.
- **Proofread every generated image** — no garbled or misspelled text;
  regenerate any image that fails.
- **Mermaid diagrams** where a structural/relational diagram genuinely helps;
  do not pad to a quota.

---

## 13. Currency Rule

- **Re-verify each app immediately before writing its chapter** — current
  official name, capabilities, workflow steps, age policy, and cost. AI
  products change monthly.
- Google I/O is May 19–20, 2026 — a Veo 4 / new-model announcement is likely;
  re-check before the relevant chapters.
- Stamp **"Verified as of <date>"** on every tool walkthrough and in Addendum E.
- Verified baseline (May 2026): Gemini 3 / 3.1 generation; in-app labels
  "Fast / Thinking / Deep Think"; paid tiers are Google AI Plus / Pro / Ultra.
  Nano Banana 2 and Nano Banana Pro; "🍌 Create images." NotebookLM three-panel
  layout with Audio & Video Overviews. Veo 3.1. Gems are free (13+), created on
  the web app.

---

## 14. Deliverable & Build

- **New GitHub repository.** MyST / Jupyter Book, deployed to GitHub Pages.
- The existing repo `c-marq/AI-Thinking-CAI1001C` is retained as the home for
  datasets, slides, and assessment companion materials.
- Chapters are MyST Markdown. UTF-8. PDF export enabled.
- Optional "Open in Colab" notebooks in `notebooks/` for the Python labs.
- **MyST quirk — dollar signs:** escape every `$` before a digit in body text
  (`\$5 billion`, not `$5 billion`) — MyST parses `$`+digit as inline math.
  Frontmatter is exempt.
- Validate every chapter with the skill's `validate-chapter.js` before commit.
- Commit and push **only when the professor asks.**

---

## 15. Out of Scope — Strip / Do Not Carry Forward

- The **South Florida / Miami / Cuban theme** — removed entirely (it was
  structural in the old book: opening narratives, recurring cast, analogies,
  dataset and code strings).
- The **recurring fictional cast** (Sofia, Marcus, Abuela Carmen, Prof. Reyes,
  etc.) — removed.
- **Heavy hand-coded Python in the chapter body** — moved to optional Colab labs.
- The old book's **broken cross-references**, **outdated model names**
  (ChatGPT / GPT-4 / DALL-E used as defaults), and **dated statistics** — do
  not carry forward.
- Quizzes, discussions, and projects left as **empty stubs** in the old repo —
  authored fresh, not inherited.

---

## 16. Workflow

1. Professor approves this `constraints.md`.
2. Scaffold the new repo + generate the book cover.
3. Per chapter: currency-check the app → write the chapter → generate figures →
   validate → **professor reviews before the next chapter** → commit only when
   the professor asks.
4. After all 8 chapters: addenda, final landing page, capstone rubric.

*Verified and authored: May 2026.*
