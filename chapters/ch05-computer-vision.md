---
title: "Chapter 5: Computer Vision"
subtitle: "How Machines See and Create"
short_title: "5 · Computer Vision"
description: "How a computer represents an image as numbers; image classification, object detection, segmentation, and motion tracking; how facial recognition works and why it is contested; how generative AI creates images; with Nano Banana and Hugging Face Spaces."
label: ch-05-computer-vision
tags: [computer-vision, image-recognition, facial-recognition, image-generation, nano-banana]
---

<!--
FIGURE 5.1 — opening master infographic. Generated with Nano Banana Pro via generate-image.js.
Style: dense ai4educators-style master infographic, deep-teal-and-coral palette, white/pale
background, faint circuit-board margin motif. 16:9 landscape. Composition: TWO-TERRITORY SPLIT
(distinct from earlier chapters' hub, journey, staircase, roster). LEFT half headed "HOW MACHINES
SEE": a photo turning into a pixel-number grid, then three small task tags CLASSIFY, DETECT,
SEGMENT. RIGHT half headed "HOW MACHINES CREATE": a text prompt turning, through a noise-to-image
progression, into a finished generated picture. A central vertical divider with a two-way arrow.
Title top: HOW MACHINES SEE AND CREATE. Reference: fig-1-1 for palette and finish. No garbled
text; short labels only.
-->

:::{figure} ../images/ch05/fig-5-1-see-and-create.png
:label: fig-5-1
:alt: A master infographic split into two territories — how machines see, turning a photo into pixel numbers and recognizing it, and how machines create, turning a text prompt into a generated image.
:width: 100%
:align: center

**Figure 5.1.** *How machines see and create.* The same core idea — an image is a grid of numbers — powers both halves of this chapter: machines that *recognize* images, and machines that *generate* them.
:::

**Chapter 5 of 8 · The Technologies**

Look at a photograph of a dog on a beach. You know, instantly and without effort, that it is a dog, that it is on sand, that the bright area is sky, that the dog is mid-run. You did not *calculate* any of that. You simply saw it.

A computer cannot do what you just did — not in that way, and not for free. When a computer "looks" at that photograph, it does not receive a dog, a beach, or a sky. It receives a grid of numbers. Nothing else. Every capability in this chapter — a phone that sorts your photos, a system that screens a chest X-ray, a camera that recognizes a face, a tool that *generates* a photorealistic image of a dog that never existed — is built on top of that one humble, strange fact.

This chapter is about teaching machines to work with images, and it has two halves that used to be separate and are now deeply linked. The first half is **recognition**: how a machine takes an image and figures out what is in it. The second half is **generation**: how a machine, given a few words, *creates* a brand-new image. Understanding both is no longer optional. We have crossed into a world where you cannot assume a photograph shows something that happened — and the only real defense is understanding how the machines behind these images actually work.

## Learning Objectives

By the end of this chapter, you will be able to:

1. **Explain** how a computer represents an image as a grid of numbers.
2. **Distinguish** the main computer-vision tasks — classification, object detection, segmentation, and motion tracking.
3. **Describe** how facial recognition works and explain why it is one of the most contested AI technologies.
4. **Explain**, in plain language, how a generative model creates a new image from a text prompt.
5. **Use** a Hugging Face Space to apply a computer-vision model, and judge AI-generated images critically.

## How This Chapter Moves

We start with the foundational fact — an image is numbers — and build recognition on top of it: the four things machines do with images, then the special and contested case of faces. Then we cross the bridge from *seeing* to *creating*, and look honestly at how generated images work and what they mean. Finally you put a vision model to work yourself.

## 5.1 How a Computer "Sees"

A digital image is made of **pixels** — tiny squares of color. Hold your phone screen close and you can almost see them. An image is simply a grid of these squares: a modest photo might be 1,200 pixels wide and 800 tall, which is 960,000 pixels in all.

Now the key step. Each pixel is stored as **numbers**. In a black-and-white image, each pixel is a single number for brightness — by convention, 0 is pure black, 255 is pure white, and the values between are shades of gray. So a black-and-white image *is* a grid of numbers between 0 and 255. That is not a metaphor. That is the literal file.

Color works the same way with one twist: each pixel gets **three** numbers — how much red, how much green, how much blue (each from 0 to 255). Mixed in different amounts, those three values produce every color you see. A pixel of (255, 0, 0) is pure red; (255, 255, 0) is yellow; (40, 40, 40) is dark gray. A color photo is three stacked grids of numbers.

So when we say a computer "sees" an image, here is what is really true: it receives a few million numbers arranged in a grid. It has no eyes, no notion of "dog" or "beach." Everything it ever does with an image — every chapter you are about to read — is *math performed on that grid of numbers.*

```{mermaid}
graph LR
    P[A photograph] --> G[A grid of pixels<br/>each pixel = numbers 0-255]
    G --> M[A vision model<br/>finds patterns in the numbers]
    M --> R[An output<br/>a label, a box, a new image]
```

*Diagram 5.1. What "computer vision" really is. A photograph becomes a grid of numbers; a model finds patterns in those numbers; the patterns become a useful output.*

:::{admonition} 🔍 Myth vs. Reality
:class: warning
**The myth:** "A computer sees an image the way I do."

**The reality:** It does not see it at all — it processes a grid of numbers. This is not a technicality; it explains the technology's strengths *and* its failures. It is why a vision model can be far more consistent than a tired human inspector — numbers do not get bored. And it is why the same model can be fooled by things that would never fool you: a small change in lighting, an unusual angle, or a pattern of pixels deliberately crafted to confuse it. The machine is not "seeing wrong." It is doing math on numbers, and the numbers changed. Hold on to this fact and the rest of the chapter follows from it.
:::

:::{figure} ../images/ch05/fig-5-2-image-as-numbers.png
:label: fig-5-2
:alt: A photograph zoomed in until individual pixels are visible, with each pixel shown as numbers — a single brightness value for grayscale and three red-green-blue values for color.
:width: 90%
:align: center

**Figure 5.2.** *An image is a grid of numbers.* Zoom in far enough and a photograph dissolves into pixels, and each pixel is just numbers — one for brightness, or three for red, green, and blue.
:::

<!--
FIGURE 5.2 — concept infographic. Title: AN IMAGE IS A GRID OF NUMBERS. A simple flat photo on
the left (e.g. a dog) with a coral zoom-callout magnifying one small region into a visible grid
of square pixels; from that grid, an arrow to a panel showing the SAME grid with each cell
holding a number. A small side note shows one pixel = "0-255" for GRAYSCALE and one pixel =
three numbers "R G B" for COLOR. Deep teal panels and grid, coral zoom lines and accents, white
background, faint circuit margin motif. ai4educators master-infographic style. Reference:
fig-1-1 for palette/finish. Short labels and small numbers only, no garbled text.
-->

## 5.2 The Four Things Machines Do With Images

Once an image is numbers, a trained model can perform several distinct jobs. Four matter most, and they form a ladder of increasing detail. It is worth seeing them as separate, because people lump them together as "the AI recognized the image" — and the differences are exactly what decide whether a system is fit for a given purpose.

**Image classification** answers one question: *what is this, overall?* The model looks at the whole image and returns a single label — "dog," "chest X-ray: pneumonia likely," "ripe." It does not say *where* anything is. Your photo app uses classification to let you search "beach." A radiology tool uses it to flag which scans a doctor should read first. Classification is the simplest task and often the most useful.

**Object detection** answers a harder question: *what is here, and where?* The model returns labels *and* locations, usually drawing a **bounding box** around each object — "dog, here; beach ball, there; person, there." A self-checkout that recognizes items, a factory camera that finds every flawed part on a fast-moving belt, a wildlife survey that counts animals in a drone photo — all need detection, because *where* and *how many* are the point.

**Image segmentation** answers the most detailed question: *which exact pixels belong to what?* Instead of a rough box, segmentation traces the precise outline of each object, labeling every pixel. A self-driving car needs this — a bounding box around a pedestrian is not enough; the car must know exactly which pixels are road, curb, and person. Medical imaging uses segmentation to outline the precise shape of a tumor so its volume can be measured.

**Motion tracking** extends all of this across *time* — across the frames of a video. By comparing how the numbers shift from frame to frame, a model can follow an object's movement: a security system tracking a person across cameras, a sports system tracing a ball's path, a traffic system following each vehicle to time the lights.

:::{figure} ../images/ch05/fig-5-3-vision-tasks.png
:label: fig-5-3
:alt: The same street scene shown four ways — classification giving one label, object detection drawing boxes, segmentation outlining exact pixel regions, and motion tracking following an object across video frames.
:width: 100%
:align: center

**Figure 5.3.** *Four jobs, one image.* Classification names the whole image; detection boxes each object; segmentation traces exact outlines; tracking follows movement across frames. Each step up the ladder costs more and reveals more.
:::

<!--
FIGURE 5.3 — concept infographic, four-panel ladder composition. Title: WHAT MACHINES DO WITH
IMAGES. Four panels showing the SAME simple street scene processed four ways: PANEL 1
"CLASSIFICATION" — the whole image with one label tag "STREET SCENE"; PANEL 2 "OBJECT DETECTION"
— the scene with coral bounding boxes around a car, a person, a sign; PANEL 3 "SEGMENTATION" —
the scene with flat coloured regions precisely filling road, sidewalk, person; PANEL 4 "MOTION
TRACKING" — three faint film-frame copies of the scene with a coral dotted path following a car.
Deep teal, coral accents, white panels, faint circuit margin motif. ai4educators
master-infographic style. Reference: fig-1-1 for palette/finish. Short labels only, no garbled text.
-->

A worked example ties them together. Imagine a hospital deploying AI to help with chest X-rays. **Classification** flags which of the night's 400 scans look most urgent, so a radiologist reads those first. For a flagged scan, **detection** boxes the specific region of concern, pointing the doctor's eye. **Segmentation** traces the exact outline of a suspicious area so its size can be measured and tracked over months. No single task does the whole job — and notice that the human radiologist is never removed. The AI sorts, points, and measures; the diagnosis stays with the doctor. That division of labor — machine handles scale and consistency, human handles judgment — is the realistic shape of good computer vision, and you saw it first in the AI project cycle in Chapter 1.

## 5.3 Facial Recognition: The Most Contested Case

One application of these techniques deserves its own section, because it is among the most powerful and the most fiercely debated technologies in this entire book: **facial recognition.**

Mechanically, it is detection and classification pointed at faces. First the system *detects* a face in an image. Then it measures dozens of geometric relationships — the distance between the eyes, the shape of the cheekbones, the contour of the jaw — and converts them into a string of numbers, sometimes called a **faceprint**. To recognize someone, it compares that faceprint against a database of known faceprints and looks for a close match. Your phone unlocking when it sees you is facial recognition doing exactly this, on a database of one.

The benefits are real: unlocking devices, organizing photos, helping a blind user know who just walked into the room, speeding a traveler through a border checkpoint. But facial recognition raises problems that the friendlier vision tasks do not, and an educated person should be able to name them.

**Accuracy is not equal across groups of people.** Large independent studies — including a landmark United States government evaluation of dozens of facial-recognition systems — found that many of them were significantly *less* accurate for women and for people with darker skin, sometimes misidentifying them at many times the rate of white men. Recall why from Section 5.1: the model learned from a training set, and if that training set contained mostly light-skinned male faces, the model is simply better practiced on them. Bias in, bias out — Chapter 1's warning, with a human face on it. When a misidentification can mean a wrongful police stop, an unequal error rate is not a statistic. It is a person's afternoon, or worse.

**It enables surveillance at a scale never before possible.** A human guard can watch a few faces. A facial-recognition network can scan every face passing every connected camera in a city, continuously, and remember them. That is a genuinely new capability, and it shifts the balance between the watched and the watcher in a way societies are still arguing about — and should be.

**Consent is almost always missing.** Your face is not a password you can change. Many facial-recognition databases were built by scraping photos from the public internet — photos people posted for their friends, never imagining them becoming training data for a system that could identify them on a street. You were likely never asked.

None of this means facial recognition is purely bad. It means it is *consequential* — and consequential technology demands that the people deploying it, and the citizens living under it, understand it. That is the entire purpose of this book, and facial recognition is the sharpest example of why it matters.

## 5.4 From Seeing to Creating: How AI Generates Images

Until recently, this chapter would have ended at recognition. But the most startling shift in computer vision is that machines no longer only *recognize* images — they *create* them. You type a sentence, and a system returns a photorealistic image of something that has never existed. How?

Start with the honest plain-language version. A generative image model was trained on an enormous collection of images, each paired with a text description — hundreds of millions of caption-and-picture pairs scraped from the internet. From all of that, it learned the statistical patterns linking *words* to *visual features*: what pixel arrangements tend to go with "golden retriever," with "sunset," with "watercolor," with "wet sand."

Now the clever part, and the dominant method is worth understanding because the word is everywhere: **diffusion.** Picture starting not with a blank canvas but with a rectangle of pure random static — visual noise, like an untuned television. The model then removes that noise a little at a time, over many steps, and at every step it nudges the pixels toward something that better matches your text prompt, guided by all the patterns it learned. Noise becomes a vague blob; the blob becomes a shape; the shape sharpens into a golden retriever on wet sand. The image is not copied from anywhere. It is *assembled*, step by step, out of noise, steered by your words.

:::{figure} ../images/ch05/fig-5-4-how-ai-generates.png
:label: fig-5-4
:alt: A left-to-right sequence showing image generation — a text prompt and a field of random noise, refined step by step through intermediate blurry stages into a finished, sharp generated image.
:width: 90%
:align: center

**Figure 5.4.** *From noise to image.* A generative model starts with random static and a text prompt, then refines the pixels step by step — guided by patterns learned from millions of captioned images — until a new image matches the words.
:::

<!--
FIGURE 5.4 — concept infographic, left-to-right process composition. Title: HOW AI GENERATES AN
IMAGE. A text-prompt box on the far left, then a sequence of four square frames joined by coral
arrows: FRAME 1 "RANDOM NOISE" (TV-static square), FRAME 2 "REFINE" (a vague blurry blob),
FRAME 3 "REFINE" (a recognisable but soft shape), FRAME 4 "FINISHED IMAGE" (a clean sharp simple
picture). A small caption under the arrows: "GUIDED BY THE PROMPT". Deep teal frames and panels,
coral arrows and accents, white background, faint circuit margin motif. ai4educators
master-infographic style. Reference: fig-1-1 for palette/finish. Short labels only, no garbled text.
-->

This is genuinely transformative, and it is worth feeling the scale of it. A teacher can produce a custom diagram for tomorrow's lesson in a minute. A small business can make product images without a photo studio. A nurse educator can illustrate a rare condition that is hard to photograph. A person who cannot draw can finally show others the picture in their head. Whole categories of visual work that once required money, equipment, or years of skill are now a sentence away.

And the same capability has a dark edge that you must hold in view at the same time. A system that can generate a convincing image of *anything* can generate a convincing image of something *false*: a public figure doing what they never did, an "event" that never happened, a fake "photo" of a real person — a **deepfake**. The cost of manufacturing visual misinformation has collapsed. This is why the digital-literacy skills from Chapter 2 are now survival skills, and why "I saw a photo of it" is no longer proof of anything. We return to this in the ethics check, and again in Chapter 8.

## 5.5 Hands-On Walkthrough: Recognizing and Generating Images

This is the walkthrough your instructor will demonstrate before you try it in the lab. It has two parts — a tool everyone can use, and an instructor demonstration.

> **Verified as of May 2026.** If a screen looks different, the idea still holds — find the equivalent control.

### Hugging Face Spaces — run a vision model in your browser

**Hugging Face Spaces** (`huggingface.co/spaces`) hosts thousands of small, free, live AI demos called Spaces. A public Space is just a web page with a working AI model behind it — **no account, no install, any age.** It is the most direct way to *feel* what a vision model does.

**Step 1 — Open a Space your instructor has chosen.** Your instructor will give you the exact link to a specific, tested Space — an **image classifier**, an **object detector**, or a **background remover.** (Do not browse Spaces at random; the platform is open and uncurated. Use the links you are given.)

**Step 2 — Give it an image.** Upload a photo, or use one provided. This is the grid of numbers from Section 5.1, about to be processed.

**Step 3 — Read the output carefully.** A classifier returns labels with **confidence scores** — "golden retriever, 0.91; yellow Labrador, 0.06." A detector draws bounding boxes. Notice the model is never simply "right"; it reports how *confident* it is, and confidence is not the same as correctness.

**Step 4 — Try to break it.** Feed it something hard: a blurry photo, an unusual angle, an object partly hidden, something genuinely ambiguous. Watch the confidence scores fall or the labels go wrong. You are seeing the lesson of Section 5.1 first-hand — the model is doing math on numbers, and when the numbers are unfamiliar, it struggles.

### Instructor demonstration — Nano Banana, image generation

Your instructor will demonstrate **image generation** using **Nano Banana**, Google's image generation feature inside the Gemini app (shown in the prompt bar as **"Create images"**). Watch how a careful, detailed prompt produces a stronger result than a vague one — the same prompting lesson from Chapter 1, now for pixels — and how follow-up requests refine the image.

**Important — this is a demonstration, not a graded student task.** Image generation in Gemini requires users to be **18 or older**, so it is not assignable to the whole class. For your own hands-on work, use the Hugging Face Spaces your instructor provides. Note too that images generated by Nano Banana carry an invisible **SynthID** watermark that marks them as AI-generated — a small, important piece of the provenance puzzle we discuss next.

:::{admonition} ✋ Try This
:class: tip
On an image classifier Space, upload a clear, ordinary photo and note the top label and its confidence. Then upload a deliberately tricky version — heavily blurred, oddly cropped, or poorly lit. Compare the confidence scores. That gap is the honest measure of how much an image's *numbers* — not its "meaning" — drive everything a vision model does.
:::

:::{admonition} ⚖️ Ethics Check: Seeing is no longer believing
:class: important
1. **Recognition can be unequal.** Facial recognition and other vision systems can be measurably less accurate for some groups of people than others, because of biased training data. An unequal error rate, in a consequential system, is a fairness problem — not a footnote.
2. **Generated images can deceive.** AI can now fabricate a convincing image of almost anything. Treat a striking image the way Chapter 2 taught you to treat a striking claim: ask where it came from before you believe it or share it.
3. **Provenance matters.** Tools like SynthID watermark AI-generated images so they can be identified as synthetic. Support and use these signals — and when *you* create an AI image, do not pass it off as a real photograph.
4. **Consent applies to faces and likenesses.** Do not generate images of a real, identifiable person doing things they did not do. A face is not raw material.
:::

## Chapter Summary

To a computer, an image is not a picture — it is a grid of numbers, one value per pixel for brightness or three for red, green, and blue. Every capability in computer vision is math performed on that grid. On the *recognition* side, machines do four escalating jobs: **classification** (what is this overall), **object detection** (what and where, with bounding boxes), **segmentation** (which exact pixels belong to what), and **motion tracking** (following objects across video frames). **Facial recognition** applies these to faces, and is the most contested case — powerful, but burdened by unequal accuracy across groups, surveillance reach, and missing consent. On the *creation* side, **generative models** turn a text prompt into a brand-new image by **diffusion** — refining random noise, step by step, toward the words — which transforms creative work and, at the same time, makes convincing visual misinformation cheap. With a Hugging Face Space you ran a vision model yourself; with Nano Banana you saw one generate.

### Key Takeaways

- A digital image is a **grid of pixels**, and each pixel is **numbers** (0–255 for brightness; three numbers for red, green, blue). A computer "sees" only numbers.
- Machines do four escalating jobs with images: **classification**, **object detection**, **segmentation**, and **motion tracking** — each costs more and reveals more.
- **Facial recognition** is detection and classification applied to faces. It is powerful and contested: accuracy can be **unequal across groups**, it enables mass **surveillance**, and it usually lacks **consent**.
- **Generative models** create new images by **diffusion** — refining random noise toward a text prompt, guided by patterns learned from millions of captioned images.
- Generated images make visual work vastly more accessible — and make **deepfakes** and visual misinformation cheap. "I saw a photo" is no longer proof.
- Vision models report **confidence**, not certainty, and can be fooled when an image's numbers are unfamiliar.

### Key Terms

**Pixel** — the smallest square unit of a digital image.
**Computer vision** — the field of teaching computers to work with images and video.
**Image classification** — predicting a single overall label for an image.
**Object detection** — locating objects in an image, usually with bounding boxes.
**Bounding box** — a rectangle a model draws around a detected object.
**Image segmentation** — labeling every pixel to trace the exact outline of objects.
**Motion tracking** — following an object's movement across video frames.
**Facial recognition** — identifying or verifying a person from an image of their face.
**Faceprint** — the numeric summary of a face's measurements used for matching.
**Confidence score** — how strongly a model rates its own prediction.
**Generative model** — an AI model that creates new content such as images.
**Diffusion** — an image-generation method that refines random noise toward a prompt.
**Deepfake** — a fabricated but convincing AI-generated image, audio, or video.
**SynthID** — a watermark that marks an image as AI-generated.

### Bridge to Chapter 6

You have seen machines work with the visual world — recognizing images and creating them. Chapter 6, **Language and Conversation**, turns to the other great human medium: words. How does a machine process language — break a sentence into pieces, gauge its sentiment, translate it, hold a conversation? What, underneath the chat box, is a large language model actually doing? And you will build something of your own: a custom AI assistant, using **Gemini Gems**, that follows instructions you design.

---

## Apply and Analyze

The instructor-led walkthrough in Section 5.5 is the demonstration for this chapter. What follows is your turn — to check your understanding, apply a vision model, and reflect.

### Review Questions

1. **When a computer "sees" a color image, what does it actually receive?**
   A. A picture, the way a person sees it.
   B. A grid of pixels, each stored as three numbers for red, green, and blue.
   C. A written description of the scene.
   D. A single number summarizing the image.

2. **A factory camera must find and locate every flawed part on a moving belt, drawing a box around each one. Which computer-vision task is this?**
   A. Image classification.
   B. Object detection.
   C. Motion tracking only.
   D. Image generation.

3. **True or False:** Independent studies have found that many facial-recognition systems are less accurate for some groups of people than others, largely because of biased training data.

4. **In plain terms, how does a diffusion model generate an image?**
   A. It copies the closest matching image from the internet.
   B. It photographs a real scene and edits it.
   C. It starts with random noise and refines it step by step toward the text prompt.
   D. It draws the image by hand-coded rules.

5. **True or False:** Because AI can now generate convincing images of almost anything, seeing a realistic photo is no longer proof that the thing it shows is real.

:::{dropdown} Answer Key
1. **B** — a color image is a grid of pixels, each stored as red, green, and blue numbers.
2. **B** — object detection finds and locates objects, drawing bounding boxes.
3. **True** — large independent evaluations documented unequal accuracy traced to biased training data.
4. **C** — diffusion refines random noise step by step toward the prompt.
5. **True** — generated images can be photorealistic, so a realistic photo is no longer proof on its own.
:::

### Discussion Question

Facial recognition is used in ways many people welcome (unlocking a phone, speeding a border line) and ways many people fear (mass surveillance, wrongful identification). Choose one specific real-world use of facial recognition and argue whether its benefits justify its risks. Your answer must engage with at least one specific concern from Section 5.3 — unequal accuracy, surveillance reach, or missing consent — and at least one idea from elsewhere in this book (such as bias in training data, or human judgment staying in the loop).

### Breakout Lab: Put a Vision Model to Work

Work in a group of three or four. Total time: about 35–45 minutes. Low-stakes — the goal is to *do it*.

1. **Open the assigned Space (5 min).** Your instructor will provide a link to a specific, tested Hugging Face Space — an image classifier or object detector. Open it; no account is needed.
2. **Run clear examples (10 min).** As a group, feed it five ordinary, clear images. Record the model's output and its confidence for each. Does it get them right?
3. **Try to break it (15 min).** Now feed it five *hard* images — blurry, oddly angled, partially hidden, ambiguous, or unusual. Record what happens to the labels and the confidence scores.
4. **Diagnose (5 min).** Using this chapter's vocabulary, explain *why* the hard images caused trouble. Connect it to Section 5.1.
5. **Share (5 min).** Each group reports its most interesting failure and its explanation.

**Submit:** your table of ten images with the model's output and confidence for each, and three sentences explaining one failure in terms of how a computer actually "sees." Due at the end of class.

### Optional Take-Home: Going Deeper

*Assigned at your instructor's discretion.* Extend the lab on your own.

- Find or generate one AI-made image and one genuine photograph of a similar subject. Study both. List the specific clues — if any — that helped you tell them apart.
- Then reflect in writing (about 300 words): How confident were you, honestly, in telling the real image from the generated one? If a generated image of a *real person* were shared as a true photo, who could be harmed, and how? Section 5.3 described biased training data in facial recognition; could a generative image model carry bias of its own — for example, in who or what it depicts by default when a prompt does not specify? Why does watermarking AI-generated images, as SynthID does, matter for the information world Chapter 2 described?
