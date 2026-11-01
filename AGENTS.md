# AGENTS.md — Standing Qoder Rules

Read this before changing code.

## Priority
1. Exam brief/rubric
2. TEST_SPEC.md / approved exam plan
3. Existing repository architecture/conventions
4. UI_DIRECTION.md
5. These rules

If anything conflicts with the exam brief, the exam brief wins.

## Work style
- Work in substantial coherent milestones, not tiny edits.
- Continue through routine implementation, build, tests and fixes without asking for approval.
- Ask only for genuine ambiguity, destructive/irreversible decisions, missing real secrets, conflicting requirements, or unjustified major architecture changes.
- Prefer the simplest reliable implementation.
- Do not over-engineer.
- Do not refactor unrelated working code.
- Do not add unnecessary dependencies.
- Reuse existing libraries/components.
- Keep the starter stack unless the brief requires otherwise.

## Output style
Be extremely concise.
No preamble.
No narration.
No repeated recap.
Do the work rather than describing it.

When finished report only:
- requirement/milestone result
- tests/checks PASS/FAIL
- changed file count
- blockers
- maximum 3 manual checks

## Testing
- Use existing test tooling.
- Test important business behaviour where useful.
- Test-first when it protects risky logic/regressions.
- Test-after is acceptable when faster and reliable.
- Prefer supplied automarkers/exact acceptance checks for infrastructure.
- Never weaken/delete a valid test just to get green.
- Fix regressions caused by your changes before returning.

## UI
Read and follow `UI_DIRECTION.md`.
Maintain one consistent visual language.
Avoid generic AI design patterns.
Do not invent a heavy design system unless required.

## Secrets
Never invent/hard-code/commit:
- PATs
- API keys
- real service passwords
- production secrets

## Git
Do not commit/push unless explicitly asked or the user uses Git review/commit.
When drafting commit messages, follow `COMMIT_STYLE.md`.

## Scope
Required rubric work beats unrequired polish/features.
Do not implement stretch ideas unless explicitly approved.
