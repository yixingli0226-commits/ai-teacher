# Teaching Heuristics

Use this reference when analyzing real lecture transcripts and slides.

## Configuration Heuristics

Use `config/defaults.yaml` as the default behavior. If the user chooses a mode or custom settings, let that override defaults for the current session.

Recommended defaults:

- Mode: classroom
- Language: match the user's language with only essential original-language terms preserved
- Transcript/slides weighting: 6.5/3.5
- Framework pacing: one framework at a time
- Quiz: AI-decided mixed questions
- Difficulty: adaptive
- Summary: concise review notes with Mistake Highlights

Offer three simple modes before advanced options:

- Classroom Mode for steady learning.
- Exam Mode for high-yield drilling.
- Fast Review Mode for quick recall.

Only expose advanced customization when the user asks for it or rejects the modes.

## Source Weighting

Default weighting for lecture priority inference:

- Transcript: 6.5 / 10
- Slides/PPT: 3.5 / 10

This means the transcript should drive the judgment of what the instructor cared about most, while slides protect against missing formal material.

Use transcript-heavy evidence for:

- repeated explanations
- spoken examples
- warnings and misconceptions
- exam, assignment, or homework cues
- student questions and instructor clarifications
- time spent on a topic

Use slide-heavy evidence for:

- exact definitions
- formulas, equations, code snippets, or procedures
- diagrams, graphs, and tables
- official terminology
- step order
- topics visually present but under-explained verbally

If a topic is strong in both transcript and slides, treat it as high priority. If it is strong only in the transcript, treat it as likely instructor emphasis. If it is strong only in the slides, treat it as formal material that may still be examinable, but check whether it was background or required setup.

## Evidence For Instructor Emphasis

Strong signals:

- The instructor repeats the same idea in different words.
- The instructor spends much more time on one slide than neighboring slides.
- The instructor gives a numerical example, story, case, demo, derivation, or code walkthrough.
- The instructor says phrases like "important", "key", "remember", "exam", "assignment", "common mistake", "intuition", "why", or "do not confuse".
- Students ask questions and the instructor clarifies.
- The instructor contrasts two similar concepts.
- The transcript explains assumptions not visible on the slide.

Weak signals:

- A term appears only once on a crowded slide.
- A formula, definition, or diagram is listed but never explained or used.
- A slide is administrative or transitional.
- A transcript segment is logistical rather than conceptual.

## Transcript Noise And Correction

Lecture transcripts are often produced by automatic speech recognition. Expect errors in names, terms, acronyms, formulas, punctuation, numbers, code tokens, and domain-specific vocabulary.

Before interpreting a strange phrase, check:

- Does the slide contain a similar term, formula, diagram, or code snippet?
- Does the sentence make sense if one word is replaced by a common course term?
- Is the phrase a homophone or near-homophone of a domain term?
- Is the speaker likely referring to a named concept, acronym, author, theorem, law, model, ticker, or variable?
- Would missing punctuation, a negative sign, decimal, percent, unit, or symbol change the meaning?

Use corrections conservatively. If the correction is obvious from slides and context, silently use the corrected term. If the correction affects teaching or assessment emphasis and confidence is low, ask the user before relying on it.

## Slide-Transcript Alignment

Prefer direct alignment by slide title, displayed term, formula, example name, timestamp, page number, or sequence. If those fail, align by concept order:

1. Definitions and motivation
2. Model, method, procedure, or argument setup
3. Example, demo, case, or application
4. Interpretation
5. Limitations, mistakes, or assessment cues

When alignment is uncertain, state the uncertainty briefly and continue.

## Teaching Framework Design

Before teaching a full lecture, divide it into 5-10 frameworks. The number should reflect teaching rhythm:

- Use 5 frameworks for a short or conceptually simple lecture.
- Use 6-8 frameworks for a normal lecture.
- Use 9-10 frameworks for dense lectures with multiple models, procedures, examples, or assessment-relevant contrasts.

A framework is a teaching unit, not a slide count. Combine slides when they support one idea. Split a slide when it contains several different concepts or tasks.

Each framework should include:

- title
- slide range or transcript range if available
- instructor emphasis signal
- learning goal
- key terms
- what the student should be able to do after the framework

Default behavior is to teach one framework and pause. Continue only after the user asks for the next framework.

## Tutoring Style

Use a professor's logic but a tutor's pacing:

1. What problem does this concept solve?
2. What is the mechanism or idea?
3. What example makes it concrete?
4. How does it connect to the instructor's wording or slides?
5. What quick question checks understanding?

For formulas, definitions, procedures, or code:

- Explain what each symbol, term, or step means.
- Explain the assumption or context that makes it valid.
- Explain what changes when the assumption fails.
- Explain how to interpret the result.

## Assessment Preparation

Convert instructor emphasis into likely task types:

- define and distinguish concepts
- set up a calculation, proof, argument, model, or procedure
- interpret a result in plain language
- identify which assumption matters
- apply a concept to a new case
- explain why a tempting wrong answer is wrong

Do not overfit to slides alone. If the transcript spends time on interpretation, make interpretation part of the review even if the slide looks formula-heavy.

## Interactive Review Design

Build review questions from the instructor's emphasis map. Do not create generic trivia.

Good interactive questions test whether the learner can:

- distinguish concepts the instructor contrasted
- set up the right method before calculating or answering
- interpret direction, magnitude, implication, or result
- identify assumptions behind a model or argument
- transfer the lecture example to a similar case
- explain why a tempting wrong answer is wrong

Prefer 2-4 questions per framework and 5-8 questions per whole lecture review. Use more only when the user asks for exam drilling.

## Summary Document Design

When the user asks "总结文档", "create summary document", "generate review notes", or "make a review document", create a compact review document, not a long prose recap.

Use the original teaching framework as the document skeleton. The goal is quick memory recovery:

- What did I learn in each framework?
- What are the key terms or procedures?
- Which formulas, definitions, arguments, or methods matter?
- What did the instructor emphasize?
- What did I personally get wrong?

Keep each framework section short. Prefer precise bullets over paragraphs. Remove repeated explanations from earlier teaching.

Mistake Highlights should be personal and concrete. Include only mistakes or weak answers actually observed in the tutoring conversation. For each mistake, state the concept, the user's incorrect reasoning if available, the corrected idea, and a review action.

## Chat Presentation

Prefer structured Markdown over plain text. Use tables when they reduce repetition:

- framework roadmap table
- key terms table
- formula/procedure/definition table
- Mistake Highlights table
- fast review checklist

Avoid:

- long uninterrupted paragraphs
- transcript-like output
- repeating the same explanation in multiple sections
- putting normal prose inside code fences
- overly decorative formatting that distracts from studying
