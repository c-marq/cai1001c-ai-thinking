---
title: "Chapter 6: Language and Conversation"
subtitle: "How Machines Understand Us"
short_title: "6 · Language & Conversation"
description: "How machines process human language — tokenization, sentiment analysis, translation, and speech; what large language models and transformers actually do; how chatbots work; and building a custom AI assistant with Gemini Gems."
label: ch-06-language-conversation
tags: [nlp, language-models, transformers, chatbots, gemini-gems]
---

<!--
FIGURE 6.1 — opening master infographic. Generated with Nano Banana Pro via generate-image.js.
Style: dense ai4educators-style master infographic, deep-teal-and-coral palette, white/pale
background, faint circuit-board margin motif. 16:9 landscape. Composition: FOUR STACKED
HORIZONTAL BANDS (distinct from earlier chapters' hub, journey, staircase, roster, split).
Band 1 "TEXT BECOMES TOKENS" — a sentence breaking into token chips. Band 2 "MACHINES READ
MEANING" — small icons for sentiment (a face), translation (two speech bubbles), speech (a
soundwave). Band 3 "LANGUAGE MODELS PREDICT WORDS" — a sentence with a next-word prediction.
Band 4 "CHATBOTS AND CUSTOM GEMS" — a chat bubble pair and a gem icon. Title top: HOW MACHINES
UNDERSTAND US. Reference: fig-1-1 for palette and finish. No garbled text; short labels only.
-->

:::{figure} ../images/ch06/fig-6-1-language-conversation.png
:label: fig-6-1
:alt: A master infographic of four stacked bands — text becoming tokens, machines reading meaning, language models predicting words, and chatbots and custom Gems.
:width: 100%
:align: center

**Figure 6.1.** *How machines understand us.* Four layers, from raw text to a conversation: words become tokens, machines read meaning, language models predict words, and chatbots — including ones you build — put it all together.
:::

**Chapter 6 of 8 · The Technologies**

Sit down with a modern AI assistant and you can have a conversation that feels — there is no other word for it — *understanding*. It follows your point. It picks up your tone. It remembers what you said three messages ago. It is easy, and almost irresistible, to conclude that the machine *understands* you the way a person would.

It does not. And the gap between how it feels and what is actually happening is one of the most important things this whole book can teach you.

A modern language AI is doing something genuinely astonishing and genuinely narrow at the same time: it is **predicting words**. Trained on a staggering amount of human writing, it has become extraordinarily good at answering one question — *given everything so far, what word is likely to come next?* — over and over, one word at a time. That is the engine inside the chatbot. It produces language so fluent that it crosses a line in our minds, and we read fluency as understanding. It is not the same thing.

This chapter is about how machines work with language — **natural language processing**, or NLP. We will see how a machine breaks language into pieces it can handle, the useful things it does with language, what a large language model and a transformer actually are, and how chatbots work. Then you will build a working AI assistant of your own — a custom **Gemini Gem** — and in doing so, build a chatbot without writing a line of code.

## Learning Objectives

By the end of this chapter, you will be able to:

1. **Explain** how a machine breaks language into tokens and turns words into numbers.
2. **Describe** the main NLP tasks — sentiment analysis, machine translation, and speech recognition and synthesis.
3. **Explain**, in plain language, what a large language model and a transformer do, and why fluency is not understanding.
4. **Distinguish** rule-based, retrieval-based, and generative chatbots.
5. **Build** a custom AI assistant with Gemini Gems and explain how its instructions shape its behavior.

## How This Chapter Moves

We start at the bottom — how raw text becomes something a machine can process. Then the useful tasks built on top of that. Then the engine of the modern era: large language models and the transformer. Then chatbots, the most familiar form language AI takes. And finally you build one yourself, as a Gem.

## 6.1 How a Machine Reads Language

Human language is, for a computer, a genuinely hard problem — much harder than numbers in a spreadsheet. It is full of ambiguity. The sentence "I saw her duck" has two completely different meanings, and you resolve which one effortlessly from context a computer does not automatically have. Words shift meaning ("bank" — money or river?). Tone carries meaning that the literal words deny ("oh, *great*"). For decades, this difficulty kept computers clumsy with language. Then two ideas changed everything.

