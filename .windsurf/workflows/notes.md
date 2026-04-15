---
description: Convert raw college lesson transcript into clean, faithful, open-note study note
---

You are converting a raw college lesson transcript into a clean, faithful, open-note study note.

## Input Context

The input will usually be a copied lesson transcript from an AAS in AI Software Engineering program.

The transcript may include:
- school/program header text
- email/account text
- course code
- lesson title
- lesson date
- tutor explanations
- student answers
- quiz questions
- code editor submissions
- confirmations/corrections
- motivational filler
- navigation text like “Message Maestro...” or “Next Lesson”
- repeated explanations caused by the interactive tutoring format

The raw input is often an interactive tutor transcript, not a polished lesson article.

Your job is to preserve the useful lesson content as closely as possible while removing transcript noise and formatting it into a better open-note reference.

Do not write a brand-new article.
Do not aggressively summarize away important teaching content.
Do not make the notes bloated or overly complicated.

## Courses This Workflow Must Handle

Use the course code, lesson title, filename, and lesson content to infer the lesson type.

Known course families:

- PY101 · Introduction to Python programming
- PY103 · Object-Oriented Programming
- CS101 · Software engineering principles
- CS102 · Data structures & algorithms
- FE101 · Introduction to modern JavaScript & TypeScript
- FE102 · Building interactive UIs
- FE103 · Frontend integration project
- BE101 · Web fundamentals
- BE102 · RESTful API Development
- BE103 · Databases: SQL & NoSQL Basics
- BE104 · Authentication, Authorization, and Middleware
- BE105 · Advanced Backend Concepts and Microservices
- BE106 · Backend project
- AI101 · Introduction to AI concepts & math foundations
- AI102 · Fundamentals of machine learning
- AI103 · Prompt engineering & working with LLMs
- AI104 · Applied AI capstone project
- MATH100 · College mathematics
- PSYC100 · General psychology
- HIST200 · American history since World War II
- ENVR100 · Global Environmental Change
- ENGL100 · English composition
- SPH100 · Essentials of public speaking
- CD101 · Professional profiles and personal branding
- CD102 · AI project portfolio development
- CD103 · AI career strategy and interview preparation
- CD104 · AI career launch workshop

## Core Goal

Create a markdown note that is:

- faithful to the original lesson
- cleaner than the transcript
- useful for open-note quizzes, assignments, and review
- concise but not shallow
- structured based on the lesson type
- easy to scan
- practical and actionable
- accurate

Preserve:
- definitions
- key terms
- rules
- steps
- examples
- code
- formulas
- dates
- names
- cause/effect relationships
- warnings
- comparisons
- final mastery points
- important “why this matters” explanations

Remove:
- account/email header noise
- motivational filler
- repeated tutor encouragement
- chat back-and-forth formatting
- accidental or incomplete student entries
- “Message Maestro...” text
- platform navigation text
- repeated confirmations
- unnecessary transcript chatter

## Student Attempts and Corrections

Do not preserve failed attempts as events.

Do not write things like:
- “The student answered incorrectly...”
- “You first wrote...”
- “The tutor corrected you...”

Instead, preserve only the lesson value:
- the correct method
- the reason it works
- what not to do
- the common pitfall
- the corrected final code or concept

If a correction reveals an important rule, include it under:
- “Common Mistakes”
- “What Not to Do”
- “Important Distinction”
- “Debugging Note”

Only include failed/incorrect code if it is genuinely useful as a brief “what not to do” example.

## Use of Examples

Examples are encouraged when they improve understanding, especially for:
- programming
- software engineering
- data structures
- APIs
- databases
- frontend/backend development
- AI/ML
- math

Examples must be:
- accurate
- directly related to the lesson
- short enough to be useful
- not filler

Prefer examples from the original lesson when available.

You may add a small clarifying example only when it directly improves understanding.

## Length Control

Keep the note compact enough for open-note use.

Default target:
- usually 600–1,500 words
- shorter if the lesson is simple
- longer only when the lesson genuinely needs it, such as code-heavy, algorithm-heavy, or formula-heavy lessons

Do not create giant notes.
Do not preserve every repeated sentence.
Do not add long outside explanations.

## Universal Output Structure

Use this as the default backbone, but adapt it to the lesson type.

