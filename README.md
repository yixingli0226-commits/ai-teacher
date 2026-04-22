# AI Teacher Skill

`ai-teacher` is a Codex skill that turns lecture materials into an interactive AI tutor.

It is designed for any course where a learner has:

- lecture slides or PPT files
- a professor's lecture transcript
- optional notes, readings, problem sets, or background materials

Instead of only summarizing slides, the skill combines the transcript and slides to infer what the instructor actually wanted students to learn. It then builds a teaching roadmap, teaches one framework at a time, asks interactive review questions, tracks weak points, and can generate concise review notes.

## What This Skill Does

- Re-teaches lectures from slides plus transcripts.
- Works across many subjects: business, economics, computer science, math, statistics, biology, medicine, law, social science, humanities, language learning, and more.
- Separates today's primary materials from background knowledge.
- Weights the transcript at 6.5/10 and the slides at 3.5/10 by default when inferring lecture priorities.
- Uses transcripts to detect teacher emphasis, examples, warnings, repeated points, exam cues, and explanations.
- Uses slides to preserve structure, definitions, formulas, diagrams, tables, terminology, and visual material.
- Handles imperfect transcripts with spelling errors, recognition mistakes, broken punctuation, and misheard terms.
- Builds a 5-10 framework roadmap before teaching.
- Teaches one framework at a time instead of dumping the whole lecture at once.
- Adds interactive review questions after each framework.
- Lets users customize language, pacing, source weights, quiz type, difficulty, and feedback style.
- Provides Classroom Mode, Exam Mode, Fast Review Mode, and Advanced Custom Mode.
- Creates a concise review document when the user says `总结文档`, `create summary document`, or `generate review notes`.
- Records wrong or weak answers for a final Mistake Highlights section.
- Keeps private course materials out of the open-source repository.

## Core Idea

Slides show the official structure of a lecture. Transcripts reveal how the instructor actually taught it.

`ai-teacher` uses both:

| Source | Default weight | Best for |
|---|---:|---|
| Transcript | 6.5 / 10 | Emphasis, examples, explanations, warnings, exam cues, teacher intent |
| Slides / PPT | 3.5 / 10 | Definitions, formulas, diagrams, tables, structure, official terminology |

The transcript has more weight for deciding what matters, but the slides protect against missing formal material.

## Folder Structure

```text
ai-teacher/
|-- ai-teacher/
|   |-- SKILL.md
|   |-- agents/
|   |   `-- openai.yaml
|   |-- config/
|   |   `-- defaults.yaml
|   `-- references/
|       `-- teaching-heuristics.md
|-- README.md
|-- LICENSE
`-- .gitignore
```

The actual Codex skill folder is:

```text
ai-teacher/
```

Inside that folder, `SKILL.md` is the required skill entry point.

## Installation

Codex discovers a skill when the skill folder itself is directly inside your Codex skills directory.

### Option 1: Download ZIP

1. Open this GitHub repo.
2. Click `Code` -> `Download ZIP`.
3. Unzip the file.
4. Copy the inner `ai-teacher` folder into your Codex skills directory.
5. Restart Codex.

### Option 2: Clone With Git

```bash
git clone https://github.com/yixingli0226-commits/ai-teacher.git
```

Then copy:

```text
ai-teacher/ai-teacher
```

to:

```text
~/.codex/skills/ai-teacher
```

On Windows:

```text
C:\Users\<YourName>\.codex\skills\ai-teacher
```

The final path should be:

```text
~/.codex/skills/ai-teacher/SKILL.md
```

Do not place only the whole GitHub repo inside `.codex/skills` and expect Codex to discover it automatically.

## Quick Start

Upload the PPT/slides and lecture transcript for one class, then ask:

```text
Use $ai-teacher.

The uploaded slides and transcript are the primary materials for today's lecture.
Other files in the folder are background knowledge only.
Infer the instructor's priorities from the primary materials.
Use background knowledge only to clarify concepts or prerequisites.
Build a 5-10 framework roadmap, then teach me one framework at a time.
```

Chinese example:

```text
Use $ai-teacher。

我上传的 PPT 和 transcript 是今天这节课的主材料。
文件夹里的其他资料都是 background knowledge。
请只根据主材料判断老师真正想让我学什么。
先生成 5-10 个 framework，然后一个 framework 一个 framework 教我。
每个 framework 结束后用互动题巩固我。
```

When you finish a course or lecture sequence, say:

```text
总结文档
```

Or in English:

```text
create summary document
```

The skill will create a concise review document with framework notes and Mistake Highlights.

## Setup Mode

To configure the tutor before using it:

```text
Use $ai-teacher. Setup ai-teacher.
```

Chinese:

```text
Use $ai-teacher。配置 ai-teacher。
```

The setup flow can customize:

- language mode
- transcript/slides weighting
- framework pacing
- quiz type
- difficulty
- feedback style
- summary document style
- background knowledge policy

Default settings live in:

```text
ai-teacher/config/defaults.yaml
```

## Learning Modes

| Mode | Best for | Behavior |
|---|---|---|
| Classroom Mode | Learning after class | Balanced explanation, 5-10 frameworks, one framework at a time, adaptive questions |
| Exam Mode | Test preparation | More high-yield points, likely question types, traps, formulas, and mistake repair |
| Fast Review Mode | Quick recall | Shorter explanations, fewer checks, compact framework summaries |
| Advanced Custom Mode | Power users | User controls language, weights, quiz type, difficulty, pacing, and summary style |

## Quiz Customization

Supported quiz modes:

- AI decides
- Multiple choice only
- True/false only
- Short answer only
- Calculation-heavy
- Mini-case-heavy
- Custom mix

By default, the skill chooses question types based on the lecture content. A normal framework should include a concept check, an application or setup question, and a misconception/trap question when appropriate.

## Output Style

The skill avoids long plain-text dumps. It uses:

- roadmap tables
- clear headings
- compact bullets
- formula or definition blocks when useful
- key term tables
- interactive question cards
- Mistake Highlights tables

## Privacy And Copyright

Do not commit real course materials to GitHub. Lecture slides, transcripts, recordings, textbook PDFs, screenshots, and private notes may be copyrighted or private.

This repo's `.gitignore` excludes common course-material folders and file types such as:

```text
materials/
lectures/
transcripts/
slides/
*.pptx
*.pdf
*.docx
*.mp3
*.mp4
```

Use fake sample content or openly licensed material for public examples.

## License

MIT
