---
title: "Chapter 4: Machine Learning"
subtitle: "Teaching Machines to Decide"
short_title: "4 · Machine Learning"
description: "How machines learn to classify from examples; k-nearest neighbors, decision trees, linear classifiers, support vector machines, and neural networks in plain language; how to train and judge a model; with Teachable Machine, TensorFlow Playground, and an optional Python lab."
label: ch-04-machine-learning
tags: [machine-learning, classification, algorithms, teachable-machine, tensorflow-playground]
---

<!--
FIGURE 4.1 — opening master infographic. Generated with Nano Banana Pro via generate-image.js.
Style: dense ai4educators-style master infographic, deep-teal-and-coral palette, white/pale
background, faint circuit-board margin motif. 16:9 landscape. Composition: ROSTER GALLERY
(distinct from Ch1 hub, Ch2 journey, Ch3 staircase). Top band: "CLASSIFICATION = DRAWING A
BOUNDARY" with a small two-colour dot scatter split by a line. Middle: a row of five small
algorithm cards — K-NN, DECISION TREE, LINEAR, SVM, NEURAL NET — each with a tiny icon. Bottom
strip: a "TRAIN -> TEST -> JUDGE" three-step bar. Title top: TEACHING MACHINES TO DECIDE.
Reference: fig-1-1 for palette and finish. No garbled text; short labels only.
-->

:::{figure} ../images/ch04/fig-4-1-machine-learning.png
:label: fig-4-1
:alt: A master infographic mapping the chapter — classification as drawing a boundary, a roster of five classifier algorithms, and the train-test-judge workflow.
:width: 100%
:align: center

**Figure 4.1.** *Teaching machines to decide.* Classification is drawing a boundary between groups. This chapter meets five algorithms that draw it, and the workflow that trains and judges them.
:::

**Chapter 4 of 8 · The Technologies**

There is a phrase that gets attached to artificial intelligence so often it has hardened into common sense: *AI is a black box.* The idea is that these systems are so complex that no one — not even their builders — can say how they reach a decision. For the giant generative models behind tools like Gemini, there is some truth in it. But applied to AI as a whole, it is one of the most misleading things people believe.

Because here is what the phrase quietly hides. The AI systems that make the most *consequential* everyday decisions about people are mostly **not** mysterious. The system that decides whether your email is spam. The one that flags a credit-card charge as fraud. The one that helps decide whether a loan is approved, whether a tumor looks suspicious, whether a job application moves forward. Most of those are a kind of AI called a **classifier** — and a classifier is genuinely understandable. You can learn, in an afternoon, the actual idea behind every one of them.

That is this chapter. We are going to open the box. You will see what it means for a machine to *learn to decide*, meet the five workhorse algorithms that do it — in plain language, no mathematics required — and learn how to tell a good model from a bad one. Then you will train a working machine learning model yourself, with **Teachable Machine**, writing no code at all. And if you want to go further, an optional lab lets you build one in Python.

## Learning Objectives

By the end of this chapter, you will be able to:

1. **Explain** what classification is and how a machine learns a decision boundary from labelled examples.
2. **Describe**, in plain language, five classification algorithms — k-nearest neighbors, decision trees, linear classifiers, support vector machines, and neural networks.
3. **Explain** why models are tested on data they have not seen, and what *overfitting* means.
4. **Judge** a model's quality and explain why accuracy alone can be misleading.
5. **Train** a working classifier with Teachable Machine and explain how its performance depends on its training examples.

## How This Chapter Moves

We start with the core idea — classification as drawing a boundary. Then we meet the five algorithms, one analogy at a time. Then we turn to the part that separates a useful model from a useless one: testing it honestly, and judging it well. Finally you train one yourself — with no code in Teachable Machine, and optionally with code in Python.

## 4.1 Learning to Decide

Recall the central idea from Chapter 1: a machine learning system learns patterns from examples instead of following hand-written rules. Now we make that concrete with the most common job in all of machine learning — **classification**.

**Classification** means predicting which *category* something belongs to. Spam or not spam. Fraud or legitimate. Benign or suspicious. Approve or deny. The categories are decided in advance; the model's job is to place each new case into one of them.

Here is the mental picture that makes the whole chapter click. Imagine plotting your examples as dots on a graph. A bank plots past loan applicants: each dot is one applicant, placed by two features — say, income across the bottom, and existing debt up the side. Now colour the dots by what actually happened: teal for "repaid," coral for "defaulted." Step back, and you will usually see the colours are not perfectly mixed — the teal dots cluster somewhat apart from the coral ones.