**The first idea: tokenization.** A computer cannot take in a sentence as a sentence. So the first step in every language AI is to chop the text into small, consistent pieces called **tokens**. A token is often a word, but not always — common words become single tokens, while a longer or rarer word may be split into a few tokens ("unhappiness" might become "un," "happi," "ness"). The sentence "Machines read tokens" might become five or six tokens. Tokenization is simply the act of cutting text into these standard pieces so the rest of the system has something uniform to work with.

**The second idea: turning tokens into numbers.** Recall a theme from every chapter so far — machines work on numbers. Language is no exception. Each token is converted into a list of numbers. And here is the elegant part: those numbers are not assigned randomly. They are learned, from enormous amounts of text, so that **tokens used in similar ways get similar numbers.** The numbers for "doctor" and "nurse" end up close together; "doctor" and "bicycle" end up far apart. The machine never gets told what a doctor *is* — it learns, from the company a word keeps across billions of sentences, a numeric fingerprint of how that word behaves. That numeric fingerprint is called an **embedding**, and it is as close as a machine gets to "meaning": meaning as *measured by context.*

```{mermaid}
graph LR
    T["A sentence of text"] --> K["Tokens<br/>text cut into standard pieces"]
    K --> E["Embeddings<br/>each token becomes numbers"]
    E --> M["A language model<br/>works entirely on the numbers"]
```

*Diagram 6.1. From text to numbers. Every language AI begins by cutting text into tokens and turning each token into numbers — because the model can only work on numbers.*

:::{admonition} 🔍 Myth vs. Reality
:class: warning
**The myth:** "When an AI uses a word, it knows what the word means."

**The reality:** It knows how the word *behaves* — which words it tends to appear near, across billions of examples. That is powerful, and it is genuinely useful, and it is not the same as knowing what the word refers to in the real world. A language model has read the word "fire" in millions of sentences and can use it flawlessly; it has never been warm. Keep this in view, and the model's strange mix of brilliance and blind spots stops being mysterious.
:::

:::{figure} ../images/ch06/fig-6-2-tokenization.png
:label: fig-6-2
:alt: A sentence being cut into token pieces, and each token then turned into a short list of numbers, with similar-meaning tokens shown landing near each other.
:width: 90%
:align: center

**Figure 6.2.** *Text becomes tokens, tokens become numbers.* A machine cannot read a sentence — so it cuts the text into tokens and turns each into numbers, positioned so that words used alike land near each other.
:::

<!--
FIGURE 6.2 — concept infographic. Title: HOW A MACHINE READS LANGUAGE. STEP 1: a sentence in a
panel, then a coral arrow to the same sentence broken into separate rounded "token" chips.
STEP 2: a coral arrow from the token chips to a panel where each chip becomes a short bracketed
list of small numbers. STEP 3: a small "meaning map" panel — a scatter where the tokens "DOCTOR"
and "NURSE" sit close together and "BICYCLE" sits far away, captioned "SIMILAR WORDS, SIMILAR
NUMBERS". Deep teal panels and chips, coral arrows and accents, white background, faint circuit
margin motif. ai4educators master-infographic style. Reference: fig-1-1 for palette/finish.
Short labels and small numbers only, no garbled text.
-->

## 6.2 What Machines Do With Language

Once text is tokens and numbers, a trained model can do a range of useful jobs. Three are worth knowing by name, because you encounter all three daily.

**Sentiment analysis** judges the emotional tone of a piece of text — is this review positive, negative, or neutral? Is this support message angry or calm? A business with ten thousand customer reviews cannot read them all; sentiment analysis sorts them, surfacing the angriest and the happiest in seconds. A support team uses it to route a furious message to a senior agent first. It is pattern-matching on the tokens of emotion — and, as the ethics section will warn, it is far from perfect at it.

**Machine translation** converts text from one language to another. Modern translation does not swap word for word — that produces nonsense. It works through the numbers: it builds a numeric representation of the meaning of the whole sentence, then generates a sentence in the target language that carries that meaning. It is good enough now that a clinic can communicate with a patient who shares no language with the staff, and a small business can read a supplier's email from another country. It is not flawless — but it is a genuine bridge between people who could not otherwise speak.

**Speech recognition and speech synthesis** are the two halves of voice. **Recognition** turns spoken audio into text — it is what produces live captions, transcribes a meeting, and lets you dictate a message. **Synthesis** does the reverse, turning text into spoken audio — the voice of a navigation app, a screen reader, an audiobook. Together they are a profound accessibility technology: speech recognition gives a deaf student live captions of a lecture; speech synthesis lets a blind user hear any written page. Voice is also simply convenient — but its deepest value is in opening the world to people a text-only computer left out.