```md
# [Clean Lesson Title]

## 1. Lesson Focus
[Plain-language explanation of what the lesson teaches.]

## 2. Core Concepts
[Main definitions, ideas, rules, and distinctions.]

## 3. Key Details to Remember
[Important facts, syntax, names, dates, formulas, terms, or steps.]

## 4. How It Works / How to Apply It
[Process, method, reasoning, workflow, or application.]

## 5. Examples
[Useful examples from the lesson, cleaned up. Add brief related examples only if helpful.]

## 6. Common Mistakes / What Not to Do
[Misunderstandings, traps, unsafe assumptions, syntax issues, edge cases, or incorrect reasoning.]

## 7. Open-Note Review
[Compact review bullets, mini checklist, or likely quiz-answer material.]

## 8. Final Takeaway
[The main idea to remember.]
````

Do not force every section if it does not fit.
Rename sections when a subject-specific title is clearer.
Add subject-specific sections when useful.

## Subject-Specific Rules

### Programming / Python / JavaScript / TypeScript / Frontend / Backend

For PY, FE, BE, and coding-heavy lessons:

Prioritize:

* syntax
* code structure
* clean examples
* expected output
* common errors
* debugging notes
* edge cases
* implementation steps
* practical usage

Useful sections may include:

* Syntax Pattern
* Clean Code Example
* Annotated Code Example
* Expected Output
* Step-by-Step Process
* Common Errors
* Edge Cases
* Debugging Notes

For code lessons:

* include clean final code when useful
* include annotated code when it helps explain syntax or logic
* preserve important code from the lesson
* remove accidental or incomplete student code
* explain what the code does and why it works
* keep examples runnable when possible

### CS / Software Engineering / Data Structures / Algorithms

For CS101 and CS102:

Prioritize:

* concepts
* mental models
* design reasoning
* algorithms
* data structures
* tradeoffs
* complexity
* reliability
* edge cases
* testing
* professional practices

Useful sections may include:

* Mental Model
* Algorithm / Process
* Complexity
* Tradeoffs
* Reliability Pattern
* Edge Cases
* Testing Checklist
* Implementation Notes

For algorithm/data-structure lessons:

* preserve operations
* include time/space complexity when present or directly relevant
* include edge cases
* include safe implementation patterns
* include concise code only when useful

### AI / Machine Learning / LLMs

For AI101–AI104:

Prioritize:

* definitions
* math intuition
* model behavior
* workflows
* limitations
* prompt patterns
* evaluation
* examples
* practical application

Useful sections may include:

* Core Idea
* Key Terms
* How the Model/System Works
* Math Intuition
* Practical Workflow
* Limitations
* Example
* Evaluation / Review

Keep explanations practical and clear.
Do not overcomplicate math unless the lesson requires it.

### Math / Statistics

For MATH100 or math-heavy AI lessons:

Prioritize:

* formulas
* variables
* worked examples
* interpretation
* units
* common mistakes
* when to use the method

Useful sections may include:

* Formula
* What Each Variable Means
* Worked Example
* Interpretation
* Common Mistakes
* Quick Practice Pattern

Always explain what the result means in plain language.

### Psychology / Social Science

For PSYC100:

Prioritize:

* definitions
* theories
* researchers
* experiments
* mechanisms
* cause/effect
* real-world applications
* practical implications

Useful sections may include:

* Core Claim
* Key Terms
* Theory / Research
* Mechanism
* Example
* Application
* Common Misunderstandings
* Final Takeaway

Preserve named theories, researchers, experiments, and important distinctions.

### History / Humanities

For HIST200 and similar prose-heavy lessons:

Prioritize:

* key people
* events
* dates
* chronology
* cause/effect
* institutions
* systems
* historical significance
* comparisons

Useful sections may include:

* Historical Context
* Key Terms
* Timeline
* Cause-and-Effect Chain
* Main Events / Systems
* Why It Mattered
* Comparison
* Common Misunderstandings

For lessons built around a chain, preserve the chain clearly, such as:

problem → response/funding → breakthrough → consequence

### Environmental Science

For ENVR100:

Prioritize:

* systems
* causes
* effects
* feedback loops
* evidence
* key terms
* human impact
* environmental consequences
* mitigation/adaptation

Useful sections may include:

* System Overview
* Causes
* Effects
* Feedback Loops
* Evidence
* Human Impact
* Solutions / Responses
* Key Takeaway

### English / Public Speaking / Career Development

For ENGL100, SPH100, and CD courses:

Prioritize:

* frameworks
* communication techniques
* writing/speaking structure
* examples
* templates
* dos/don’ts
* practical application
* checklists

Useful sections may include:

* Framework
* Process
* Template
* Example
* Checklist
* Common Mistakes
* Application

For career/profile lessons:

* preserve concrete action steps
* preserve resume/profile/interview advice
* format templates clearly
* avoid generic fluff

## Handling Interactive Tutor Transcripts

If the input is a tutor/student transcript:

1. Identify the actual lesson topic.
2. Extract the teaching content.
3. Preserve the useful examples and exercises.
4. Remove repeated tutor prompts.
5. Remove accidental student submissions.
6. Convert quiz questions into review points when useful.
7. Convert final recap into a clean summary.
8. Preserve the lesson’s progression when it helps learning.

Do not preserve the chat format.

## Handling Quizzes and Checkpoints

If the transcript includes multiple-choice questions:

* preserve the correct answer only if useful
* explain why briefly
* do not include every option unless the options clarify a common misconception

If a question is a useful review prompt, include it in “Open-Note Review.”

## Handling Code

When code appears:

* clean formatting
* use fenced code blocks
* keep code runnable when possible
* preserve important syntax
* include expected output if useful
* avoid excessive duplicate snippets
* prefer one clean final version over many partial versions

For Python, use:

```python
# code here
```

For JavaScript/TypeScript, use:

```js
// code here
```

or:

```ts
// code here
```

For SQL, use:

```sql
-- code here
```

## Handling Metadata

At the top, include a small metadata block only when available:

```md
> Course: [COURSE CODE]
> Lesson: [LESSON TITLE]
> Date: [DATE, if useful]
```

Do not include:

* email
* school account text
* platform footer text
* “Message Maestro”
* motivational intro text

## Accuracy Rules

Do not invent facts.
Do not add unrelated outside material.
Do not over-explain beyond the lesson.
Do not silently change the meaning of the lesson.
Do not use examples that could confuse the concept.
Do not add advanced material unless it directly clarifies the lesson.

If something in the transcript is unclear, preserve the safe version and avoid overclaiming.

## Final Output Requirements

Output only the finished markdown note.

Do not explain your process.
Do not mention that you inferred the lesson type.
Do not mention these instructions.
Do not include a preface.
Do not include follow-up questions.