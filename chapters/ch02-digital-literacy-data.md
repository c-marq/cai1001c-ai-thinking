---
title: "Chapter 2: Digital Literacy and Data"
subtitle: "Where Knowledge Comes From"
short_title: "2 · Digital Literacy & Data"
description: "What digital literacy really is; how to judge whether a source can be trusted; where data comes from and how it is collected; the Internet of Things; and grounding AI in sources you choose with NotebookLM."
label: ch-02-digital-literacy-data
tags: [foundations, digital-literacy, data-sources, iot, notebooklm]
---

<!--
FIGURE 2.1 — opening master infographic. Generated with Nano Banana Pro via generate-image.js.
Style: dense ai4educators-style master infographic, deep-teal-and-coral palette, white/pale
background, faint circuit-board margin motif. 16:9 landscape. Composition: LEFT-TO-RIGHT JOURNEY
(deliberately different from Chapter 1's hub layout) — four numbered stages joined by coral
arrows: 1 SOURCES (books, websites, sensors, people), 2 JUDGE IT (a checklist/magnifier),
3 CURATE IT (organised folder of trusted sources), 4 GROUND THE AI (a notebook feeding a
friendly assistant that answers with a citation). Title top: WHERE KNOWLEDGE COMES FROM.
Reference: fig-1-1 for palette and finish. No garbled text; short labels only.
-->

:::{figure} ../images/ch02/fig-2-1-where-knowledge-comes-from.png
:label: fig-2-1
:alt: A master infographic showing knowledge moving through four stages — gathering sources, judging them, curating the trustworthy ones, and using them to ground an AI assistant.
:width: 100%
:align: center

**Figure 2.1.** *Where knowledge comes from.* Knowledge is not something an AI simply "has." It is gathered from sources, judged, curated, and — if you do it well — used to give an AI solid ground to stand on.
:::

**Chapter 2 of 8 · Foundations**

In Chapter 1 you learned an uncomfortable fact: an AI assistant can be confidently, fluently wrong. Gemini does not look up the truth — it predicts plausible text, and plausible is not the same as true. That leaves you with a sharp question, and this chapter is built to answer it: *how do you know what to trust at all?*

It is not a small question. Every day you are handed claims — by a search result, a social feed, a coworker, a headline, and now an AI. Some are solid. Some are guesses dressed up as facts. Some are outright invented. A student once asked an AI assistant for research sources and received a tidy list, complete with authors, journals, and years — and not one of the studies existed. The AI had not lied, exactly. It had done what it does: produced text that *looked* like a citation list.

The skill that protects you here is older than AI and more important than ever. It is called **digital literacy** — the ability to find information, judge whether it can be trusted, organize it, and use it well. This chapter teaches that skill directly. Then it puts a tool in your hands — **NotebookLM** — that does something Gemini cannot: it answers *only* from sources you give it, and it shows you exactly where each answer came from.

## Learning Objectives

By the end of this chapter, you will be able to:

1. **Explain** what digital literacy is and why it is a survival skill in an age of AI.
2. **Judge** whether a source is trustworthy using a clear, repeatable set of questions.
3. **Describe** where data comes from — including the Internet of Things — and the difference between structured and unstructured data.
4. **Explain** what it means to *curate* information and to *ground* an AI in sources you choose.
5. **Use** NotebookLM to build a grounded, source-cited research notebook, and connect it to the Gemini skills from Chapter 1.

## How This Chapter Moves

We start with the skill — what digital literacy actually is, and how to judge a source without needing a degree in library science. Then we look at *data*: where it comes from, how it is collected, and how the Internet of Things turned the physical world into a firehose of it. Then we get practical — curating sources, and using NotebookLM to keep an AI honest by tying it to material you trust.

## 2.1 What Digital Literacy Really Is

People often hear "digital literacy" and picture being comfortable with apps and devices — knowing how to attach a file, join a video call, reset a password. That is *digital fluency*, and it is useful. But it is not the same thing.

**Digital literacy** is the ability to *think clearly* with digital information: to find it, judge it, organize it, and use it responsibly. It is a thinking skill, not a clicking skill. A person can be lightning-fast with every app on their phone and still fall for a fabricated statistic. Another can be slow with technology and still be a careful, hard-to-fool reader. The second person is the digitally literate one.

It helps to break the skill into four habits:

- **Find.** Locating information that is actually relevant to your question — and knowing that *where* you look shapes *what* you find.
- **Evaluate.** Judging whether what you found can be trusted. This is the heart of it, and the next section is devoted to it.
- **Organize.** Keeping track of what you have found so it is usable later — what this chapter will call *curating*.
- **Use responsibly.** Applying information honestly: crediting sources, respecting privacy, and not passing along what you have not checked.

:::{admonition} 🔍 Myth vs. Reality
:class: warning
**The myth:** "More information means better decisions."

**The reality:** Past a certain point, more information makes decisions *worse* — unless you can filter it. A nurse with three trustworthy sources on a drug interaction is in a far better position than one with forty browser tabs of mixed quality. The bottleneck in modern life is almost never *access* to information; it is *judgment* about which information deserves your trust. AI raises the stakes again: it can generate unlimited plausible-sounding text in seconds. Digital literacy is what keeps that flood from drowning you.
:::

Why does this matter enough to open a chapter with it? Because every other skill in this book sits on top of it. You cannot build a useful AI system on bad data. You cannot trust an AI's answer if you cannot judge the sources behind it. And you cannot be a responsible professional — in healthcare, business, a trade, or anything else — if you cannot tell a reliable claim from a confident guess. Digital literacy is not a soft skill. It is the foundation the rest of the building stands on.

## 2.2 Judging a Source

Here is the practical core of the chapter. When you encounter a claim — in an article, a video, a post, or an AI's answer — you can judge how much to trust it with five plain questions. You do not need to memorize a framework. You need to build a habit.

**1. Who made this, and what do they know?** Look for the author or organization. Are they identifiable? Do they have real expertise or first-hand knowledge of the topic? An anonymous post and a named specialist are not equal. *Authority matters — but it is not everything; experts are sometimes wrong, and a non-expert reporting carefully can be right.*

**2. How current is it?** Check the date. For some topics — a historical fact, a definition — age does not matter. For others — a medical guideline, a tax rule, the capabilities of an AI tool — a source from even two years ago can be dangerously out of date. Always ask: *has the world changed since this was written?*

**3. What is the evidence?** Does the claim rest on something — data, a study, a document, direct observation — or only on assertion? Can you follow the evidence to its source? "A study found" is not evidence until you can see *which* study. (Remember the invented citation list. A citation is a promise; a real one can be checked.)

**4. What is the purpose, and who benefits?** Is this trying to inform you, sell you something, or persuade you of a position? Information is rarely neutral. A claim about a product from the company selling it, or a claim about a policy from a group campaigning for it, is not worthless — but it must be read with its purpose in mind.

**5. Does it hold up elsewhere?** The single most powerful move in digital literacy: **cross-check.** Find the same claim in a second, independent source. If a surprising fact appears in only one place, treat it as unconfirmed. If three independent, credible sources agree, your confidence can rise.

:::{figure} ../images/ch02/fig-2-2-judging-a-source.png
:label: fig-2-2
:alt: A five-point checklist for judging whether a source can be trusted — who made it, how current it is, what evidence it offers, its purpose, and whether it holds up against other sources.
:width: 90%
:align: center

**Figure 2.2.** *Five questions for any source.* Not a test to pass or fail — a habit to build. Run a claim through these before you trust it, repeat it, or feed it to an AI.
:::

<!--
FIGURE 2.2 — concept infographic, card-row / checklist composition. Title: JUDGING A SOURCE.
Five stacked or rowed cards, each with an icon badge, a short heading and a one-line caption:
1 WHO MADE IT (person/badge icon), 2 HOW CURRENT (calendar icon), 3 WHAT EVIDENCE (magnifier
over a document), 4 WHAT PURPOSE (a signpost / dollar-tag), 5 DOES IT HOLD UP (two/three
documents with a check). Deep teal cards, coral icon accents and check marks, white background,
faint circuit margin motif. ai4educators master-infographic style. Reference: fig-1-1 for
palette/finish. Short labels only, no garbled text.
-->

:::{admonition} ✋ Try This
:class: tip
Pick one surprising claim you have seen online or heard from an AI in the past week. Run it through the five questions. Most claims fail at question 3 (no traceable evidence) or question 5 (you cannot find it confirmed anywhere independent). Notice how fast a weak claim falls apart once you *ask*.
:::

A note on AI specifically. When an AI assistant gives you an answer, questions 3 and 5 do the heavy lifting. *What is the evidence* — did it cite a real, checkable source, or just assert? *Does it hold up* — can you confirm the key facts somewhere independent? An AI answer is a *starting point for checking*, never the end of it. That is true of Gemini from Chapter 1, and — as you will see — it is *less* true of NotebookLM, by design.

## 2.3 Where Data Comes From

Information does not appear from nowhere, and neither does the **data** that AI systems learn from. Recall from Chapter 1 that a machine learning model is only as good as its training data. So it is worth asking plainly: where does data actually come from?

**Data** is simply recorded facts — numbers, text, images, measurements, clicks, timestamps. **Data acquisition** is the act of collecting it. It enters the world through a few main doors:

- **People entering it** — a nurse charting vital signs, a customer filling a form, a clerk logging a sale.
- **Devices sensing it** — a thermostat reading temperature, a phone recording location, a fitness band counting steps.
- **Systems logging it** — a website recording every click, a payment system recording every transaction, an app recording every tap.
- **People creating it** — every photo, post, review, and document added to the internet.

It also helps to know two broad shapes data comes in. **Structured data** is neatly organized into rows and columns, like a spreadsheet — a sales table, a patient registry. It is easy for software to work with. **Unstructured data** is everything else — the text of an email, a photograph, an audio recording, a video. It carries enormous information but takes more work to use. Most of the world's data is unstructured, which is exactly why the deep-learning breakthroughs of Chapter 1 — which finally made images and language usable — mattered so much.

```{mermaid}
graph LR
    W[The real world] --> C{How it is captured}
    C --> P[People enter it<br/>forms, charts, logs]
    C --> S[Sensors record it<br/>devices, IoT]
    C --> L[Systems log it<br/>clicks, transactions]
    P --> R[Raw data]
    S --> R
    L --> R
    R --> D[Prepared dataset<br/>cleaned and organized]
```

*Diagram 2.1. How data is acquired. The real world becomes raw data through people, sensors, and system logs — and only becomes a usable dataset after it is cleaned, the subject of Chapter 3.*

### The Internet of Things

For most of computing history, data came mainly from people typing. That changed with the **Internet of Things** — usually shortened to **IoT** — the vast and growing network of everyday physical objects that contain sensors and connect to the internet.

A smart thermostat, a delivery van with a GPS tracker, a hospital infusion pump that reports its status, a shipping container that logs its temperature, a city traffic sensor, a doorbell camera — each is a small computer, sensing the physical world and sending a stream of data about it. Billions of these devices now exist. Together they turned the physical world into something that constantly generates data.

This is genuinely transformative, and worth feeling the weight of. A logistics company can now see every truck in its fleet in real time and reroute around a jam before a delivery is late. A hospital can monitor every patient's vital signs continuously instead of every four hours, and catch a deterioration that a scheduled check would miss. A farm can water each section of a field based on its actual soil moisture rather than a guess. None of that was possible when data meant a person typing into a form. The IoT did not just add more data — it changed *what kinds of decisions are possible*.

:::{figure} ../images/ch02/fig-2-3-where-data-comes-from.png
:label: fig-2-3
:alt: A hub-and-spoke diagram showing data flowing into a central store from people, connected sensor devices, and system logs, with examples of Internet-of-Things devices.
:width: 90%
:align: center

**Figure 2.3.** *The data firehose.* People, system logs, and — increasingly — billions of connected Internet-of-Things devices all feed the data that modern AI learns from.
:::

<!--
FIGURE 2.3 — concept infographic, hub-and-spoke composition. Title: WHERE DATA COMES FROM.
Central node labelled DATA (a database/cylinder icon). Spokes to labelled source nodes:
PEOPLE (form/keyboard icon), SENSORS / IoT (a small cluster — thermostat, delivery van,
wearable, camera), SYSTEM LOGS (clicks/transaction icon), CREATED CONTENT (photo/post icon).
A small side panel headed STRUCTURED vs UNSTRUCTURED showing a tidy table beside a photo/audio
/text cluster. Deep teal nodes, coral spokes/arrows, white background, faint circuit margin
motif. ai4educators master-infographic style. Reference: fig-1-1 for palette/finish. Short
labels only, no garbled text.
-->

:::{admonition} ⚠️ Watch Out: Every sensor is also a watcher
:class: caution
The same connected device that improves a decision is also collecting data about someone. A doorbell camera deters a package thief and records every neighbor who walks past. A fitness band coaches your health and builds a minute-by-minute record of your body and movements. A delivery van's tracker optimizes routes and monitors the driver. None of this is automatically wrong — but it is never neutral. As you meet each technology in this book, ask the question this chapter trains you to ask: *what data is being collected, who holds it, and who benefits?* We return to this directly in Chapter 8.
:::

## 2.4 Curating Information

You can find information and you can judge it. The third habit — the one that turns scattered effort into real knowledge — is **curating** it.

To curate information is to deliberately gather, evaluate, and organize a set of trustworthy sources on a topic, and keep them where you can use them. A museum curator does not display every object in storage; they choose, arrange, and label the ones that matter. Curating information is the same act. Out of the ocean of available material, you select the credible and relevant pieces and bring them together.

This is more than tidiness. A well-curated set of sources is a form of knowledge in itself — and, as you are about to see, it is the key to using AI well. Here is the connection. An AI assistant like Gemini answers from the vast, messy, unlabeled mixture it was trained on; that is why it can drift into a confident guess. But if you could hand an AI a *curated* set of sources you have already judged and trusted, and require it to answer *only* from those — then its answers would be anchored to ground you chose. That anchoring has a name: **grounding.** And it is exactly what the tool in this chapter does.

## 2.5 Meet NotebookLM: An AI That Cites Its Sources

**NotebookLM** is a research assistant made by Google. It is built on the same kind of large language model as Gemini — but it is pointed at a fundamentally different job.

Recall the contrast. Gemini draws on everything it was trained on and predicts a plausible answer; it is broad, creative, and capable of hallucinating. **NotebookLM works only from sources *you* give it.** You create a "notebook" and add your sources — PDFs, documents, websites, even videos. From that point on, NotebookLM answers your questions *using only that material*, and — this is the part that matters most — **every answer comes with citations** that point to the exact place in your sources it came from. You can click a citation and land on the sentence that backs the claim.

This is grounding made real. NotebookLM is not smarter than Gemini. It is *more constrained* — and for research, that constraint is the feature. If the answer is not in your sources, a well-behaved NotebookLM tells you so rather than inventing one.

:::{admonition} 🔍 Myth vs. Reality
:class: warning
**The myth:** "NotebookLM can't hallucinate, so its answers are guaranteed true."

**The reality:** Grounding solves *one* problem, not all of them. NotebookLM is far less likely to invent facts, because it answers from your sources and shows its citations — you can check every claim against the original. But it cannot tell you that a source you gave it is *wrong, biased, or out of date.* If you feed it three unreliable articles, it will faithfully, with citations, summarize unreliable information. Grounding moves the responsibility to where it belongs: on **your** judgment of the sources. Which is exactly why Section 2.2 came first.
:::

As of **May 2026**, NotebookLM is **free** with a Google account and available to anyone **13 or older** — so every student can use it directly. It runs in a web browser and as a mobile app. A free notebook holds up to 50 sources, which is far more than enough for any assignment in this course.

:::{figure} ../images/ch02/fig-2-4-grounded-answers.png
:label: fig-2-4
:alt: A before-and-after comparison — an ungrounded assistant producing a confident answer with no sources, versus a grounded assistant answering from chosen sources with clickable citations.
:width: 90%
:align: center

**Figure 2.4.** *Ungrounded versus grounded.* A general assistant predicts a plausible answer from everything it has seen. A grounded assistant answers only from the sources you gave it — and cites them.
:::

<!--
FIGURE 2.4 — concept infographic, before/after composition. Title: TWO KINDS OF ANSWER.
LEFT panel "UNGROUNDED": a question going into a cloud-brain that outputs a confident answer
card with a small coral warning pill "NO SOURCES — COULD BE WRONG". RIGHT panel "GROUNDED":
the same question plus a small stack of source documents going into an assistant that outputs
an answer card with little numbered citation chips linking back to the sources; a teal pill
"ANSWERED FROM YOUR SOURCES". Central coral arrow or divider. Deep teal, coral accents, white
background, faint circuit margin motif. ai4educators master-infographic style. Reference:
fig-1-1 for palette/finish. Short labels only, no garbled text.
-->

## 2.6 Hands-On Walkthrough: Research That Cites Its Sources

This is the walkthrough your instructor will demonstrate before you try it in the lab.

> **Verified as of May 2026.** If a screen looks different, the idea still holds — find the equivalent control.

**Step 1 — Open and sign in.** Go to **notebooklm.google.com** and sign in with a Google account. Click **Create new** (or **New notebook**).

**Step 2 — Add your sources.** This is the most important step, and Section 2.2 is what makes you good at it. In the **Sources** panel, add material you have judged to be trustworthy — upload PDFs, link a document, paste a web address, even add a video. The quality of everything that follows is set right here. *Curate before you add.*

**Step 3 — Ask questions in the Chat panel.** Ask in plain language: *"What are the main causes this report identifies?"* or *"Summarize the safety steps across all three documents."* Each answer arrives with **numbered citations.** Click one — it takes you to the exact passage in the source. Get into the habit of clicking them; that click is you doing question 3 from Section 2.2 in one second.

**Step 4 — Use the Studio panel.** NotebookLM can turn your sources into study and review materials — a written briefing, a set of flashcards, a quiz, a mind map, and even an **Audio Overview**, a podcast-style discussion of your sources you can listen to while commuting. These are generated from *your* curated sources, so they stay on topic.

**Step 5 — Notice what it will not do.** Ask NotebookLM something your sources do not cover. A well-behaved notebook will tell you the answer is not in the material rather than invent one. That refusal is the tool working correctly — and it is the behavior Chapter 1's Gemini does not have.

### Working With Chapter 1: NotebookLM and Gemini Together

The two tools are strongest as a pair, and the handoff between them is a workflow you will use all term.

Suppose you are preparing a report on a topic. **First, research with NotebookLM:** gather five or six sources you have judged credible, add them to a notebook, and ask questions until you understand the material — every answer cited, every claim checkable. **Then, hand the grounded findings to Gemini:** take what you have confirmed and ask Gemini, with its broader drafting skill, to help you outline and write. NotebookLM keeps the *facts* honest; Gemini helps shape the *writing*. Research grounded, then drafted — that is the pattern.

### Other Use Cases

- **Healthcare student:** load your assigned readings and lecture notes into one notebook; ask it to explain a hard concept and generate a practice quiz — all cited to your actual course material.
- **Small-business owner:** drop in three vendor contracts and ask for a plain comparison of the cancellation terms, each point traceable to the contract it came from.
- **Skilled trades:** load an equipment manual and a safety standard; ask for the exact procedure for a task, with citations to the page.
- **Anyone facing a dense document:** a lease, a benefits packet, a policy — add it and ask plain questions instead of guessing.

:::{dropdown} 🔎 Going Deeper: Why "grounding" is a big deal beyond this one app
The idea behind NotebookLM — make an AI answer from a specific, trusted set of documents instead of from its general training — is one of the most important patterns in AI right now. In industry it is often called *retrieval-augmented generation*, and you do not need the jargon, only the idea: pair a language model with a trusted library, and make it answer from the library.

It is how a company builds an AI help desk that answers only from its real policies, how a hospital builds an assistant that responds only from its approved clinical guidelines, and how a law firm builds a tool that cites only the actual case files. The reason is always the same one this chapter is about: an ungrounded model is fluent but unaccountable; a grounded one can be checked. As AI moves into serious, high-stakes work, grounding is how it earns the right to be there.
:::

:::{admonition} ⚖️ Ethics Check: Grounding does not retire your judgment
:class: important
1. **You still own the sources.** NotebookLM will faithfully summarize whatever you give it. Garbage sources produce well-cited garbage. The five questions in Section 2.2 are not optional homework — they are the real work.
2. **Mind what you upload.** Sources you add are processed by the service. Do not upload other people's private documents — a patient's records, a colleague's file, confidential business material — into a personal AI tool.
3. **Citations are a promise, not a guarantee.** A citation tells you *where* a claim came from, not that the claim is *correct.* Click through. Read the original. The tool points at the evidence; weighing it is still yours to do.
:::

## Chapter Summary

The hard problem of the information age is not finding information — it is judging it. **Digital literacy** is the skill that does that: finding, evaluating, organizing, and responsibly using information. You can judge almost any source or AI answer with five plain questions — who made it, how current it is, what evidence backs it, what its purpose is, and whether it holds up against independent sources. **Data** enters the world through people, sensors, system logs, and created content, and the **Internet of Things** has turned the physical world itself into a constant data source. **Curating** trustworthy sources lets you **ground** an AI in material you have chosen — and **NotebookLM** does exactly that, answering only from your sources and citing every claim. Grounding does not remove your responsibility; it focuses it on the judgment you now know how to apply.

### Key Takeaways

- **Digital literacy** is a thinking skill — finding, evaluating, organizing, and responsibly using information — not the same as being quick with apps.
- Judge any source or AI answer with five questions: **who, how current, what evidence, what purpose, does it hold up.** Cross-checking is the most powerful move.
- **Data** comes from people, sensors, system logs, and created content; it is **structured** (tables) or **unstructured** (text, images, audio, video).
- The **Internet of Things** turned billions of everyday objects into sensors, changing what decisions are possible — and what is being watched.
- **Curating** sources lets you **ground** an AI. **NotebookLM** answers only from sources you provide and cites them — far less prone to hallucination, but only as trustworthy as the sources you chose.
- NotebookLM and Gemini work best together: **research grounded in NotebookLM, then draft with Gemini.**

### Key Terms

**Digital literacy** — the ability to find, evaluate, organize, and responsibly use information.
**Source evaluation** — judging whether information can be trusted, using questions of authority, currency, evidence, purpose, and corroboration.
**Cross-checking** — confirming a claim against a second, independent, credible source.
**Data** — recorded facts: numbers, text, images, measurements, and more.
**Data acquisition** — the process of collecting data.
**Structured data** — data organized into rows and columns, like a spreadsheet.
**Unstructured data** — data with no fixed format, such as text, images, audio, and video.
**Internet of Things (IoT)** — the network of everyday physical objects with sensors that connect to the internet and generate data.
**Curating** — deliberately gathering, evaluating, and organizing a trustworthy set of sources.
**Grounding** — requiring an AI to answer only from a specific, chosen set of sources.
**NotebookLM** — a Google research assistant that answers only from sources you provide and cites them.
**Citation** — a pointer to the exact source and place a claim came from.

### Bridge to Chapter 3

You can now find trustworthy information, judge it, and ground an AI in it. But raw data — even good data — is rarely ready to use. It arrives messy: missing entries, inconsistent formats, errors, duplication. Chapter 3, **Working with Data**, is about turning that raw material into something you can actually learn from — exploring it, cleaning it, and visualizing it so it tells the truth rather than a flattering story. You will meet tools that let you do this without writing code, and you will see the workflow that carries a dataset all the way to a model.

---

## Apply and Analyze

The instructor-led walkthrough in Section 2.6 is the demonstration for this chapter. What follows is your turn — to check your understanding, apply NotebookLM to sources of your own, and reflect.

### Review Questions

1. **Digital literacy is best described as:**
   A. Knowing how to use apps and devices quickly.
   B. The ability to find, evaluate, organize, and responsibly use information.
   C. The ability to write computer code.
   D. Owning the latest technology.

2. **You read a surprising health claim that cites "a recent study" but names no study you can locate, and you cannot find the claim confirmed anywhere else. Which two source-evaluation questions has it most clearly failed?**
   A. Who made it, and how current it is.
   B. What evidence backs it, and whether it holds up against independent sources.
   C. What its purpose is, and who made it.
   D. It has failed none — a confident claim is enough.

3. **True or False:** A patient's continuously transmitting heart monitor is an example of an Internet of Things device.

4. **What does it mean to "ground" an AI assistant?**
   A. To run it on a local computer instead of the internet.
   B. To require it to answer only from a specific set of sources you provide.
   C. To make it respond more quickly.
   D. To stop it from being used at all.

5. **True or False:** Because NotebookLM cites its sources, its answers are guaranteed to be accurate and unbiased.

:::{dropdown} Answer Key
1. **B** — digital literacy is the thinking skill of finding, evaluating, organizing, and using information.
2. **B** — no traceable evidence (question 3) and no independent corroboration (question 5).
3. **True** — it is a sensor-equipped physical object connected to the internet, generating data.
4. **B** — grounding means requiring the AI to answer only from sources you provide.
5. **False** — citations show *where* a claim came from, not that it is correct; NotebookLM is only as trustworthy as the sources you chose.
:::

### Discussion Question

Think about how you personally decided what was true the last time you researched something important — a purchase, a health question, a news event. Which of the five source-evaluation questions did you actually use, and which did you skip? Now that AI assistants can generate unlimited confident-sounding text, which of the five do you think becomes the *most* important, and why? Support your answer with at least one specific idea from this chapter.

### Breakout Lab: Build a Grounded Notebook

Work in a group of three or four. Total time: about 35–45 minutes. Low-stakes — the goal is to *do it*, not to be perfect.

1. **Choose a question (5 min).** As a group, pick one real research question from a member's field, studies, or life — a question with a genuine answer, not an opinion.
2. **Curate four to six sources (15 min).** Find sources together, and run each one through the five questions from Section 2.2 *before* you accept it. Keep only the ones that pass. Write one sentence per source on why you trust it.
3. **Build the notebook (10 min).** Create a NotebookLM notebook, add your chosen sources, and ask it at least three questions about your topic. Click the citations.
4. **Test its honesty (5 min).** Ask NotebookLM one question your sources do *not* cover. Note what it does.
5. **Share (5 min).** Each group reports its question, how many candidate sources it rejected and why, and what happened in step 4.

**Submit:** your research question, your list of accepted sources with the one-sentence reason for each, and three sentences on what NotebookLM did when asked something outside its sources. Due at the end of class.

### Optional Take-Home: Going Deeper

*Assigned at your instructor's discretion.* Extend your group's notebook on your own.

- Deliberately add one **weak** source to your notebook — something that fails the Section 2.2 questions — and ask NotebookLM a question it would influence. Describe what happens to the answer.
- Then reflect in writing (about 300 words): NotebookLM grounded its answer in your sources and cited them — but did grounding make the answer *trustworthy*? Whose judgment was actually responsible for the result? Could a curated source set still be biased even if every source in it is individually "credible" — for example, if all of them share the same viewpoint? How would you guard against that?