:::{admonition} 🛠️ In Practice: One inbox, three NLP tasks
:class: note
A community clinic gets a voicemail from a worried patient who speaks mostly Haitian Creole. Watch three NLP tasks chain together. **Speech recognition** transcribes the voicemail into text. **Machine translation** renders it into English for the front-desk staff. **Sentiment analysis** flags it as distressed, so it jumps the queue. Three technologies from this section, working in sequence — and notice that a human still makes the callback. The NLP did not replace the clinic's care; it removed the language and triage barriers in front of it.
:::

## 6.3 Large Language Models and the Transformer

Now to the engine of the current AI era — the technology behind Gemini and every assistant like it: the **large language model**, or LLM.

Strip away the awe and an LLM is, at its core, a next-word predictor. It was trained on an enormous body of human text — books, articles, websites, conversations — and from all of it, it learned the patterns of how language flows. Give it a string of text and it predicts the most likely next token. Then it adds that token and predicts the next. Then again. A whole fluent paragraph is built one predicted token at a time. It is, in a real sense, autocomplete — but autocomplete trained on a substantial fraction of everything humanity has written, which turns out to be enough to draft an essay, explain a concept, or carry a conversation.

What made this leap possible was a specific invention, and you met its name in Chapter 1: the **transformer**, introduced in 2017. Earlier language systems read text strictly in order and tended to "forget" the beginning of a long passage by the time they reached the end. The transformer's breakthrough is a mechanism called **attention**. When the model processes a particular word, attention lets it look at *all* the other words in the passage at once and weigh which ones actually matter for this word.

Consider the sentence: *"The trophy did not fit in the suitcase because it was too big."* What does "it" refer to — the trophy or the suitcase? You know instantly: the trophy. Attention is the mechanism that lets the model learn to make that link — to weigh "trophy" heavily when it processes "it." Multiply that ability across long passages and many layers, and you get a system that tracks meaning, reference, and context with startling skill.

But return to the honest center of this. An LLM predicts *plausible* text. Plausible usually overlaps with *true* and with *understood* — but not always, and the model cannot tell the difference. This is the deep reason behind the **hallucination** you met in Chapter 1: a confident, fluent, wrong answer is simply the model doing its only job — predicting plausible words — in a case where the plausible words happen to be false. Fluency is not understanding. Fluency is not truth. The most fluent machine ever built still needs you to check it.

:::{figure} ../images/ch06/fig-6-3-next-word-prediction.png
:label: fig-6-3
:alt: A diagram of a language model predicting the next word — a partial sentence, and several candidate next words each with a probability, the highest one chosen.
:width: 90%
:align: center

**Figure 6.3.** *An LLM predicts the next word.* Given the text so far, the model ranks likely next tokens by probability and picks one — then repeats. Whole paragraphs are built one prediction at a time.
:::

<!--
FIGURE 6.3 — concept infographic. Title: WHAT A LANGUAGE MODEL DOES. Center: a partial sentence
in a panel, e.g. "The community clinic opens at ___". A coral arrow to a short ranked list of
candidate next words, each with a small probability bar: "8 a.m. — 0.62", "nine — 0.21",
"dawn — 0.05" (illustrative). The top candidate is highlighted and shown being added to the
sentence, with a small loop arrow labelled "REPEAT" going back. A footer caption: "FLUENT IS NOT
THE SAME AS TRUE". Deep teal panels, coral arrows bars and accents, white background, faint
circuit margin motif. ai4educators master-infographic style. Reference: fig-1-1 for
palette/finish. Short labels and small numbers only, no garbled text.
-->

## 6.4 Chatbots: Three Kinds

A **chatbot** is any program you interact with through conversation. They are not all the same thing, and the differences matter — they decide how capable, how predictable, and how trustworthy a given bot is. There are three broad kinds, and it helps to see them as a spectrum.

**Rule-based chatbots** follow a script a human wrote — essentially a flowchart of keywords and canned replies. If the message contains "hours," reply with the hours. If it contains "refund," start the refund script. They are completely predictable, never invent anything, and are genuinely useful for narrow jobs — a bot that answers the same five front-desk questions. Their limit is total: ask anything the script does not anticipate and they fail. You will build one of these, in Python, in this chapter's optional lab — because building one is the clearest way to see exactly how a chatbot has no understanding at all.