**Learning to classify is learning where to draw the boundary between the colours.** Once a model has drawn that boundary from past examples, a brand-new applicant arrives as a new dot — and whichever side of the boundary they land on is the model's prediction. That is it. That is what is inside the box. Every algorithm in this chapter is just a different *way of drawing that boundary*.

:::{admonition} 🔍 Myth vs. Reality
:class: warning
**The myth:** "Machine learning models are black boxes nobody can understand."

**The reality:** The huge generative models *are* genuinely hard to interpret. But the classifiers that make most of the consequential, everyday decisions about people are not. A decision tree can be printed out and read like a flowchart. A linear classifier is a line you can see. Treating *all* AI as an unknowable black box is not humility — it is a way of dodging accountability. "The algorithm decided" stops being an excuse the moment you understand that someone chose the examples, chose the features, and chose where the boundary gets drawn.
:::

A few terms, building on Chapter 1. The things you measure — income, debt, the words in an email — are the **features**. The known answer on each training example — repaid or defaulted — is the **label**. The drawn boundary, learned from the examples, is the **model**. And the features you feed a model are often exactly the *derived columns* you learned to build in Chapter 3 — which is why good data transformation and good machine learning are the same skill, two chapters apart.

## 4.2 The Classifier Family

There is no single "machine learning algorithm." There is a family of them, and they differ in *how they draw the boundary*. Here are the five you should know — each in plain language, each with the analogy that makes it stick.

### k-Nearest Neighbors: judge by your neighbors

**k-Nearest Neighbors** — k-NN — barely "learns" at all. To classify a new dot, it simply looks at the *k* closest known examples — its nearest neighbors — and takes a vote. If you set k to 5, it finds the 5 nearest past cases; if 4 of them defaulted, it predicts "default."

The analogy is an old saying: *tell me who your neighbors are, and I will tell you who you are.* k-NN takes that literally. It is wonderfully intuitive, and it has a real weakness — it must compare every new case against all the stored examples, which gets slow with large data, and "closest" stops meaning much when there are many features.

### Decision Trees: a flowchart of questions

A **decision tree** classifies by asking a sequence of yes-or-no questions, exactly like a triage flowchart a nurse might follow.

```{mermaid}
graph TD
    A["Income above threshold?"] -->|No| D1["Predict: DENY"]
    A -->|Yes| B["Existing debt high?"]
    B -->|Yes| C["Missed a payment before?"]
    B -->|No| D2["Predict: APPROVE"]
    C -->|Yes| D3["Predict: DENY"]
    C -->|No| D4["Predict: APPROVE"]
```

*Diagram 4.1. A decision tree is a flowchart the machine writes itself. It learns, from the examples, which questions to ask and in which order.*

That is the appeal of a decision tree: you can *read it*. You can hand it to the loan applicant and show them the path their case took. Its weakness is that a single tree, grown too deep, will memorize the training data — a problem we name in the next section.

### Linear Classifiers: draw a straight line

A **linear classifier** does the most direct thing imaginable: it draws a single straight line — in higher dimensions, a flat plane — to separate the two groups. Everything on one side is predicted teal; everything on the other, coral.

It is fast, and the line is easy to understand. Its limit is in the name: if the two groups cannot be cleanly separated by a *straight* line — if the real boundary curves — a linear classifier will always get some cases wrong.

### Support Vector Machines: the widest possible gap

A **support vector machine** — SVM — also separates groups with a boundary, but it is choosy about *which* boundary. Many lines might split the two colours; an SVM looks for the one that leaves the **widest possible gap** between them, the boundary with the most breathing room on both sides.

The analogy: picture paving the widest straight road you can between two neighborhoods without paving over any house. That road is the SVM's boundary, and the houses closest to it — the ones that determine where it can go — are the "support vectors." With a clever extension (a *kernel*), an SVM can also bend its boundary into a curve to handle groups a straight line cannot split.

### Neural Networks: stack many small decisions

A **neural network** builds its boundary out of many small, simple units — loosely inspired by brain cells — connected in layers. Each unit makes a tiny decision; layered together, they can bend and fold the boundary into almost any shape, however complex.

