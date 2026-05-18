---
title: "Chapter 3: Working with Data"
subtitle: "Turning Numbers Into Insight"
short_title: "3 · Working with Data"
description: "Exploring, cleaning, and transforming raw data; visualizing it honestly; spotting charts that mislead; and how prepared data feeds a model — with a hands-on Datawrapper walkthrough."
label: ch-03-working-with-data
tags: [foundations, data, data-cleaning, data-visualization, datawrapper]
---

<!--
FIGURE 3.1 — opening master infographic. Generated with Nano Banana Pro via generate-image.js.
Style: dense ai4educators-style master infographic, deep-teal-and-coral palette, white/pale
background, faint circuit-board margin motif. 16:9 landscape. Composition: ASCENDING LAYERED
STAIRCASE (deliberately different from Ch1's hub and Ch2's left-to-right journey) — five rising
steps, each a labelled tier with a small icon, climbing left-to-low to right-to-high:
1 RAW DATA (messy spreadsheet), 2 EXPLORE (magnifier), 3 CLEAN (broom/sparkle), 4 TRANSFORM
(gears reshaping a column), 5 VISUALIZE (a bar chart). At the top of the staircase a glowing
coral badge labelled INSIGHT. Title top: TURNING NUMBERS INTO INSIGHT. Reference: fig-1-1 for
palette and finish. No garbled text; short labels only.
-->

:::{figure} ../images/ch03/fig-3-1-turning-numbers-into-insight.png
:label: fig-3-1
:alt: A master infographic showing data climbing a five-step staircase — raw data, explore, clean, transform, visualize — and arriving at insight.
:width: 100%
:align: center

**Figure 3.1.** *Turning numbers into insight.* Raw data is not insight. It becomes insight by climbing a staircase: explore it, clean it, transform it, and visualize it honestly.
:::

**Chapter 3 of 8 · Foundations**

There is a comforting belief about data, and it is wrong. The belief is that data is objective — that numbers are clean, neutral facts, and that once you "have the data," the truth is simply *in there*, waiting. It is a belief worth dismantling early, because almost everything in the rest of this book depends on dismantling it.

Here is the reality. Raw data arrives messy: entries missing, dates in three different formats, a price typed as 450 when it should be 4.50, the same customer listed twice under two spellings of their name. And even when every number is correct, a chart built from those numbers can still tell a flat lie — not by inventing data, but by *framing* it. Two honest charts of the very same figures can leave two people with opposite impressions of what happened.

So data does not hand you the truth. It hands you raw material. Turning that raw material into something trustworthy — into *insight* — is real work, and it is the work this chapter teaches. Recall the AI project cycle from Chapter 1: the stage called "gather and prepare data" is where teams spend most of their time, often well over half a project. This chapter is that stage, up close.

You will explore data, clean it, transform it, and visualize it — and you will learn to spot a chart that misleads. Your hands-on tool is **Datawrapper**, a free, no-sign-up tool for building honest charts. Your instructor will also demonstrate **Google AI Studio**, a developer's view of putting AI to work on data.

## Learning Objectives

By the end of this chapter, you will be able to:

1. **Explore** an unfamiliar dataset to understand its size, shape, and quality before using it.
2. **Identify** common data problems — missing values, errors, duplicates, inconsistent formats — and explain how to clean them.
3. **Explain** what it means to *transform* data and why new, derived columns make data more useful.
4. **Choose** an appropriate chart for a question, and **detect** the techniques that make a chart mislead.
5. **Use** Datawrapper to turn a real dataset into a clear, honest visualization.

## How This Chapter Moves

We follow the staircase in Figure 3.1, one step at a time: first *explore* (get to know the data), then *clean* (fix what is wrong), then *transform* (reshape it to be more useful), then *visualize* (make it speak). Along the way we stop on the most important defensive skill of the chapter — reading a chart critically — and then you build one yourself.

## 3.1 Getting to Know Your Data

Before you clean, transform, or chart anything, you do something quieter and more important: you *look*. **Data exploration** is the unglamorous, essential first step of getting to know a dataset before you trust it for anything.

Imagine a small coffee shop hands you a file of last year's daily sales and asks, "Are we growing?" Before you can answer, you need to know what you are holding. Exploring it means asking plain questions:

