---
title: "Chapter 1: Welcome to the Age of AI"
subtitle: "Cutting Through the Hype"
short_title: "1 · Age of AI"
description: "What artificial intelligence, machine learning, and deep learning really are; the honest history of AI and its cycles of hype; how machines learn; the AI project cycle; and a first hands-on look at Gemini."
label: ch-01-age-of-ai
tags: [foundations, ai-history, machine-learning, gemini]
---

<!--
FIGURE 1.1 — opening master infographic. Generated with Nano Banana Pro via generate-image.js.
Style: dense ai4educators-style master infographic, retinted to the book palette (deep teal,
warm coral, white/pale background, light circuit-board margin motif). 16:9 landscape.
Composition: hub-with-side-panels — central title block "THE AGE OF AI", four labelled zones
around it: (1) AI / ML / DL nested rings, (2) a small boom-and-winter history timeline,
(3) "how machines learn" with labelled-examples icons, (4) the five-step AI project cycle as
a loop. No garbled text; short labels only.
-->

:::{figure} ../images/ch01/fig-1-1-age-of-ai.png
:label: fig-1-1
:alt: A master infographic mapping the chapter — what AI, machine learning, and deep learning are, a short history of AI, how machines learn from examples, and the five-step AI project cycle.
:width: 100%
:align: center

**Figure 1.1.** *The Age of AI.* The whole chapter on one page — what AI really is, where it came from, how machines learn, and the cycle every AI project follows.
:::

**Chapter 1 of 8 · Foundations**

In the same month, you can read that artificial intelligence will eliminate half the world's jobs within a decade — and that AI is "just fancy autocomplete" that cannot really do anything. You can hear that it is the most important invention since electricity, and that it is a bubble about to burst. You have probably felt the whiplash yourself: a flash of *this is amazing*, followed closely by *wait, is this nonsense?*

Both feelings are reasonable. And both headlines cannot be right.

Here is the promise of this book, starting with this chapter: by the end, you will not have to take anyone's word for it — not a headline's, not a tech company's, and not mine. You will understand how this technology actually works, well enough to use it for real tasks and to judge the claims people make about it. That is what the title of this book means. *Mind the machine*: pay attention to it, learn what it is doing — and keep your own judgment firmly in charge.

This first chapter lays the foundation. We will define what artificial intelligence really is (and clear away what it is not), walk through its surprisingly bumpy history, see how machines actually "learn," and trace the cycle that every AI project follows. Then you will open **Gemini** — a free AI assistant — and put it to work on a real task, with a clear eye for what it does well and where it falls down.

## Learning Objectives

By the end of this chapter, you will be able to:

1. **Define** artificial intelligence, machine learning, and deep learning, and explain how the three relate.
2. **Distinguish** software that follows rules a human wrote from software that learns patterns from examples.
3. **Trace** the history of AI and recognize its repeating pattern of hype, disappointment, and renewal.
4. **Describe** how machines learn — supervised versus unsupervised — and the five stages of the AI project cycle.
5. **Use** Gemini for a genuine task and **evaluate** the quality and trustworthiness of what it produces.

## How This Chapter Moves

We start with definitions, because almost every argument about AI is really an argument about words. From there we go back in time — the history matters, because it shows you that today's excitement has happened before. Then we open the hood: how a machine "learns," and the standard cycle for building an AI system. Finally, we get hands-on with Gemini and turn understanding into a skill you can use the same night.

## 1.1 What Artificial Intelligence Actually Is

Let us begin with a definition that will actually hold up.

**Artificial intelligence** is the field of building computer systems that perform tasks we normally associate with human intelligence — recognizing a face, understanding a sentence, recommending a treatment, predicting next month's sales.

That definition is fine as far as it goes, but it hides the part that matters. A pocket calculator performs a task that takes humans real mental effort, and nobody calls a calculator "intelligent." So what is the actual difference between ordinary software and AI?

The difference is *where the know-how comes from.*

Think about two ways a community clinic might flag patients who are likely to miss an appointment. In the **traditional software** approach, a programmer sits down with a nurse and writes explicit rules: *if the patient is more than 30 minutes away, and it is their first visit, and they have missed an appointment before, then flag them.* Every rule is written by a human, in advance. The computer just follows the list.