**Retrieval-based chatbots** are a step up. Instead of generating language, they pick the best-fitting answer from a prepared library of responses, using the meaning-numbers from Section 6.1 to match your question to the closest stored answer. Better coverage than rules, and still safe — every possible answer was written and approved by a human.

**Generative chatbots** are the modern kind — the kind powering Gemini. They do not pick from a library; they *generate* a fresh response, token by token, with a large language model, taking in your message and the whole conversation so far. This is what makes them feel so capable and so human. It is also what makes them able to hallucinate. Power and risk arrive together, and they arrive for the same reason.

```{mermaid}
graph TD
    U["Your message"] --> A{What kind of chatbot?}
    A -->|Rule-based| R["Match a keyword,<br/>return a scripted reply"]
    A -->|Retrieval-based| B["Find the closest<br/>pre-written answer"]
    A -->|Generative| G["A language model<br/>generates a fresh reply"]
```

*Diagram 6.2. Three kinds of chatbot. They differ in where the reply comes from — a fixed script, a library of answers, or a language model generating one fresh.*

## 6.5 Hands-On Walkthrough: Build Your Own AI Assistant

You have used Gemini as a general assistant since Chapter 1. Now you will create a *specialized* one — a **Gem** — that behaves exactly the way you want, every time, without re-explaining yourself. A Gem is a custom version of Gemini that you build, and building one is building your own generative chatbot, with no code.

> **Verified as of May 2026.** If a screen looks different, the idea still holds — find the equivalent control.

<!--
FIGURE 6.4 — concept infographic, combine-into composition. Title: WHAT IS INSIDE A CUSTOM GEM.
Three input ingredient cards on the left, each with an icon and short label: "NAME" (a tag icon),
"INSTRUCTIONS" (a document with rule lines — drawn largest, marked as the most important), and
"KNOWLEDGE FILES — OPTIONAL" (a small file stack). Coral arrows from the three cards converge
into a single rounded panel on the right: a friendly assistant icon labelled "YOUR CUSTOM GEM".
A small caption under the instructions card: "THIS IS THE HEART OF IT". Deep teal cards and
panels, coral arrows and accents, white interiors, faint circuit margin motif. ai4educators
master-infographic style. Reference: fig-1-1 for palette/finish. Short labels only, no garbled text.
-->

:::{figure} ../images/ch06/fig-6-4-anatomy-of-a-gem.png
:label: fig-6-4
:alt: A diagram showing the parts of a custom Gem — a name, instructions, and optional knowledge files — combining into a finished custom AI assistant.
:width: 90%
:align: center

**Figure 6.4.** *Anatomy of a custom Gem.* A Gem is built from a name, a set of instructions, and optional knowledge files. The instructions are the heart of it — they are what make the assistant behave the way you want.
:::

**Step 1 — Open Gems.** Go to **gemini.google.com**, sign in, and find **Gems** in the left sidebar (look for "Explore Gems" or a Gems section). New Gems are created on the web; once made, a Gem can be used on the phone app too. Gems are **free** and available to anyone **13 or older**.

**Step 2 — Create a new Gem and name it.** Choose to create a new Gem and give it a clear name — "Study Coach," "Résumé Reviewer," "Recipe Helper." The name is for you; the next step is what matters.

**Step 3 — Write the instructions.** This is the heart of it. The instructions tell the Gem *who to be and how to behave* — its role, its tone, its rules, what it should and should not do. Compare a weak set of instructions with a strong one:

- Weak: *"Help me study."*
- Strong: *"You are a patient study coach for a college student. When I give you a topic, do not lecture — ask me one question at a time to test what I know, wait for my answer, then explain anything I got wrong in plain language. Never give me the full answer before I have tried. Keep a warm, encouraging tone."*

The strong version produces a genuinely different assistant. This is the prompt-writing skill from Chapter 1, leveled up: instead of instructions for one message, you are writing instructions for *every* conversation the Gem will ever have.

**Step 4 — Add knowledge (optional).** You can attach files — notes, a syllabus, a guide — as the Gem's knowledge. Now it answers from that material, a smaller echo of the grounding idea you met with NotebookLM in Chapter 2.

