# Markdown Generation Skill

You are generating a Markdown document. Follow these rules strictly to produce readable, well-structured output.

---

## Part 1: Universal Rules (Apply to ALL documents)

### 1.1 Heading Hierarchy

MUST:
- Use exactly one H1 (`#`) per document — the document title only
- Use H2 (`##`) for major sections
- Use H3 (`###`) for subsections within an H2
- Never skip levels (e.g., H1 → H3 is forbidden)

MUST NOT:
- Use H4 or deeper unless the document is explicitly a long-form reference (>2000 words)
- Use bold text as a substitute for headings
- Add a heading for every paragraph — headings mark sections, not sentences

---

### 1.2 Bold and Italic

MUST:
- Bold (`**text**`) only for genuinely critical terms, warnings, or key concepts — maximum 1-2 per paragraph
- Italic (`*text*`) only for titles of works, technical terms on first introduction, or necessary emphasis

MUST NOT:
- Bold entire sentences or phrases for decoration
- Use bold to highlight things that are merely "interesting"
- Use italic for general emphasis — that's what sentence structure is for
- Combine bold + italic (`***text***`) unless absolutely necessary

Rule of thumb: if everything is emphasized, nothing is.

---

### 1.3 Lists

Use lists ONLY when the content is genuinely enumerable. Apply this decision tree:

- Is the content a sequence of steps? → Ordered list (`1. 2. 3.`)
- Is the content 3+ parallel items with no natural prose flow? → Unordered list (`-`)
- Is the content fewer than 3 items, or flows naturally as a sentence? → Write as prose

MUST NOT:
- Convert continuous reasoning into bullet fragments
- Use nested lists more than 2 levels deep
- Put more than 7 items in a single list without grouping under subheadings
- Start every section with a bullet list instead of an introductory sentence

---

### 1.4 Code Blocks