In the **machine learning** approach, nobody writes those rules. Instead, you hand the computer two years of past appointments — who showed up, who did not, and dozens of details about each one — and the computer finds the patterns itself. It might discover that Monday-morning first visits in winter are the real risk, a pattern no one thought to write down. Nobody told it that rule. It *learned* it from examples.

That is the line that matters. Traditional software follows instructions a human wrote. **Machine learning** writes its own instructions by studying examples. Almost everything people find surprising about modern AI flows from that one shift.

:::{admonition} 🔍 Myth vs. Reality
:class: warning
**The myth:** "AI thinks like a human brain."

**The reality:** It does not. A machine learning system is a very sophisticated pattern-matcher. It has read or seen an enormous number of examples and become extremely good at predicting what tends to come next — the next word, the next pixel, the right category. That is genuinely powerful, and it is *not* the same as understanding, wanting, or knowing. Keeping this straight is the single most useful habit in this whole book: when a system impresses you, ask *what pattern is it matching?* rather than *what is it thinking?*
:::

### The AI Family Tree

You will hear three terms used almost interchangeably — *AI*, *machine learning*, *deep learning* — plus a fourth, *generative AI*, that is everywhere right now. They are not synonyms. They nest inside one another, like measuring cups.

```{mermaid}
graph TD
    AI["Artificial Intelligence — the whole field"]
    AI --> RULES["Rule-based systems — humans write every rule"]
    AI --> ML["Machine Learning — learns patterns from examples"]
    ML --> DL["Deep Learning — layered networks, huge data"]
    DL --> GEN["Generative AI — creates text, images, audio, video"]
```

*Diagram 1.1. The AI family tree. Each inner box is a more specialized kind of the box above it.*

- **Artificial intelligence** is the whole field — every attempt to make computers do intelligent-seeming things, including the old rule-based approach.
- **Machine learning** is the part of AI where the system learns from examples instead of following hand-written rules. This is where nearly all of today's progress lives.
- **Deep learning** is a powerful style of machine learning that uses many-layered networks loosely inspired by brain cells. It is what made AI suddenly good at images and language around 2012.
- **Generative AI** is the most recent branch: deep-learning systems that *create* — they produce new text, images, audio, and video. Gemini, the tool you will use in this chapter, lives here.

So when a news story says "AI," it almost always means machine learning, and usually deep learning, and lately generative AI most of all. Knowing which layer someone means is half of cutting through the hype.

<!--
FIGURE 1.2 — concept infographic, before/after composition. Two large side-by-side panels with
a central coral arrow. LEFT "TRADITIONAL SOFTWARE": a person at a desk handing a list of rules
("IF... THEN...") into a computer. RIGHT "MACHINE LEARNING": a stack of labelled example cards
flowing into a computer that outputs its own rule. Footer banner: "RULES IN vs. EXAMPLES IN".
Deep teal + warm coral, white background, ai4educators master-infographic style. Short labels only.
-->

:::{figure} ../images/ch01/fig-1-2-rules-vs-learning.png
:label: fig-1-2
:alt: A side-by-side comparison: traditional software, where a person writes every rule, versus machine learning, where the system studies labelled examples and produces its own rules.
:width: 90%
:align: center

**Figure 1.2.** *Two ways to build software.* Traditional software runs on rules a human wrote in advance. Machine learning studies examples and writes its own.
:::

Why does this distinction matter beyond trivia? Because it tells you exactly where AI is strong and where it is dangerous. A system that learns from examples is brilliant at tasks where good examples exist and the future looks like the past — sorting email, transcribing speech, spotting a tumor pattern a radiologist has seen ten thousand times. That same system is unreliable the moment the world changes, the examples were biased, or the task needs genuine reasoning about something new. You will see that trade-off in every chapter of this book.

## 1.2 The Honest History of AI: Booms, Winters, and Now

Here is the fact that should make you a calmer, sharper reader of AI headlines: **we have been here before.** Not at this scale, and not with these capabilities — but the *pattern* of breathless excitement is decades old. Knowing the history inoculates you against both the hype and the cynicism.

AI is not new. It has gone through roughly seventy years of booms and busts.