- **How big is it?** How many rows (records) and columns (fields)? A year of daily sales should have about 365 rows. If it has 300, eleven weeks are missing — and that changes every conclusion.
- **What is in each column?** What does each field mean, and what type of value is it — a number, a date, a category, a piece of text?
- **What is the range?** What are the smallest and largest values? A daily-sales column running from \$0 to \$4,200 is plausible. One with a value of \$450,000 has an error in it, or a story you need to hear.
- **What is missing?** Which entries are blank? Missing data is not nothing — it is a question. *Why* is it missing?
- **What looks strange?** Duplicated rows, impossible values (a date of February 30th), a category spelled four different ways.

Exploration is not busywork. It is how you avoid the most common and most embarrassing mistake in all of data work: confidently answering a question with a dataset that could never have answered it. You explore so that you are never surprised later.

:::{admonition} 🔍 Myth vs. Reality
:class: warning
**The myth:** "The data speaks for itself."

**The reality:** Data never speaks for itself. *Someone* decided what to record and what to ignore, how to define each category, and what to do about the awkward cases. Those decisions are baked into every dataset before you ever open it. Exploring data is partly about counting rows — and partly about uncovering the human choices already inside it. A dataset is a record of what someone *chose* to measure.
:::

## 3.2 Cleaning Data

Once you know what is wrong, you fix it. **Data cleaning** is the work of correcting errors and inconsistencies so the data can be trusted. It is the single most time-consuming step in most data and AI projects, and Chapter 1 already told you why it matters: garbage in, garbage out. A model — or a chart — built on dirty data produces confident nonsense.

Four problems come up again and again.

**Missing values.** Blank entries. You have choices, and the choice matters: you can remove the incomplete records, fill the blanks with a reasonable estimate (such as the average), or — often best — find out *why* they are missing. If the coffee shop's sales are blank every Sunday because it is closed, those blanks are not errors at all; they are information.

**Errors.** Values that are simply wrong — the \$450,000 sales day, the price typed as 450 instead of 4.50, a customer age of 200. Exploration flags them; cleaning corrects them or, if they cannot be corrected, removes them honestly.

**Duplicates.** The same record entered twice. Duplicates quietly distort every total and average. They often hide behind small differences — "Maria Lopez" and "maria lopez " with a trailing space read as two different people to a computer.

**Inconsistent formats.** The same thing recorded different ways: dates as `01/02/2026`, `Jan 2`, and `2026-01-02`; a category written as "Large," "large," and "LG." A human sees one thing; software sees three. Cleaning makes them consistent.

:::{figure} ../images/ch03/fig-3-2-messy-vs-clean.png
:label: fig-3-2
:alt: A before-and-after comparison of a dataset — a messy table with blanks, a typo, a duplicate row, and mixed date formats, beside the same table cleaned and consistent.
:width: 90%
:align: center

**Figure 3.2.** *Before and after cleaning.* The same data, made trustworthy — blanks resolved, an error corrected, a duplicate removed, formats made consistent.
:::

<!--
FIGURE 3.2 — concept infographic, before/after composition. Title: CLEANING DATA. Two side-by-side
panels with a central coral arrow. LEFT panel header "MESSY": a small spreadsheet table with a few
cells visibly flagged in coral — a blank cell, a wrong value, a duplicated row, a date in a
different format. RIGHT panel header "CLEAN": the same table tidy and consistent, the flagged
cells now corrected and marked with small teal checks. A footer banner: "GARBAGE IN, GARBAGE OUT".
Deep teal, coral accents, white panels, faint circuit margin motif. ai4educators master-infographic
style. Reference: fig-1-1 for palette/finish. Short labels only, no garbled text.
-->

:::{admonition} ⚠️ Watch Out: Cleaning is also a set of decisions
:class: caution
Every cleaning choice is a judgment call, and judgment calls can change the answer. If you delete every record with a missing value, and those records belong mostly to one neighborhood or one group of customers, you have just quietly erased that group from your results — and any chart or model built afterward will be blind to them. Cleaning is necessary, but it is never neutral. Write down what you changed and why, so the decisions stay visible instead of hiding inside a "clean" file.
:::

## 3.3 Transforming Data