MUST:
- Always specify the language for fenced code blocks: ` ```python `, ` ```bash `, ` ```typescript `, etc.
- Use inline code (`` `code` ``) for: variable names, function names, file paths, CLI commands inline with text, technical identifiers
- Keep code blocks self-contained — include necessary imports or context

MUST NOT:
- Use inline code for general emphasis or non-technical terms
- Use code blocks for non-code content (config values that aren't actual code, plain text examples)
- Leave language identifier blank on fenced blocks

---

### 1.5 Tables

Use tables ONLY when comparing multiple entities across multiple attributes simultaneously.

Valid use: comparing 3 libraries across 4 properties.
Invalid use: a 2-column "term / definition" table (use a list or prose instead).

MUST NOT:
- Use tables for simple key-value pairs (use a list)
- Use tables for sequential steps (use an ordered list)
- Create tables with more than 6 columns — split or restructure instead

---

### 1.6 Visual Spacing and Rhythm

MUST:
- Add one blank line between paragraphs
- Add one blank line before and after every heading, list, code block, and table
- Add two blank lines between major H2 sections in longer documents (>500 words)

MUST NOT:
- Stack multiple headings without any body text between them
- Write walls of text longer than 5-6 sentences without a break
- Add blank lines between individual list items (unless items are multi-paragraph)

---

### 1.7 Writing Style — Eliminating Redundancy

MUST NOT include any of the following patterns:

**Forbidden openers:**
- "In this document, we will..."
- "This article covers..."
- "Let's dive into..."
- "In this section, we'll explore..."

**Forbidden closers:**
- "In summary, we learned that..."
- "To summarize the above..."
- "As we can see from the above..."
- "I hope this helps!"

**Forbidden filler phrases:**
- "It's worth noting that..."
- "Please note that..."
- "It is important to mention..."
- "As mentioned earlier..."
- "Needless to say..."

Start sections directly with content. End when the content is complete.

---

## Part 2: Scene-Specific Rules

Detect the document type from context (user request, title, content) and apply the matching template.

---

### 2.1 Technical Note / Learning Note

Trigger: user asks to "整理笔记", "总结知识点", "记录学习", or the topic is a technology/framework/language concept.

Structure (in order):
1. **Concept** — one paragraph, plain language definition. No jargon without explanation.
2. **Why it matters** — one paragraph. What problem does it solve? Skip if obvious.
3. **How it works** — the core mechanism. Use prose first, diagrams/lists only if structure genuinely helps.
4. **Usage / Examples** — concrete code examples with language tags. Show real usage, not toy examples.
5. **Gotchas / Caveats** — only include if there are genuine non-obvious pitfalls. Skip if none.
6. **References** — links only, no prose. Skip if none.

Rules:
- Do not add a section if you have nothing meaningful to say in it
- Code examples must be runnable or clearly marked as pseudocode
- Prefer one good example over three mediocre ones

---

### 2.2 Project Documentation

Trigger: README, API docs, architecture docs, setup guides, contribution guides.

Structure (in order):
1. **Title + one-line description** — what this project does, in one sentence
2. **Quick Start** — minimum steps to get something running. Numbered list. No theory here.
3. **What / Why** — what problem this solves, why this approach. Keep it short.
4. **How it works** — architecture overview, key concepts. Use diagrams if helpful.
5. **Configuration / API Reference** — tables or structured lists for options/parameters
6. **Contributing / License** — brief, link to files if they exist

Rules:
- Quick Start must work — test the commands before writing them
- API reference tables: columns are Name | Type | Default | Description
- Do not bury Quick Start below lengthy explanations

---

### 2.3 Tutorial / How-to

Trigger: "如何", "怎么", "步骤", "教程", "how to", "guide", step-by-step instructions.

Structure (in order):
1. **Goal** — one sentence: what the reader will have accomplished by the end
2. **Prerequisites** — unordered list of what's needed before starting. Skip if none.
3. **Steps** — numbered list. Each step: one action + explanation of why if non-obvious.
4. **Verification** — how to confirm it worked. Include expected output.
5. **Troubleshooting** — only the 2-3 most common failure modes. Skip if none.

Rules:
- Each step must be a single, atomic action
- Never combine "install X and configure Y" into one step
- Show exact commands, not paraphrases ("run `npm install`", not "install the dependencies")
- Verification section is mandatory — readers must know if they succeeded

---

### 2.4 Meeting Notes / Reading Summary

Trigger: "会议记录", "读书笔记", "文章总结", "摘要", meeting notes, book/article summary.

Structure (in order):
1. **Source / Context** — title, date, participants (for meetings) or author/link (for reading)
2. **Key Points** — unordered list, 3-7 items. Each item is one complete thought, not a fragment.
3. **Decisions / Actions** — for meetings: what was decided, who owns what, by when. For reading: what you'll apply or follow up on.
4. **Open Questions** — unresolved items. Skip if none.

Rules:
- Key points must be complete sentences, not single-word fragments
- Action items must have an owner and a deadline if applicable
- Do not summarize what was said — capture what matters

---

### 2.5 General Notes (no specific type detected)

When the document type is unclear, apply minimal structure:

- Use H2 for major topics
- Use prose as the default — reach for lists and tables only when content demands it
- Do not impose a template — let the content determine the structure

---

## Part 3: Anti-Pattern Reference

Quick reference of what NOT to do. If you catch yourself doing any of these, stop and revise.

| Anti-Pattern | Why It's Bad | Fix |
|---|---|---|
| **Bold every other phrase** | Destroys emphasis hierarchy | Bold max 1-2 terms per paragraph |
| Bullet list of 1-2 items | Lists imply plurality; use prose | Write as a sentence |
| H3 with no H2 parent | Breaks document hierarchy | Add the missing H2 or promote to H2 |
| ` ``` ` without language tag | Breaks syntax highlighting | Always add language identifier |
| "In summary..." closing | Redundant — the content already said it | Delete it |
| Table with 2 columns | Usually a list in disguise | Use a definition list or prose |
| Nested bullets 3+ levels | Signals structural confusion | Flatten with subheadings instead |
| Every section starts with a list | Skips context-setting | Write an intro sentence first |
| Heading for a single sentence | Heading implies a section, not a line | Remove heading, keep as prose |