- **1950 — A question.** The mathematician Alan Turing asked, "Can machines think?" and proposed a practical test: if you cannot tell whether you are talking to a person or a machine, the difference may not matter.
- **1956 — A name.** A small conference at Dartmouth College coined the term "artificial intelligence" and predicted human-level machines within a generation. They were wildly, famously wrong about the timeline.
- **1970s — The first "AI winter."** The bold predictions did not arrive. Funding dried up. The phrase *AI winter* was coined for these long freezes of disappointment and lost investment.
- **1980s–1990s — A boom, then a second winter.** "Expert systems" — huge collections of hand-written rules — showed real commercial promise, then hit a wall: they were too rigid, and they could not learn. Winter returned.
- **1997 — Deep Blue.** IBM's chess computer beat world champion Garry Kasparov. Impressive — but it won by brute-force calculation, not by anything resembling understanding.
- **2012 — The breakthrough that started today.** A deep-learning system crushed every competitor at recognizing objects in photographs. Suddenly machines could see, hear, and translate far better than before. This is the real beginning of the current era.
- **2017 — The transformer.** A new design for neural networks — the "transformer" — made it possible to train enormous models on enormous amounts of text. Every modern AI assistant is built on it.
- **2022 — AI goes mainstream.** A generative chatbot reached a hundred million users faster than any product in history. For most people, this was the moment AI stopped being science fiction.
- **2023–2026 — The current boom.** Hundreds of billions of dollars invested, a new model every few weeks, AI features pushed into every app you own. Genuine breakthroughs and genuine overpromising, side by side.

<!--
FIGURE 1.3 — concept infographic, left-to-right journey/timeline composition. A horizontal
timeline 1950 -> 2026 with milestone markers (Turing 1950, Dartmouth 1956, AI Winter 1970s,
Expert Systems 1980s, AI Winter 1990s, Deep Blue 1997, Deep Learning 2012, Transformer 2017,
Mainstream 2022, Boom 2026). Two visible dips labelled "AI WINTER", a steep climb after 2012.
Deep teal line and markers, warm coral for the winter dips and the final climb. White background,
ai4educators master-infographic style. Short labels only, no paragraphs.
-->

:::{figure} ../images/ch01/fig-1-3-history-timeline.png
:label: fig-1-3
:alt: A timeline of AI from 1950 to 2026 showing two AI winter dips and the steep climb of the modern era after 2012.
:width: 90%
:align: center

**Figure 1.3.** *Seventy years of hype and renewal.* AI has boomed and frozen over before. The line is climbing steeply now — but the pattern is not new.
:::

What should you take from this? Two things, and they pull in opposite directions — which is exactly the point.

First, **the cynics have been wrong.** Every AI winter ended. The technology in your hands today is not a trick; it does things that were genuinely impossible fifteen years ago. Dismissing it as "just hype" is its own kind of mistake.

Second, **the boosters have also been wrong** — repeatedly, confidently, for seventy years. Every boom has produced predictions that did not come true on schedule. When someone today gives you a confident date for when AI will do some dramatic thing, the honest historical answer is: *maybe, and probably later and messier than they say.*

A demystified mind holds both of these at once. The technology is real **and** the hype is real. Your job is to tell them apart — and you can.

:::{dropdown} 🔎 Going Deeper: Why did everything change around 2012?
Three things arrived at the same time, and all three were needed.

**Data.** The internet had quietly produced enormous collections of labelled examples — billions of captioned photos, tagged posts, digitized books. Machine learning is useless without examples, and suddenly there were oceans of them.

**Computing power.** Graphics chips (GPUs), originally built to render video games, turned out to be perfect for the math behind neural networks. Training that once took months took days.

**Better algorithms.** Researchers worked out how to train *deep* networks — many layers stacked together — without them collapsing into nonsense.

Any one of these alone would have changed little. Together they ended the second AI winter and started the era you live in. Keep this in mind: progress in AI is rarely one genius idea. It is usually data, hardware, and method arriving together.
:::

## 1.3 How Machines Learn

We have said that machine learning systems "learn from examples." Now let us make that concrete, because the *kind* of example a system gets shapes everything it can do.

There are two main styles of learning, plus a third worth naming.

**Supervised learning** uses *labelled* examples — examples where someone has already provided the right answer. Imagine training a system to flag fraudulent credit-card charges. You feed it millions of past transactions, each one tagged "fraud" or "not fraud." The system studies them until it can predict the label on a transaction it has never seen. The word *supervised* simply means a human supplied the answers it learned from. Most of the AI you encounter — spam filters, medical-image screening, loan scoring — is supervised.