This flexibility is why neural networks power the modern AI era you read about in Chapter 1 — and it comes at a price. They need a lot of examples, a lot of computing power, and they are the hardest of the five to interpret. A neural network is the closest of this family to the "black box," which is exactly why the readable alternatives still matter.

:::{figure} ../images/ch04/fig-4-2-classifier-family.png
:label: fig-4-2
:alt: Five small panels showing the same two groups of dots separated five different ways — by k-nearest-neighbor regions, a decision tree's boxy splits, a straight linear boundary, an SVM's widest-margin line, and a neural network's curved boundary.
:width: 100%
:align: center

**Figure 4.2.** *Five ways to draw one boundary.* The same two groups of examples, separated by each algorithm. They are not five different goals — they are five different strategies for the same job.
:::

<!--
FIGURE 4.2 — concept infographic, five-panel gallery composition. Title: FIVE WAYS TO DRAW A
BOUNDARY. Five small labelled panels in a row, each showing the SAME simple scatter of teal dots
and coral dots, separated a different way: PANEL 1 "K-NN" — coloured neighbourhood regions;
PANEL 2 "DECISION TREE" — boxy right-angled step splits; PANEL 3 "LINEAR" — one straight diagonal
line; PANEL 4 "SVM" — a straight line with a visible shaded margin/gap on both sides; PANEL 5
"NEURAL NETWORK" — a smooth curving boundary. Deep teal and coral dots, coral boundary lines,
white panels, faint circuit margin motif. ai4educators master-infographic style. Reference:
fig-1-1 for palette/finish. Short labels only, no garbled text.
-->

So which algorithm is best? The honest answer is *it depends* — on how much data you have, whether you need to explain the decision, how the boundary really curves, and how fast it must run. A bank that must legally explain every denial may choose a readable decision tree over a more accurate neural network. Choosing well is a skill; knowing that the choice exists is the start of it.

## 4.3 Training and Testing a Model

Drawing a boundary from examples is only half the job. The other half is making sure the boundary is actually *good* — and "good" has a precise meaning that beginners almost always get wrong.

A good model is not one that does well on the examples it learned from. It is one that does well on examples it has **never seen.** That quality has a name: **generalization.** A model that generalizes has learned the real pattern; a model that does not has merely memorized.

To tell the difference, machine learning practitioners do something simple and clever. They **split their data**. Before training, they set aside a portion — often around 20–30% — as a **test set**, and they hide it. The model learns only from the remaining **training set**. Then, and only then, the model is shown the hidden test set, and its predictions are checked against the answers it was never allowed to see. Performance on that test set is the honest measure.

Why the ceremony? Because of a failure mode with a name you should know: **overfitting.** An overfit model has essentially memorized its training examples — every quirk, every fluke, every bit of noise — instead of learning the general pattern. It will score brilliantly on the data it studied and then fail on anything new. It is the student who memorized the answers to last year's exam and is lost the moment the questions change.

:::{figure} ../images/ch04/fig-4-3-train-and-test.png
:label: fig-4-3
:alt: A diagram showing a dataset split into a larger training set and a smaller hidden test set, and a comparison of an overfit boundary that memorizes versus a general boundary that learns the pattern.
:width: 90%
:align: center

**Figure 4.3.** *Train, then test on the unseen.* Data is split so the model is judged on examples it never studied — and an overfit model, which memorized instead of learning, is exposed.
:::

<!--
FIGURE 4.3 — concept infographic, two-part composition. Title: TRAIN, THEN TEST. TOP half: a
dataset block splitting via a coral arrow into a large panel "TRAINING SET" and a smaller panel
"TEST SET (HIDDEN)". BOTTOM half: two small side-by-side scatter panels labelled "OVERFIT —
MEMORIZED" (a wildly wiggly boundary contorting around every single dot) and "GENERAL — LEARNED"
(a smooth sensible boundary). Deep teal panels, coral arrows and accents, teal/coral dots, white
background, faint circuit margin motif. ai4educators master-infographic style. Reference: fig-1-1
for palette/finish. Short labels only, no garbled text.
-->

You can *watch* overfitting happen. In the hands-on section you will use TensorFlow Playground, where a neural network trains in front of you: push it too hard and you will see its boundary stop being a sensible curve and start contorting itself around individual dots — memorizing. Seeing it once teaches the idea better than any paragraph can.

## 4.4 Judging a Model: Why Accuracy Can Lie