Clean data is trustworthy, but it is not always *useful* in the form it arrives. **Data transformation** is reshaping data — and especially *adding* to it — so it can answer the question you actually have.

The most powerful move is creating a new column from existing ones. The coffee shop's file has a date for every day. A date alone is hard to reason about. But from that one column you can *derive* others:

- A **day-of-week** column ("Monday," "Tuesday"…) — now you can compare weekdays to weekends.
- A **month** column — now you can see seasonal patterns.
- A **weekly total** by grouping the daily rows — now the long-term trend is visible without the daily noise.

Nothing new was measured. Yet the data can now answer questions it could not answer five minutes ago. That is transformation: the same facts, reorganized into a more revealing shape.

Two transformations you will use constantly:

- **Grouping and summarizing** — collapsing many rows into one summary, such as turning 365 daily rows into 52 weekly totals or 12 monthly averages.
- **Filtering** — keeping only the rows relevant to your question, such as only this year, or only weekends.

There is also a deeper reason transformation matters, and it points straight at the next chapter. Recall *features* from Chapter 1 — the individual pieces of input a machine learning model learns from. The derived columns you create here — day-of-week, month, weekly total — are exactly the kind of features a model needs. Good feature-making *is* skilled data transformation. When you reshape data well, you are not only making a clearer chart; you are preparing the raw material for the models you will meet in Chapter 4.

```{mermaid}
graph LR
    R[Clean data] --> T[Transform<br/>derive new columns]
    T --> V[Visualize<br/>a clear, honest chart]
    T --> F[Features<br/>input for a model]
    V --> I[Insight for a human]
    F --> M[A model — Chapter 4]
```

*Diagram 3.1. Two destinations for well-prepared data. Transformed data feeds a human (through a chart) and feeds a machine (through features). This chapter walks the top path; Chapter 4 walks the bottom one.*

## 3.4 Visualizing Data Honestly

A table of numbers hides its own patterns. The human eye is extraordinary at seeing shape, trend, and outlier — but only when numbers are turned into a picture. **Data visualization** is that translation: turning numbers into a chart so a person can *see* what the data is doing.

The whole skill comes down to one question: **what do you want the reader to understand?** Match the chart to that, not to what looks impressive.

- To **compare amounts** across categories — sales by product, visits by location — use a **bar chart.**
- To show **change over time** — daily sales across a year — use a **line chart.**
- To show **how parts make up a whole** — use a pie chart *sparingly*, and only with a few slices; a bar chart is usually clearer.
- To show a **relationship between two numbers** — study hours versus exam score — use a **scatter plot.**
- To show data **by geography** — use a **map.**

:::{figure} ../images/ch03/fig-3-3-choosing-a-chart.png
:label: fig-3-3
:alt: A gallery of chart types matched to their best use — bar chart for comparison, line chart for change over time, scatter plot for relationships, and a map for geography.
:width: 90%
:align: center

**Figure 3.3.** *Match the chart to the question.* The right chart is the one that makes your specific point easiest to see. Start from the question, then choose.
:::

<!--
FIGURE 3.3 — concept infographic, card-grid / gallery composition. Title: CHOOSING THE RIGHT CHART.
Four titled cards in a grid, each showing a small clean mock chart and a one-line "use it for"
caption: CARD 1 BAR CHART (mock bar chart) - "compare amounts"; CARD 2 LINE CHART (mock line) -
"change over time"; CARD 3 SCATTER PLOT (mock dot scatter) - "a relationship"; CARD 4 MAP (simple
region map with shaded areas) - "by geography". Deep teal cards and chart shapes, warm coral
accents and data highlights, white interiors, faint circuit margin motif. ai4educators
master-infographic style. Reference: fig-1-1 for palette/finish. Short labels only, no garbled text.
-->

A good chart also does the quiet things right: it has a clear title that states the point, labelled axes, a sensible scale, and no decoration that does not carry information. The goal is never to look clever. The goal is for a busy reader to glance at it and understand the truth in three seconds.

## 3.5 How a Chart Misleads

Here is the defensive skill — the one that connects this chapter back to digital literacy in Chapter 2. A chart can be built entirely from accurate numbers and still leave you believing something false. Knowing the common tricks protects you as a reader, and keeps you honest as a maker.