**Unsupervised learning** uses *unlabelled* examples — raw data with no answers attached. Here the system's job is to find structure on its own. Hand it the purchase histories of fifty thousand shoppers with no labels, and it might discover that customers naturally fall into a handful of groups: weekly bulk shoppers, occasional gift-buyers, late-night browsers. Nobody defined those groups in advance. The system found them.

**Reinforcement learning** is the third style: the system learns by *doing*, through reward and penalty — the way you might train a dog, or learn a video game. It is how AI mastered complex games and how some robots learn to move. We will return to it in Chapter 8.

A small vocabulary makes the rest of this book easier:

| Term | Plain meaning |
|---|---|
| **Feature** | One piece of input information — a patient's age, a transaction's amount, a pixel's color. |
| **Label** | The "right answer" attached to a training example — "fraud," "benign," "will reschedule." |
| **Training data** | The collection of examples a system learns from. |
| **Model** | The pattern the system ends up with after training — the thing that makes predictions. |

Notice the quiet, central role of the **training data**. The model is only ever as good as the examples it learned from. That is not a minor caveat. It is the source of most of what goes wrong with AI.

:::{admonition} ⚠️ Watch Out: Garbage in, garbage out — and bias in, bias out
:class: caution
If a company trains a model on its past hiring decisions, and those past decisions quietly favored one group of applicants, the model will learn that preference and repeat it — faster, at scale, and wrapped in a false air of mathematical neutrality. The machine did not *invent* the bias. It *inherited* it from the examples, exactly as designed.

This is why "the algorithm decided" is never a complete answer. Someone chose the training data. Someone chose the labels. A learning system is a mirror held up to its examples — and mirrors do not flatter or correct. We will return to this in every chapter, because it is the ethical heart of the whole field.
:::

## 1.4 The AI Project Cycle

Whether a team is building a fraud detector, a no-show predictor, or a customer-service chatbot, the work follows the same five-stage cycle. Learning this cycle gives you a mental map for every AI project you will ever see, hear about, or help build.

<!--
FIGURE 1.4 — synthesis infographic, hub-and-spoke / cycle composition. Five labelled stages
arranged in a ring with coral chevron arrows between them: 1 DEFINE THE PROBLEM, 2 GATHER DATA,
3 BUILD THE MODEL, 4 DEPLOY, 5 EVALUATE; a return arrow from EVALUATE back to DEFINE. Small flat
icon in each node (target, database, gears, rocket, magnifying glass). Center label "AI PROJECT
CYCLE". Deep teal nodes, coral arrows, white background, ai4educators master-infographic style.
-->

:::{figure} ../images/ch01/fig-1-4-project-cycle.png
:label: fig-1-4
:alt: The five-stage AI project cycle drawn as a loop — Define the Problem, Gather Data, Build the Model, Deploy, Evaluate — with an arrow looping evaluation back to the start.
:width: 90%
:align: center

**Figure 1.4.** *The AI project cycle.* Five stages, drawn as a loop, because real projects never stop at "done" — they circle back.
:::

**Stage 1 — Define the problem.** Before any data or code, answer one question: *what decision will this AI help a human make?* A clinic does not really want "an AI." It wants to know which of tomorrow's patients to call with a reminder. Vague goals ("use AI to improve care") produce failed projects. Sharp goals ("predict no-shows so front-desk staff can call the ten highest-risk patients") produce useful ones.

**Stage 2 — Gather and prepare data.** Collect the examples the system will learn from, and clean them. This stage is unglamorous and it is where teams spend most of their time — often well over half the project. Real data is messy: missing entries, typos, duplicates, inconsistent formats. As you saw in the last section, the quality of this stage sets the ceiling for everything after it.

**Stage 3 — Build the model.** Now the system actually learns. The team picks a learning method, feeds it the training data, and tests how well it predicts on examples it has never seen. This is the stage people imagine when they think "AI" — and it is often the *fastest* of the five.

**Stage 4 — Deploy.** Put the model where it can do real work — connected to the clinic's scheduling screen, the bank's checkout, the app's home page. Deployment surfaces problems no test could: the data arrives in a slightly different format, the system is slower than expected, staff do not trust its suggestions.

**Stage 5 — Evaluate and monitor.** Watch the system in the real world. Is it accurate? Is it fair across different groups of people? Is it still accurate six months later, or has the world drifted away from its training data? Findings here send you straight back to Stage 1 — which is why the cycle is a *loop*, not a line.