Once a model is tested on unseen data, how do you score it? The obvious measure is **accuracy** — the percentage of test cases it gets right. A model that correctly classifies 92 of 100 unseen cases is 92% accurate.

Accuracy is useful. But relied on alone, it can hide a worthless model — and this is one of the most important cautions in the chapter.

Picture a fraud detector. In real credit-card data, genuine fraud is rare — perhaps 1 in 100 transactions. Now build the laziest possible model: one that ignores every feature and simply predicts "legitimate" every single time. What is its accuracy? **99%.** It is right on all 99 legitimate transactions and wrong only on the 1 fraud. By the accuracy score alone, it looks excellent. It is, in fact, completely useless — it has never caught a single fraud, which was the entire point.

This is the **accuracy trap**, and it appears whenever the categories are *imbalanced* — when one outcome is far more common than the other. And imbalance is everywhere in the decisions that matter: fraud is rare, a particular disease is rare, the flagged résumé is rare. So a careful practitioner never stops at accuracy. They ask the sharper question: *how does the model do on the rare cases that actually matter?* — how many real frauds did it catch, and how often did it cry fraud on an innocent transaction.

:::{figure} ../images/ch04/fig-4-4-judging-a-model.png
:label: fig-4-4
:alt: An illustration of the accuracy trap — a lazy model that always predicts the common class scores 99% accuracy on imbalanced data while catching zero of the rare important cases.
:width: 90%
:align: center

**Figure 4.4.** *The accuracy trap.* On imbalanced data, a model that always guesses the common answer can post a dazzling accuracy score while being completely useless at the job that matters.
:::

<!--
FIGURE 4.4 — concept infographic. Title: WHY ACCURACY CAN LIE. Center: 100 small transaction
icons, 99 teal "LEGITIMATE" and 1 coral "FRAUD". An arrow to a "LAZY MODEL" box whose rule reads
"ALWAYS SAY LEGITIMATE". Two result pills: a large green-ish pill "99% ACCURATE" and beside it a
coral warning pill "0 FRAUDS CAUGHT". A footer banner: "CHECK THE CASES THAT MATTER". Deep teal,
coral accents, white background, faint circuit margin motif. ai4educators master-infographic
style. Reference: fig-1-1 for palette/finish. Short labels only, no garbled text.
-->

:::{dropdown} 🔎 Going Deeper: Precision and recall
When practitioners look past accuracy, two measures do most of the work. **Recall** asks: of all the cases that *were* fraud, what fraction did the model catch? A recall of 0 exposes the lazy model instantly. **Precision** asks: of all the cases the model *flagged* as fraud, what fraction really were? Low precision means the model cries wolf, freezing innocent customers' cards.

The two trade off. Flag more aggressively and you catch more real fraud (higher recall) but annoy more innocent people (lower precision). Flag cautiously and the reverse. There is no universally right balance — it is a judgment call about real-world costs. A cancer screen leans toward recall: better a false alarm than a missed tumor. A spam filter leans toward precision: better a little spam in the inbox than a real job offer lost to the spam folder. You do not need the formulas to carry the lesson: *one number is never the whole story.*
:::

## 4.5 Hands-On Walkthrough: Train Your Own Model

Enough description. In this section you train a real machine learning model and watch another one learn — and you do it with no code and no account, using two free tools.

> **Verified as of May 2026.** If a screen looks different, the idea still holds — find the equivalent control.

### Teachable Machine — train a classifier with your own examples

**Teachable Machine** (`teachablemachine.withgoogle.com`), made by Google, lets you train a working classifier in your browser by *showing it examples*. No code, no account, any age.

**Step 1 — Start a project.** Open the site and choose an **Image Project** (it can also classify sounds or poses).

**Step 2 — Create your classes.** A class is one category. Name them meaningfully — for a demo, "Mug" and "Phone," or "Mask On" and "Mask Off."

**Step 3 — Add examples.** For each class, hold the object to your webcam and record sample images. This is your *training data* — and everything from Chapter 1 onward applies: more and more *varied* examples make a stronger model.

**Step 4 — Train.** Click **Train Model**. In seconds, it learns the boundary between your classes — entirely from the examples you gave it.

**Step 5 — Test it live.** Show the webcam a new object. The model predicts a class with a confidence score. Now experiment honestly: change the lighting, the background, the angle. Watch it get confused. You have just *felt* the lesson of this whole book — a model is only as good, and only as general, as its training examples.

### TensorFlow Playground — watch a neural network learn