**The truncated axis.** A bar or line chart whose vertical axis does not start at zero. A change from 102 to 105 can be made to look like an enormous surge if the axis runs from 100 to 106. Every bar's *height* is exaggerated. Always check where the axis starts.

**The cherry-picked range.** Showing only the slice of time that supports a story. A company's sales might be down sharply over five years — but a chart of just the last three months, during a small uptick, tells the opposite tale. Ask: *why does the timeline start and end exactly there?*

**The wrong chart type.** A pie chart with twelve nearly equal slices, where no one can tell which is biggest. A line chart connecting categories that have no order. The wrong chart type buries the point — sometimes by accident, sometimes not.

**Missing context.** A number with nothing to compare it to. "Complaints rose to 240 this year" means nothing without last year's figure, or the total number of customers. A chart that omits the comparison omits the truth.

:::{figure} ../images/ch03/fig-3-4-how-a-chart-misleads.png
:label: fig-3-4
:alt: A single chart annotated with warning flags pointing at four misleading techniques — a truncated axis, a cherry-picked time range, a wrong chart type, and missing context.
:width: 90%
:align: center

**Figure 3.4.** *Spot the tricks.* Four ways an accurate set of numbers can still produce a dishonest chart. A careful reader checks for each one.
:::

<!--
FIGURE 3.4 — concept infographic, "deconstruct the trick" composition. Title: HOW A CHART MISLEADS.
A central mock chart drawn as deliberately misleading, with four coral warning-flag callouts
pointing inward at the problems, each flag with a short label: "TRUNCATED AXIS" (flag pointing at
a y-axis that starts high, not zero), "CHERRY-PICKED RANGE" (flag at a short slice of the
timeline), "WRONG CHART TYPE" (flag at a cluttered pie of equal slices shown small), "MISSING
CONTEXT" (flag at a lone number with no comparison). Deep teal chart and panels, warm coral
warning flags and accents, white background, faint circuit margin motif. ai4educators
master-infographic style. Reference: fig-1-1 for palette/finish. Short labels only, no garbled text.
-->

:::{admonition} ⚖️ Ethics Check: A misleading chart is a quiet lie
:class: important
Every number in a chart can be accurate while the chart as a whole deceives. That makes a misleading chart one of the most respectable-looking forms of dishonesty there is — it wears the costume of objectivity. When you *make* charts — in a class, a job, a community report — you hold real power over what other people will believe. Use it straight: start axes at zero unless you have a clear reason not to and you say so, show the full relevant time range, choose the chart that reveals rather than buries, and give every number its context. Honesty in a chart is not a style preference. It is a duty to your reader.
:::

## 3.6 Hands-On Walkthrough: Building an Honest Chart

This is the walkthrough your instructor will demonstrate before you try it in the lab. Your hands-on tool is **Datawrapper** — a free, browser-based tool for building clear charts, used by newsrooms and analysts worldwide.

> **Verified as of May 2026.** If a screen looks different, the idea still holds — find the equivalent control.

**Step 1 — Open Datawrapper.** Go to **datawrapper.de** and click to create a new chart. You can begin building **without creating an account** — an account is only needed to save and revisit your work later.

**Step 2 — Add your data.** Paste or upload your data as a simple table — for the demo, the coffee shop's cleaned monthly sales. Everything you learned about exploring and cleaning matters here: Datawrapper will faithfully chart whatever you give it, mess and all.

**Step 3 — Check and describe.** Datawrapper shows your data and lets you confirm what each column is — a date, a number, a category. This is a small built-in *exploration* step. Catch any problem now.

**Step 4 — Choose the chart.** Pick a chart type. Apply Section 3.4: for monthly sales over a year, a **line chart** shows the trend. Datawrapper previews it instantly.

**Step 5 — Make it honest and clear.** Give the chart a real title that states the point ("Monthly sales rose 18% over 2025," not "Sales Chart"). Confirm the axis starts at zero. Label clearly. Remove clutter.

**Step 6 — Publish or export.** Datawrapper produces a clean image or an interactive chart you can share or embed. Done — numbers turned into honest insight.

:::{admonition} 🛠️ In Practice: Instructor demo — Google AI Studio
:class: note
Your instructor will also demonstrate **Google AI Studio** (`aistudio.google.com`), a free *developer playground* for working with Google's AI models. It shows a side of AI the Gemini chat box hides: a **system instruction** that fixes the AI's role ("You are a careful data analyst; never guess a missing value"), and **structured output**, which forces the AI to return clean, table-ready data instead of loose prose — a genuine data-cleaning aid.