:::{admonition} 🛠️ In Practice: One problem, all five stages
:class: note
A regional bookstore wants to reduce wasted stock. Watch the cycle turn:

1. **Define:** "Predict next week's demand for each title so we order the right amount." (Not "use AI for inventory.")
2. **Gather:** Three years of sales, plus season, local events, and release dates — then weeks of cleaning.
3. **Build:** Train a model; it predicts demand within a usable margin on past data.
4. **Deploy:** The weekly order screen now shows a suggested quantity per title.
5. **Evaluate:** Waste drops — but the model is weak on new authors with no sales history. Back to Stage 1 with a sharper problem.

No AI project is ever truly finished. It is maintained.
:::

## 1.5 Meet Gemini: Your AI Thinking Partner

You now have the concepts. Time to use one.

**Gemini** is a conversational AI assistant made by Google. Under the hood it is a *large language model* — a deep-learning, generative-AI system (look back at Diagram 1.1 and place it: AI → ML → deep learning → generative AI). It was trained on an enormous amount of text and learned, with remarkable skill, to predict what words should come next given what came before. That sounds modest. In practice it means Gemini can draft, summarize, explain, translate, brainstorm, analyze a document you give it, and answer questions in plain conversation.

We start the book here, with Gemini, for a simple reason: it is the most *general-purpose* AI tool you will meet. It is a thinking partner — useful to a nursing student, a small-business owner, a welder studying for a license exam, and a parent planning a budget. Later chapters bring specialized tools for data, images, and video. Gemini is the front door.

As of **May 2026**, Gemini runs on Google's Gemini 3 generation of models. In the app you will see plain labels rather than technical names — typically a faster everyday option and a slower "thinking" option for harder problems. It is **free** with any Google account, and available to anyone **13 or older**. (A paid tier exists with higher limits; you will not need it for this course.)

:::{admonition} 🔍 Myth vs. Reality
:class: warning
**The myth:** "Gemini knows the answer. If it says something confidently, it is true."

**The reality:** Gemini does not look things up in a box of facts. It *predicts plausible text.* Usually plausible and true travel together — but not always. When they part ways, you get a confident, fluent, completely wrong answer. The industry's polite word for this is a **hallucination.** It is not a rare glitch; it is a basic property of how the tool works. Treat Gemini as a fast, articulate, occasionally mistaken colleague — never as an oracle. **You verify. Always.**
:::

## 1.6 Hands-On Walkthrough: Using Gemini Well

This section is the walkthrough your instructor will demonstrate live before you try it yourself. Follow along — then you will apply it in the lab.

> **Verified as of May 2026.** AI tools change fast. If a screen looks different from this description, the *idea* still holds — find the equivalent control.

**Step 1 — Open and sign in.** Go to **gemini.google.com** in any web browser, or open the Gemini app on a phone. Sign in with a Google account. You can try a prompt or two without signing in, but signing in lets you save your conversations.

**Step 2 — Find your way around.** The screen is mostly one big text box that says something like *"Ask Gemini."* That is where you type. Near it you will find a **model selector** (the faster everyday option versus the slower "thinking" option) and a **+** or paperclip button to **attach a file or image**. That is genuinely most of the interface.

**Step 3 — Write a real prompt.** A *prompt* is just the instruction you type. The single biggest skill in this whole book is writing a good one, and it comes down to one habit: **be specific, and give context.**

Watch the difference.

- A weak prompt: *"Give me study tips."*
- A strong prompt: *"I am a part-time nursing student with about five hours to study this week for a pharmacology exam. I learn best by testing myself. Give me a five-day plan with a specific activity each day, and end with three practice questions."*

The weak prompt gets a generic list anyone could have written. The strong prompt gets something genuinely useful — because you supplied the *who, what, how much,* and *what form you want the answer in.* Gemini is a pattern-matcher: the richer and clearer your input, the better the pattern it can match.

:::{admonition} ✋ Try This
:class: tip
Open Gemini and run both prompts above, back to back. Read the two answers side by side. You have just learned more about prompting than any list of "prompt hacks" could teach you — the lesson is simply *specificity and context win.*
:::

**Step 4 — Refine with follow-ups.** You are in a *conversation*, not a search box. If the first answer is close but not right, say so: *"Make it shorter,"* *"Use simpler language,"* *"Focus only on day one,"* *"Now turn the practice questions into multiple choice."* Gemini remembers the thread and adjusts. Most of the value comes from this second and third turn, not the first.