**TensorFlow Playground** (`playground.tensorflow.org`) lets you watch a neural network train, live, in your browser. No account, any age.

**Step 1 — Open it and press play.** A small neural network begins learning to separate two colours of dots. Watch the boundary form.

**Step 2 — Give it a hard problem.** Switch the dataset to the **spiral**. With the default setup, the network struggles — a straight-ish boundary cannot separate a spiral.

**Step 3 — Add power.** Add hidden layers and neurons. Watch the boundary gain the flexibility to wrap around the spiral. This is the neural network from Section 4.2, learning in front of you.

**Step 4 — Push too far, and see overfitting.** Pile on neurons and let it run. Watch the boundary stop being a clean curve and start contorting around individual dots — and watch the *test* loss rise even as the *training* loss falls. That divergence **is** overfitting, made visible.

:::{admonition} ✋ Try This
:class: tip
In Teachable Machine, train a two-class model with only **three** example images per class. Test it. Then retrain with **thirty** varied images per class and test again. The jump in reliability is the single most important practical lesson in machine learning — the model's quality lives in its data.
:::

:::{admonition} ⚖️ Ethics Check: A classifier decides things about people
:class: important
The friendly demo — mugs and phones — hides real stakes. The same technology decides who gets a loan, whose résumé a recruiter sees, whose transaction is frozen. Carry three habits forward:

1. **Biased examples make a biased classifier.** A model trained on past decisions inherits the unfairness in them — "bias in, bias out," from Chapter 1. The machine launders an old prejudice into a confident new number.
2. **Accuracy is not fairness.** A model can be highly accurate overall and still be far worse for one group of people. Overall accuracy can hide that completely.
3. **Someone is accountable.** A person chose the training data, the features, and where the boundary falls. "The algorithm decided" names no one — and a decision about a person's life deserves a name.
:::

## Chapter Summary

Machine learning is not an unknowable black box — at least not the classifiers that make most of the consequential decisions about people. **Classification** is predicting a category, and learning to classify is learning where to draw the **boundary** between groups of labelled examples. Five algorithms draw that boundary differently: **k-nearest neighbors** votes among the closest examples, a **decision tree** asks a flowchart of questions, a **linear classifier** draws a straight line, a **support vector machine** finds the widest-margin line, and a **neural network** stacks many small decisions into a flexible curve. A model is only good if it **generalizes** to unseen data, so data is split into training and test sets — guarding against **overfitting**, where a model memorizes instead of learning. And a model is judged with care, because **accuracy alone can lie** on imbalanced data. With Teachable Machine you trained a real classifier from your own examples; with TensorFlow Playground you watched one learn — and overfit.

### Key Takeaways

- **Classification** predicts a category; learning to classify is learning where to draw the **boundary** between labelled groups.
- Five algorithms draw it differently — **k-NN** (vote among neighbors), **decision tree** (flowchart of questions), **linear classifier** (straight line), **SVM** (widest-margin line), **neural network** (flexible stacked decisions).
- A good model **generalizes** to unseen data. Data is split into a **training set** and a hidden **test set** to measure this honestly.
- **Overfitting** is memorizing the training data instead of learning the pattern — great training scores, poor real performance.
- **Accuracy alone can lie:** on imbalanced data, a lazy model can score 99% and still be useless. Always check the rare cases that matter.
- A model's quality lives in its **training examples** — and a biased classifier is a biased dataset wearing a confident number.

### Key Terms

**Classification** — predicting which predefined category a case belongs to.
**Classifier** — a model that performs classification.
**Decision boundary** — the dividing line a classifier learns between categories.
**k-Nearest Neighbors (k-NN)** — a classifier that votes among the closest known examples.
**Decision tree** — a classifier that asks a sequence of yes/no questions.
**Linear classifier** — a classifier that separates groups with a straight line or flat plane.
**Support vector machine (SVM)** — a classifier that draws the boundary with the widest margin between groups.
**Neural network** — a classifier built from many simple units in layers, able to learn flexible boundaries.
**Generalization** — a model's ability to perform well on data it has not seen.
**Training set / test set** — the examples a model learns from / the held-out examples it is judged on.
**Overfitting** — when a model memorizes its training data instead of learning the general pattern.
**Accuracy** — the percentage of cases a model classifies correctly.
**Imbalanced data** — data in which one category is far more common than another.

### Bridge to Chapter 5