**Important:** Google AI Studio requires users to be **18 or older**, so it is a *demonstration only* — not a graded student task. For your own hands-on work, use Datawrapper (any age, no account). If you want AI help thinking through a dataset, the Gemini skills from Chapter 1 (you can upload a file and ask questions) are available to everyone 13 and older.
:::

### Working With Earlier Chapters

The workflow now spans three chapters. In Chapter 2 you learned to find trustworthy *sources* of data. In this chapter you explore, clean, transform, and chart it. And the Gemini and NotebookLM skills still apply: ask Gemini to suggest which chart fits your question, or to explain an unfamiliar column — then judge its answer with the eye this chapter gave you. The tools assist; the data judgment is yours.

### Other Use Cases

- **Healthcare:** chart monthly patient-visit volume to plan staffing; clean a registry before anyone trusts it.
- **Business:** turn a year of messy sales records into one honest trend line for a meeting.
- **Skilled trades:** track job durations or material costs over time to bid future work more accurately.
- **Community work:** visualize a food pantry's monthly demand to make the case for funding — honestly.
- **Students:** chart your own study hours against exam scores and see whether the relationship is what you assumed.

:::{dropdown} 🔎 Going Deeper: The 80% nobody photographs
There is a well-worn saying among data professionals: data work is 80% cleaning and 20% everything else. The exact number varies, but every experienced analyst recognizes the shape of it.

This is worth knowing for an honest reason. The glamorous image of AI and data work — the clever model, the striking chart — is the small, final 20%. The other 80% is what this chapter is really about: tracking down why eleven weeks are missing, reconciling three date formats, deciding what to do about the impossible value. It is patient, detailed, and invisible in the finished product.

If you ever do this work and it feels slow and unglamorous, you are not doing it wrong. You are doing the part that actually determines whether the result can be trusted. The model gets the photograph. The cleaning earns the truth.
:::

## Chapter Summary

Data is not objective truth handed to you ready-made — it is messy raw material. Turning it into insight means climbing a staircase. You **explore** it to learn its size, shape, and quality. You **clean** it — fixing missing values, errors, duplicates, and inconsistent formats — knowing every cleaning choice is a judgment that can change the answer. You **transform** it, deriving new columns that let it answer questions it could not before, and those derived columns double as the *features* a model will need. You **visualize** it, matching the chart to the question — and you stay alert to the truncated axes, cherry-picked ranges, wrong chart types, and missing context that let an accurate set of numbers tell a lie. With Datawrapper, you turned a real dataset into an honest chart yourself.

### Key Takeaways

- Raw data is messy and never neutral; someone already chose what to measure. **Explore** a dataset before trusting it.
- **Cleaning** fixes missing values, errors, duplicates, and inconsistent formats — and every cleaning decision can change the result, so record it.
- **Transforming** data — especially deriving new columns — lets it answer new questions, and produces the **features** a model learns from.
- Match the chart to the question: **bar** to compare, **line** for change over time, **scatter** for a relationship, **map** for geography.
- A chart of accurate numbers can still mislead — through a **truncated axis, cherry-picked range, wrong chart type,** or **missing context.** Read every chart defensively; build yours honestly.
- **Datawrapper** builds clear charts free, with no account. Google **AI Studio** is an 18+ instructor demo, not a student task.

### Key Terms

**Data exploration** — examining a dataset's size, shape, and quality before using it.
**Data cleaning** — correcting errors and inconsistencies so data can be trusted.
**Missing value** — a blank entry where a value was expected.
**Duplicate** — the same record entered more than once.
**Data transformation** — reshaping data, especially deriving new columns, to make it more useful.
**Derived column** — a new column calculated from existing ones (such as day-of-week from a date).
**Grouping and summarizing** — collapsing many rows into summary figures.
**Filtering** — keeping only the rows relevant to a question.
**Data visualization** — turning numbers into a chart so a person can see the pattern.
**Truncated axis** — a chart axis that does not start at zero, exaggerating differences.
**Cherry-picked range** — showing only the slice of data that supports a chosen story.
**Datawrapper** — a free, browser-based tool for building clear, honest charts.