**Step 5 — Customize how it responds.** Two quick ways to shape Gemini's behavior. First, **tell it who to be and how to answer**, right in the prompt: *"Explain this the way you would to someone with no medical background, in about 150 words."* Second, **attach a file** with the **+** button — a PDF, an image, a document — and ask questions about *that*: *"Summarize the key dates from this syllabus."* In Chapter 6 you will learn to save a reusable set of instructions as a custom assistant. For now, putting the instructions directly in your prompt is enough.

### A Worked Example

Suppose you manage a small landscaping business and a customer has emailed an angry complaint. You could type:

> *"You are helping me, the owner of a small landscaping company. A customer emailed upset that we missed an appointment after a rainstorm. Draft a calm, professional reply, under 120 words, that apologizes, explains we reschedule for safety in storms, and offers a discount on the next visit. Friendly, not corporate."*

Gemini returns a solid draft in seconds. You read it, fix the one detail it guessed wrong, adjust a sentence to sound like you, and send. That loop — *you direct, it drafts, you judge and finish* — is the honest picture of working with AI. It is not the machine replacing you. It is the machine handing you a first draft so your effort goes to the judgment only you can supply.

### Other Use Cases

The same pattern serves almost any field:

- **Healthcare student:** turn dense lecture notes into a quiz; have a hard concept re-explained three different ways.
- **Business:** draft a job posting, compare two vendor contracts you paste in, brainstorm names for a service.
- **Skilled trades:** get a study guide for a licensing exam; turn a manual's procedure into a plain checklist.
- **Creative work:** push past a blank page with twenty rough ideas, then pick and develop the two real ones.
- **Everyday life:** build a meal plan around a budget and a dietary restriction; draft a hard email you have been avoiding.

In every case the human sets the goal and judges the result. Gemini supplies speed and a starting point.

:::{admonition} ⚖️ Ethics Check: Three habits, starting now
:class: important
1. **Verify before you trust.** For any fact, name, number, or citation that matters, confirm it with a reliable source. Gemini can hallucinate, and it does so fluently.
2. **Guard other people's information.** Anything you type may be used to improve the service. Never paste someone else's private data — a patient's chart, a classmate's record, a customer's financial details — into a consumer AI tool.
3. **Be honest about using it.** When AI helped with your work, say so if the context calls for it. Using AI is not cheating; *hiding* it when disclosure is expected is. Addendum D spells out this course's policy.
:::

## Chapter Summary

Artificial intelligence is not magic and it is not a fraud. It is software that learns patterns from examples instead of following hand-written rules — a genuinely powerful shift, and a genuinely limited one. AI has boomed and frozen over for seventy years, and today's excitement is the biggest boom yet, mixing real breakthroughs with real hype. Machines learn from labelled examples (supervised), from raw structure (unsupervised), or from reward (reinforcement), and every project moves through the same five-stage cycle. And you have now used Gemini — a generative-AI thinking partner — with the one habit that matters most: direct it clearly, then judge what it gives back.

### Key Takeaways

- **AI** is the broad field; **machine learning** is the part that learns from examples; **deep learning** powers today's progress; **generative AI** creates new content. Knowing which layer someone means cuts through most hype.
- Traditional software follows rules a human wrote. Machine learning **writes its own rules from examples** — which is its power and its risk.
- AI has cycled through booms and "winters" since the 1950s. The technology is real **and** the hype is real; a clear mind holds both.
- A model is only as good as its **training data.** Biased examples produce biased systems — "the algorithm decided" is never the whole story.
- Every AI project follows five stages: **define, gather, build, deploy, evaluate** — and loops back.
- Gemini is a generative-AI assistant. It **predicts plausible text**, so it can be confidently wrong. Specific prompts and human verification are non-negotiable.

### Key Terms

