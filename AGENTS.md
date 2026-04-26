# Agents Guide

This repository stores reusable Codex Skills under `.agents/skills`.

## Purpose

Use this repository as a portable Skill library. Clone or fork it into projects that need repeatable workflows for design, review, testing, commit preparation, and pull request writing.

## Skill Layout

Each Skill must live at this path:

```text
.agents/skills/{skill-name}/SKILL.md
```

Every `SKILL.md` must include YAML frontmatter:

```yaml
---
name: skill-name
description: English description used by Codex for Skill discovery.
description_en: English description for humans and tools.
description_ko: Korean description for Korean users.
---
```

## Available Skills

- `code-designer`: Design production-ready backend code before implementation.
- `code-review-perfect`: Review changed code for correctness, architecture, transaction safety, performance, security, maintainability, and production risk.
- `test-writer-perfect`: Design and write focused tests for changed code.
- `bug-root-cause`: Investigate bugs, errors, failing tests, and incidents by root cause.
- `git-commit-perfect`: Analyze git changes and create clean Conventional Commit plans.
- `create-pr-template`: Create complete pull request descriptions from git diff and commit history.

## Language Policy

Korean is the default because this repository is maintained by a Korean user.

However, these Skills are intended to be forked and reused by other people. If a user asks for English or another language, final answers should use that requested language.

Keep code, commands, class names, method names, branch names, and error messages in their original language or English.

## Editing Rules

- Keep each Skill self-contained.
- Add both `description_en` and `description_ko` when creating or updating a Skill.
- Prefer practical workflow instructions over vague advice.
- Include concrete output formats.
- Keep final language rules at the end of each Skill.
- Do not commit unrelated application files when changing Skills.

## Recommended Workflow

```text
1. code-designer
   Design the feature before implementation.

2. test-writer-perfect
   Define meaningful tests before or during implementation.

3. code-review-perfect
   Review the final diff.

4. bug-root-cause
   Use when tests fail or unexpected runtime behavior appears.

5. git-commit-perfect
   Prepare clean logical commits.

6. create-pr-template
   Write the pull request description.
```