### Bridge to Chapter 4

You can now take raw data and turn it into something trustworthy and clear — and you saw, in Section 3.3, that the derived columns you build are exactly the *features* a model learns from. That is the doorway to Chapter 4, **Machine Learning**. So far, *you* have done the analysis — exploring, judging, charting. Next, you hand prepared data to a machine and let it find the patterns itself. You will learn how machines classify and predict, meet the major algorithms in plain language, and — with **Teachable Machine** — train a working model with your own examples and no code at all.

---

## Apply and Analyze

The instructor-led walkthrough in Section 3.6 is the demonstration for this chapter. What follows is your turn — to check your understanding, build an honest chart of your own, and reflect.

### Review Questions

1. **Why do you *explore* a dataset before using it?**
   A. To make the file smaller.
   B. To understand its size, shape, and quality so you are not surprised by it later.
   C. To delete columns you do not like.
   D. Exploration is optional and usually skipped.

2. **A sales file lists "Maria Lopez" and "maria lopez " (with a trailing space) as separate customers. This is an example of:**
   A. A missing value.
   B. A transformation.
   C. A duplicate hidden by inconsistent formatting.
   D. A truncated axis.

3. **True or False:** Creating a "day-of-week" column from an existing date column is an example of data transformation.

4. **A bar chart's vertical axis runs from 100 to 106 instead of starting at 0, making a small change look dramatic. This misleading technique is called:**
   A. A cherry-picked range.
   B. A truncated axis.
   C. Missing context.
   D. A duplicate.

5. **True or False:** Because every number in a chart is accurate, the chart cannot be misleading.

:::{dropdown} Answer Key
1. **B** — exploration reveals a dataset's size, shape, and quality before you rely on it.
2. **C** — a duplicate hidden by an inconsistent format (the trailing space).
3. **True** — deriving a new column from an existing one is transformation.
4. **B** — an axis that does not start at zero is a truncated axis.
5. **False** — accurate numbers can still mislead through framing, such as a truncated axis or missing context.
:::

### Discussion Question

Find a chart in the wild this week — in a news article, an advertisement, a social-media post, or a report. Examine it with Section 3.5 in mind. Does it start its axis at zero? Does it show the full relevant time range? Is it the right chart type? Does it give its numbers context? Describe one specific thing the chart does well or poorly, and explain how a reader could be misled — or correctly informed — as a result. Reference at least one idea from this chapter.

### Breakout Lab: Build an Honest Chart

Work in a group of three or four. Total time: about 35–45 minutes. Low-stakes — the goal is to *do it*.

1. **Get a small dataset (10 min).** Use a real one a group member has access to (study hours, work logs, a club's attendance, monthly expenses) or a small public dataset. It should have at least one date or category column and one number column.
2. **Explore and clean it together (10 min).** Apply Section 3.1 and 3.2. Note its size and columns. Find at least one problem — a blank, an error, a duplicate, an inconsistent format — and decide as a group how to handle it. Write down the decision.
3. **Build the chart in Datawrapper (10 min).** Choose the chart type that fits your question (Section 3.4). Give it an honest, point-stating title. Confirm the axis starts at zero.
4. **Stress-test it (5 min).** Look at your own chart with Section 3.5 in hand. Could anyone accuse it of misleading? Fix it if so.
5. **Share (5 min).** Each group shows its chart, names the data problem it found and how it handled it, and states the chart's one-sentence point.

**Submit:** your finished chart, one sentence on the data problem you found and your decision, and one sentence on the chart's main point. Due at the end of class.

### Optional Take-Home: Going Deeper

*Assigned at your instructor's discretion.* Extend your group's chart on your own.

- Build a **second** version of the same chart that is deliberately *misleading* — truncate the axis, or cherry-pick the range — without inventing or changing a single number. Place it beside your honest version.
- Then reflect in writing (about 300 words): Every number in your misleading chart is accurate — so is the chart "true"? Who could be harmed if your misleading version were published as real? You also made cleaning decisions in step 2 of the lab; could a *different* reasonable cleaning decision have changed your chart's story? What does this tell you about trusting any chart — including one made by an AI tool — without seeing the data and the choices behind it?
