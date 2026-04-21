# Finance Teacher Skill

`finance-teacher` is a Codex skill for re-teaching finance lectures from a professor's PPT/slides and lecture transcript.

It is designed for learners who want a tutor to infer what the instructor actually wanted students to learn, rather than only summarizing slide headings.

## What It Does

- Uses both lecture transcripts and PPT/slides.
- Weights the transcript at 6.5/10 and the PPT/slides at 3.5/10 when inferring lecture priorities.
- Uses the transcript for emphasis, pacing, teacher intent, examples, warnings, and exam cues.
- Uses the PPT/slides for formal definitions, formulas, diagrams, tables, official terminology, and structure.
- Handles imperfect automatic transcripts with possible spelling or recognition errors.
- Builds a 5-10 frame teaching roadmap before teaching.
- Teaches one frame at a time and waits for the learner to say "next frame" or "下一个框架".
- Explains mainly in Chinese, while preserving only essential finance terms in English.
- Adds interactive review questions after each frame or lecture.
- Creates a concise Word review document when the learner says "总结".

## Folder Structure

```text
finance-teacher-skill/
├─ finance-teacher/
│  ├─ SKILL.md
│  ├─ agents/
│  │  └─ openai.yaml
│  └─ references/
│     └─ teaching-heuristics.md
├─ README.md
├─ LICENSE
└─ .gitignore
```

## Installation

Copy the `finance-teacher` folder into your Codex skills directory.

On macOS or Linux:

```text
~/.codex/skills/finance-teacher
```

On Windows:

```text
C:\Users\<YourName>\.codex\skills\finance-teacher
```

Then restart Codex so the skill can be discovered.

## Basic Usage

Upload the PPT and transcript for the lecture, then ask:

```text
Use $finance-teacher.

The uploaded PPT and transcript are the primary materials for today's lecture.
Other files in the folder are background knowledge only.
Please infer the professor's priorities from the primary materials.
Use background knowledge only to clarify concepts or prerequisites.
Build a 5-10 frame roadmap, then teach me one frame at a time.
```

Chinese prompt example:

```text
Use $finance-teacher。

我上传的 PPT 和 transcript 是今天这节课的主材料。
文件夹里的其他资料都是 background knowledge。
请只根据主材料判断老师真正想让我学什么。
用中文讲解，只在核心金融术语上保留英文。
先生成 5-10 个 framework，然后一个 framework 一个 framework 教我。
讲完每个 framework 后用选择题互动复习。
```

When you finish a course or lecture sequence, say:

```text
总结
```

The skill will create a concise Word review document with framework notes and mistake highlights.

## Teaching Philosophy

The skill treats the transcript as the stronger signal for what the teacher cared about, but it still uses slides to avoid missing formulas, diagrams, definitions, and official terminology.

It avoids dumping the whole lecture at once. Instead, it creates a structured teaching rhythm:

```text
Preview -> Explain -> Example -> Connect -> Check -> Recap -> Pause
```

## License

MIT
