---
name: create-pr-template
description: Create a complete pull request description from git diff and commit history, including summary, change details, test evidence, risk, rollback, and reviewer focus.
description_en: Create a complete pull request description from git diff and commit history, including summary, change details, test evidence, risk, rollback, and reviewer focus.
description_ko: git diff와 커밋 히스토리를 바탕으로 요약, 변경사항, 테스트 근거, 리스크, 롤백, 리뷰 포인트를 포함한 PR 설명을 작성할 때 사용한다.
---

You are a senior engineer writing a pull request description.

Your goal is to help reviewers understand:
- what changed
- why it changed
- how it was tested
- what risk exists
- where to focus review

Inspect:
1. git status
2. git branch --show-current
3. git log origin/main..HEAD --oneline
4. git diff origin/main...HEAD --stat
5. git diff origin/main...HEAD
6. existing pull_request_description.md if present
7. related test files
8. configuration changes
9. migration changes

If origin/main does not exist, use main.
If main does not exist, use master.
If base branch is unclear, ask or infer from repository.

Analyze:
- feature changes
- bug fixes
- refactoring
- API changes
- DB schema changes
- config changes
- deployment impact
- test coverage
- breaking changes
- rollback method

Create or update:

```text
pull_request_description.md
```

Use this template exactly:

```md
#### Overview

<!-- 2~4 lines. Explain why this PR exists and what it changes. -->

#### Changes

<!-- Group by domain, not by random file order. -->

1.
   - Files:
   - Details:

2.
   - Files:
   - Details:

#### Test

<!-- Include actual commands or manual test evidence. -->

- [ ] Unit test
- [ ] Integration test
- [ ] Manual test
- [ ] Build success

Commands:

```bash
./gradlew clean build
```

#### Risk & Impact

<!-- Transaction, DB, config, deployment, backward compatibility, API impact. -->

- Risk:
- Impact:
- Mitigation:

#### Reviewer Focus

<!-- Tell reviewers exactly where to focus. -->

-
-

#### Rollback Plan

<!-- Explain how to rollback safely. -->

-

#### Checklist

- [ ] Code follows project conventions
- [ ] Tests were added or updated
- [ ] No secrets or local config included
- [ ] No unnecessary generated files included
- [ ] API compatibility checked
- [ ] DB migration impact checked
- [ ] Monitoring/logging impact checked
```

After writing the file:
1. show the generated PR description
2. summarize missing test evidence
3. warn about risky changes
4. do not create remote PR unless user explicitly asks

Rules:
- Do not write vague PR text.
- Do not list files without explaining meaning.
- Do not hide risk.
- If tests are missing, clearly say so.
- If there is DB/config/deployment impact, make it visible.
- Keep PR readable for senior reviewers.
- 코드, 명령어, 클래스명, 메서드명, 브랜치명, 에러 메시지는 원문 또는 영어를 유지한다.
- Default final answers should be written in Korean. If the user asks for English or another language, write the final answer in that requested language.
- 기본 최종 답변은 한국어로 작성한다. 사용자가 English 또는 다른 언어를 요청하면 해당 언어로 최종 답변을 작성한다.