You can now teach a machine to decide between categories — and you saw, with Teachable Machine, that classifying *images* is just classification with pixels as the features. That is the doorway to Chapter 5, **Computer Vision**. We will look closely at how a computer turns a photograph into numbers it can learn from, how it detects and locates objects, how facial recognition works — and the serious questions that last one raises. And then a turn you might not expect: from machines that *recognize* images to machines that *create* them.

---

## Apply and Analyze

The instructor-led walkthrough in Section 4.5 is the demonstration for this chapter. What follows is your turn — to check your understanding, train a model of your own, and reflect.

### Review Questions

1. **In machine learning, "classification" means:**
   A. Sorting data files into folders.
   B. Predicting which predefined category a case belongs to.
   C. Cleaning a dataset.
   D. Drawing any chart from data.

2. **Which algorithm classifies a new case by taking a vote among the closest known examples?**
   A. Decision tree.
   B. Linear classifier.
   C. k-Nearest Neighbors.
   D. Support vector machine.

3. **True or False:** A model that scores very high on its training data is, for that reason, guaranteed to perform well on new data.

4. **A fraud detector that always predicts "legitimate" reaches 99% accuracy because real fraud is rare. This is an example of:**
   A. Overfitting.
   B. The accuracy trap on imbalanced data.
   C. A decision boundary.
   D. Generalization.

5. **True or False:** Overfitting is when a model memorizes its training examples instead of learning the general pattern.

:::{dropdown} Answer Key
1. **B** — classification predicts a predefined category.
2. **C** — k-Nearest Neighbors votes among the nearest examples.
3. **False** — high training performance can mean overfitting; only performance on unseen data shows generalization.
4. **B** — the accuracy trap: high accuracy on imbalanced data hiding a useless model.
5. **True** — that is exactly what overfitting is.
:::

### Discussion Question

Think of one real decision in your field or daily life that could be framed as a classification problem (approve/deny, urgent/routine, safe/at-risk, and so on). What features would a model need? Where would the training examples come from — and what bias might already be hiding in them? Would you want the model to be a *readable* decision tree or a more accurate but opaque neural network, and why? Support your answer with at least one idea from this chapter.

### Breakout Lab: Train a Classifier in Teachable Machine

Work in a group of three or four. Total time: about 35–45 minutes. Low-stakes — the goal is to *do it*.

1. **Choose a classification task (5 min).** Pick something a webcam image classifier could decide — two or three classes of objects, hand signs, or expressions. Keep it appropriate and simple.
2. **Plan the training data (5 min).** Before recording anything, decide as a group: how many examples per class, and how will you make them *varied* (angles, lighting, backgrounds)?
3. **Train it (15 min).** Build the model in Teachable Machine. Test it live.
4. **Break it on purpose (10 min).** Find a situation where it fails — new lighting, a new background, an object it was not trained on. Diagnose *why*, using this chapter's vocabulary.
5. **Share (5 min).** Each group demonstrates its model, shows one failure, and explains the cause.

**Submit:** a one-paragraph description of your model, how many training examples you used per class, and three sentences explaining one failure you found and what about the training data caused it. Due at the end of class.

### Optional Advanced Lab: Build a Classifier in Python

<a href="https://colab.research.google.com/github/c-marq/cai1001c-ai-thinking/blob/main/notebooks/ch04-train-a-classifier.ipynb" target="_blank">
<img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

*Optional, and assigned at your instructor's discretion.* Teachable Machine trained a classifier with no code. This lab does the same thing the way a data scientist would — in Python, with a few lines of the scikit-learn library — so you can see what is happening underneath. It runs entirely in **Google Colab**, free in your browser, with nothing to install. You will load a dataset, split it into training and test sets, train a **k-nearest neighbors** classifier and a **decision tree**, and compare how each one scores on data it never saw. Click the badge above to open it.

### Optional Take-Home: Going Deeper

*Assigned at your instructor's discretion.* Extend your group's Teachable Machine project on your own.

- Retrain your model twice: once with very few examples per class, once with many varied examples. Record how the reliability changes.
- Then reflect in writing (about 300 words): Your model's behavior changed only because its *training data* changed — the algorithm never did. If this were a model that screened job applicants instead of recognizing objects, what kinds of bias could enter through the training examples, and who could be harmed? Why is "the algorithm decided" an inadequate explanation for a decision about a person — and what would a more honest explanation name?