**Artificial intelligence (AI)** — building computer systems that perform tasks associated with human intelligence.
**Machine learning (ML)** — AI that learns patterns from examples instead of following hand-written rules.
**Deep learning** — machine learning using many-layered networks; the engine of the modern AI era.
**Generative AI** — deep-learning systems that create new text, images, audio, or video.
**Supervised learning** — learning from labelled examples (the right answers are provided).
**Unsupervised learning** — finding structure in unlabelled data, with no answers provided.
**Reinforcement learning** — learning through reward and penalty by trial and error.
**Feature** — a single piece of input information used by a model.
**Label** — the correct answer attached to a training example.
**Training data** — the collection of examples a model learns from.
**Model** — the learned pattern a system uses to make predictions.
**AI project cycle** — the five stages of an AI project: define, gather, build, deploy, evaluate.
**Large language model (LLM)** — a generative model trained on vast text to predict and produce language.
**Hallucination** — a confident, fluent, but false output from a generative AI system.
**Prompt** — the instruction a person gives an AI assistant.

### Bridge to Chapter 2

You can now use an AI assistant — and you know it can be confidently wrong. That raises the question the next chapter is built on: *how do you know what to trust at all?* Chapter 2, **Digital Literacy and Data**, is about where knowledge and data actually come from, how to judge a source, and how to give an AI assistant solid ground to stand on instead of letting it guess. You will meet **NotebookLM**, a tool that answers only from sources *you* choose — and watch it work together with the Gemini skills you just built.

---

## Apply and Analyze

The instructor-led walkthrough in Section 1.6 is the demonstration for this chapter. What follows is your turn — first to check your understanding, then to apply Gemini to a problem of your own, then to reflect.

### Review Questions

1. **What best describes the core difference between traditional software and machine learning?**
   A. Machine learning runs faster.
   B. Machine learning follows rules a programmer wrote; traditional software does not.
   C. Machine learning writes its own rules by studying examples; traditional software follows rules a human wrote.
   D. There is no real difference.

2. **Deep learning is best described as:**
   A. The whole field of artificial intelligence.
   B. A style of machine learning using many-layered networks, responsible for most modern progress.
   C. Any computer program that uses rules.
   D. A way to store training data.

3. **True or False:** An "AI winter" is a period when AI research lost funding and momentum after its promises went unmet.

4. **A team trains a model on a company's past hiring decisions, which quietly favored one group of applicants. The model then favors that same group. This is mainly an example of:**
   A. A hallucination.
   B. Bias inherited from the training data.
   C. Reinforcement learning.
   D. The AI project cycle.

5. **True or False:** Because Gemini answers confidently and fluently, a confident answer can be taken as a verified fact.

:::{dropdown} Answer Key
1. **C** — machine learning writes its own rules from examples.
2. **B** — deep learning is many-layered machine learning; it drove the post-2012 era.
3. **True** — AI winters are documented freezes in funding and interest.
4. **B** — the model inherited bias from biased training data ("bias in, bias out").
5. **False** — Gemini predicts plausible text and can be confidently wrong (a hallucination). Always verify.
:::

### Discussion Question

Think of one task in your own field, job, or daily life that you would consider handing to an AI assistant. Where exactly would the line fall between what the AI should do and what a human must still decide — and *why* would you draw it there? Refer to at least one specific idea from this chapter (for example, hallucination, training-data bias, or the role of human judgment) to support your reasoning.

### Breakout Lab: Your First Real Use Case

Work in a group of three or four. Total time: about 30–40 minutes. This is low-stakes — the goal is to *try*, not to be perfect.

1. **Pick a real problem (5 min).** Choose one small, genuine task from a group member's life, studies, or work — drafting a tricky email, building a study plan, planning an event on a budget, comparing two options.
2. **Write a strong prompt together (10 min).** Apply Section 1.6: state *who* you are, *what* you need, *how much*, and *what form* the answer should take. Write it down before you run it.
3. **Run it and refine (10 min).** Give the prompt to Gemini. Then improve the result with at least two follow-up messages.
4. **Judge the output (10 min).** As a group, mark anything that is wrong, generic, or needs a human's judgment. Identify at least one thing you would verify before trusting it.
5. **Share (5 min).** Each group reports its task, its best prompt, and the most important flaw it caught.

**Submit:** your final prompt, Gemini's final response, and three sentences on what you would still check or change. Due at the end of class.

### Optional Take-Home: Going Deeper

*Assigned at your instructor's discretion.* Extend your breakout project on your own.

- Run your group's task again, but deliberately write a **vague** prompt first, then your **strong** prompt. Describe how the two answers differ.
- Then reflect in writing (about 300 words): Did either answer contain anything misleading or biased? What in this chapter explains *why* an AI tool might produce that? If you used this AI output in real work or study, when and how would you disclose that AI helped — and who could be affected if you did not?