**Step 5 — Test and refine.** Use the preview to chat with your Gem. It is not behaving quite right? You do not argue with it — you go back and *edit the instructions.* The Gem is only ever as good as the instructions you wrote, exactly as a classifier is only as good as its training data and a chart is only as good as its source. The pattern of this whole book holds once more.

**Step 6 — Save it.** Your Gem now lives in your sidebar, ready whenever you need it — a custom chatbot you designed, reusable forever.

:::{admonition} ✋ Try This
:class: tip
Build a Gem with deliberately thin instructions ("help me write emails"). Chat with it. Then rewrite the instructions to be specific — the audience, the tone, the length, what to avoid. Chat again. The difference between the two is not the AI getting smarter. It is *you* getting clearer. That is the entire skill.
:::

:::{admonition} ⚖️ Ethics Check: Fluent, confident, and not neutral
:class: important
1. **Fluency is not truth.** A chatbot's answer is as polished when it is wrong as when it is right. Verify anything that matters — the habit from Chapter 1 never retires.
2. **Language models carry bias.** An LLM learned from human text, and absorbed its biases. It often performs *worse* on languages, dialects, and varieties of English that were underrepresented in its training — and a translation or a sentiment score can quietly encode a stereotype. A tool that works smoothly for one group and stumbles for another is a fairness problem, not a quirk.
3. **Disclose, and do not impersonate.** If people interact with a chatbot you built, they deserve to know it is a bot. And do not build a Gem to imitate a real, specific person without their consent.
4. **Your instructions are public-facing behavior.** The instructions you write *are* the assistant. If they are careless, the carelessness reaches every user. Write them as deliberately as you would write anything your name is on.
:::

## Chapter Summary

Natural language processing is how machines work with human language, and it rests on two ideas: **tokenization** cuts text into standard pieces, and each token becomes **numbers** (an **embedding**) positioned so that words used alike land near each other. On that foundation, machines perform **sentiment analysis**, **machine translation**, and **speech recognition and synthesis**. The engine of the modern era is the **large language model** — a next-word predictor trained on vast text — made possible by the **transformer** and its **attention** mechanism, which weighs which words matter for which. But an LLM predicts *plausible* text, which is why fluency is never proof of truth or understanding. **Chatbots** come in three kinds — rule-based, retrieval-based, and generative — and with **Gemini Gems** you built a generative one of your own, learning that an assistant is only ever as good as the instructions you write for it.

### Key Takeaways

- **Tokenization** cuts text into standard pieces; each token becomes **numbers** (an **embedding**), positioned so similar-meaning words land near each other.
- Core NLP tasks: **sentiment analysis** (emotional tone), **machine translation** (between languages), and **speech recognition and synthesis** (voice in and out).
- A **large language model** predicts the next token, over and over; the **transformer** and its **attention** mechanism made this work at scale.
- An LLM predicts **plausible** text — so **fluency is not understanding, and not truth.** Hallucination is this fact showing through.
- Chatbots are **rule-based**, **retrieval-based**, or **generative**; only generative chatbots create fresh language — and only they can hallucinate.
- A **Gem** is a custom AI assistant you build from **instructions**; it is only as good as those instructions — the recurring lesson of this book.

### Key Terms

**Natural language processing (NLP)** — the field of teaching machines to work with human language.
**Token** — a standard small piece of text (a word or word-part) that a model processes.
**Tokenization** — cutting text into tokens.
**Embedding** — the list of numbers representing a token, positioned by learned meaning.
**Sentiment analysis** — judging the emotional tone of a piece of text.
**Machine translation** — converting text from one language to another.
**Speech recognition** — converting spoken audio into text.
**Speech synthesis** — converting text into spoken audio.
**Large language model (LLM)** — a model trained on vast text that predicts the next token.
**Transformer** — the 2017 neural-network design behind modern language models.
**Attention** — the transformer mechanism that weighs which words matter for which.
**Chatbot** — a program you interact with through conversation.
**Generative chatbot** — a chatbot that generates fresh replies with a language model.
**Gem** — a custom AI assistant built in Gemini from instructions you write.

### Bridge to Chapter 7

You have seen machines work with language and with images. Chapter 7, **Generative Media**, follows the generative thread to its current frontier: AI that creates **video, sound, and multimodal media** — and what it means to live in a world where convincing media of anything can be made from a sentence. You will look at how these systems work, where they fail, and how AI-made media is labeled — and you will try a generative media tool yourself.

---

## Apply and Analyze

The instructor-led walkthrough in Section 6.5 is the demonstration for this chapter. What follows is your turn — to check your understanding, build a Gem of your own, and reflect.

### Review Questions

1. **What is "tokenization" in natural language processing?**
   A. Translating text into another language.
   B. Cutting text into standard small pieces a model can process.
   C. Judging the emotional tone of text.
   D. Converting speech into text.

2. **An embedding positions the words "doctor" and "nurse" close together and "bicycle" far away because:**
   A. The words were placed alphabetically.
   B. A human manually sorted every word.
   C. The numbers are learned so words used in similar ways get similar values.
   D. Shorter words are always closer together.

3. **True or False:** A large language model works mainly by repeatedly predicting the next token.

4. **Which kind of chatbot generates a fresh reply with a language model rather than choosing from pre-written answers?**
   A. Rule-based.
   B. Retrieval-based.
   C. Generative.
   D. None of them generate replies.

5. **True or False:** Because a chatbot's answer is fluent and confident, it can be trusted as accurate.

:::{dropdown} Answer Key
1. **B** — tokenization cuts text into standard pieces.
2. **C** — embeddings are learned so similarly-used words get similar numbers.
3. **True** — an LLM repeatedly predicts the next token.
4. **C** — generative chatbots generate fresh replies with a language model.
5. **False** — fluency is not truth; an LLM predicts plausible text and can be confidently wrong.
:::

### Discussion Question

Think about a conversation you have had with an AI assistant. At what moment, if any, did it feel like the machine "understood" you? Knowing now that an LLM predicts plausible words rather than grasping meaning the way you do, does that change how much you trust it — and for which kinds of tasks? Where is the line between a task you would hand to a generative chatbot and one you would not? Support your answer with at least one specific idea from this chapter.

### Breakout Lab: Build a Gem

Work in a group of three or four. Total time: about 35–45 minutes. Low-stakes — the goal is to *build something that works.*

1. **Choose a purpose (5 min).** As a group, pick one genuinely useful, specific assistant — a study coach for a particular course, a helper that drafts professional emails, a guide for a campus process.
2. **Write the instructions together (15 min).** Apply Section 6.5: define the Gem's role, tone, rules, what it must do, and what it must never do. Write the instructions out before building.
3. **Build and test it (15 min).** Create the Gem in Gemini, paste in your instructions, and test it with at least four different messages — including one designed to make it misbehave.
4. **Refine (5 min).** Based on the test, improve the instructions at least once. Note what you changed and why.
5. **Share (5 min).** Each group demonstrates its Gem and reads its final instructions aloud.

**Submit:** your Gem's final instructions, four test messages with the Gem's responses, and three sentences on what you changed after testing and why. Due at the end of class.

### Optional Advanced Lab: Build a Chatbot in Python

<a href="https://colab.research.google.com/github/c-marq/cai1001c-ai-thinking/blob/main/notebooks/ch06-build-a-chatbot.ipynb" target="_blank">
<img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab" style="margin-bottom: 1rem;"/>
</a>

*Optional, and assigned at your instructor's discretion.* You built a generative chatbot as a Gem with no code. This lab builds the *other* kind — a **rule-based chatbot** — in Python, in Google Colab, free in your browser, with nothing to install. You will write the keyword rules yourself, chat with your bot, and see plainly that a rule-based chatbot has no understanding at all — it only matches keywords to scripted replies. That contrast is the lesson: it shows you exactly what a generative model adds, and what it risks. Click the badge above to open it.

### Optional Take-Home: Going Deeper

*Assigned at your instructor's discretion.* Extend your group's Gem on your own.

- Give your Gem three test messages in deliberately casual, non-standard, or mixed-language English. Note honestly how well it handled each.
- Then reflect in writing (about 300 words): An LLM often performs worse on languages, dialects, and varieties of English that were underrepresented in its training. If your Gem stumbled on the non-standard messages, who would that disadvantage in a real deployment — and is that a "bug" or a predictable result of how the model learned? Your Gem's behavior is set entirely by the instructions you wrote and the model underneath; when it gives a harmful or biased answer, who is responsible — and why is "the AI said it" not a sufficient answer?
