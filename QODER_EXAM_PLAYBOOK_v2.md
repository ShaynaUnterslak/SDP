# QODER EXAM PLAYBOOK v2 — COMS3011A
## 8-hour exam strategy: 4h + lunch + 4h
### Built for: maximum marks, minimum prompting, controlled Qoder credits/tokens

Use this as a static open-book note during the exam.

---

# THE WHOLE STRATEGY IN ONE LINE

**Brief + rubric once → Qoder plan once → BIG Core build → quick proof → commit/push → BIG high-value milestones → UI polish → final audit → clean clone → final push.**

Do **not** repeat the test-day mistake of breaking the work into tiny Qoder tasks.

Your job:
- decide what earns marks
- sanity-check Qoder's plan
- verify important behaviour
- protect working versions with Git
- stop Qoder going off-scope

Qoder's job:
- inspect the repo
- implement substantial coherent milestones
- run commands/tests itself
- fix failures it caused
- report only what you need to know

---

# 0. NON-NEGOTIABLE RULES

1. Upload/read the brief + rubric **once**.
2. Qoder creates `TEST_SPEC.md` **once**.
3. You sanity-check it for missed requirements/marks.
4. Build the complete CORE/MVP as one substantial milestone where practical.
5. Do a **quick Core gate**, not a 45-minute audit.
6. Commit + push every known-good milestone.
7. Rank add-ons by **marks vs time/risk**, not paper order.
8. Do not make Qoder ask for approval between normal implementation steps.
9. Keep Qoder outputs terse; make it **do**, not narrate.
10. Use tests to protect marks; do not turn TDD into the assignment unless required.
11. For UI apps: establish a **light visual baseline during Core**, then do a dedicated polish pass later.
12. Optional “nice extras” only happen after required/high-value marks are safe.
13. Follow course AI-attribution policy on every AI-assisted code commit.
14. Never commit PATs, API keys, real secrets or production credentials.
15. Freeze risky work before the end and protect submission time.

---

# 1. QODER MODE / CREDIT / TOKEN STRATEGY

Use the credit multipliers actually shown in Qoder on exam day.

## Default model use

**Ask + Efficient / cheapest suitable model**
- brief/rubric analysis
- prioritisation
- concise status checks
- final audits
- simple diagnosis

**Agent + Auto**
- almost all implementation
- Core
- normal add-ons
- UI polish

**Agent + Performance**
- complex debugging
- architecture problem after Auto has genuinely struggled
- difficult failing tests

**Ultimate / very expensive model**
- emergency only

## Credit mindset

The test showed that under-using Qoder is also a failure mode.

Do **not** finish an 8-hour exam with most of your useful Agent capacity unused while marks are incomplete.

Rough guide only:
- ~2 hours in: 20–25% used
- lunch: ~40–50% used
- ~2 hours after lunch: ~60–70% used
- final hour: ~80–85% used
- keep ~10–15% emergency reserve

Do not chase these numbers exactly.  
The principle is: **use the tool aggressively enough to finish the work, but keep an emergency reserve.**

---

# 2. TOKEN-SAVING / LOW-PROMPTING RULES

These matter more than “clever” prompt wording.

## DO

- attach brief + rubric once
- create `TEST_SPEC.md`
- use `TEST_SPEC.md` as the persistent source of truth
- give Agent one substantial milestone at a time
- let Agent inspect the repo itself
- let Agent run build/tests itself
- let Agent fix failures it caused before returning
- require terse outputs
- start a fresh Qoder conversation if a thread becomes bloated/confused
- in a fresh conversation, reference `TEST_SPEC.md` + current repo instead of retelling the whole exam
- use exact errors/logs when debugging

## DO NOT

- repeatedly attach the PDF
- paste huge source files into chat when Qoder can inspect the repo
- ask “what next?” after every tiny change
- ask Qoder to explain every line it writes
- make separate prompts for database → form → button → styling when they belong to one milestone
- keep asking for summaries of work it just did
- use expensive models for routine code
- ask for three alternative implementations unless you genuinely need a decision

## TARGET INTERACTION PATTERN

A strong 8-hour exam may only need roughly:

1. plan/spec call
2. Core implementation call
3. remaining-work ranking call
4. major add-on call
5. another major add-on call
6. another add-on if worthwhile
7. UI polish call
8. final audit call
9. README/clean-clone correction call if needed

Debug calls happen only when something actually fails.

---

# 3. FIRST 15–20 MINUTES — QODER MAKES THE PLAN

Upload:
- original exam brief PDF
- rubric / marking guide

Prefer original files.  
If Qoder clearly misreads a scanned/table section, paste **only that section** as text.

## MODE
**Ask + Efficient / cheapest suitable**

## COPY THIS PROMPT

```text
READ ONLY. Do not change any files.

Read the ENTIRE attached exam brief and marking rubric before answering.

Create TEST_SPEC.md as a concise scoring-oriented implementation plan for this 8-hour exam.

Extract:

1. CORE / MVP requirements
2. every required add-on / feature
3. marks for every requirement where stated
4. exact acceptance criteria / Done When conditions
5. dependencies between requirements
6. required architecture / framework / technologies
7. supplied tests, automarkers and validation commands
8. persistence/database/infrastructure requirements
9. required configuration/environment variables
10. real secrets vs safe local/demo configuration
11. forbidden choices / constraints
12. README / submission requirements
13. AI-use / attribution requirements stated in the exam
14. anything that could cause a zero or major penalty

Then create 3–5 SUBSTANTIAL IMPLEMENTATION MILESTONES.

Milestones must be coherent end-to-end chunks, NOT tiny edits.

For each milestone include:
- requirement IDs
- marks protected
- exact Done When
- dependencies
- risk: LOW / MEDIUM / HIGH
- best validation command/check

For UI applications, also include:
- a MINIMAL VISUAL BASELINE inside the Core milestone:
  app shell/layout, spacing, typography, form/button consistency, responsive container
- do NOT spend major time polishing individual pages yet
- schedule final UI polish only after the important functionality is working

Add a section called:
STRETCH IDEAS — NOT REQUIRED FOR MARKS

Leave it empty for now unless the brief explicitly contains bonus/stretch work.

Finally give:
A. recommended implementation order
B. highest-value required features by marks vs effort/risk
C. biggest submission risks

Do not implement anything yet.

OUTPUT:
Keep the response under 500 words.
No generic advice.
Create/update TEST_SPEC.md and report only:
- file created
- number of Core requirements
- number of remaining requirements
- major ambiguity/blocker, if any
```

---

# 4. YOUR SANITY CHECK OF TEST_SPEC — MAX 3–5 MINUTES

Open the real paper next to `TEST_SPEC.md`.

Check only:

- Did Qoder miss any requirement?
- Did it misunderstand the marks?
- Did it misclassify required vs optional?
- Did it miss a “must”, “must not”, submission rule or zero-risk?
- Are milestones too small?

If fine → move straight to Core.

Do **not** spend 30 minutes perfecting the plan.

---

# 5. IF QODER MISSED A REQUIRED REQUIREMENT

Do not rewrite the whole spec yourself.

## COPY THIS

```text
Update TEST_SPEC.md only.

You missed or misclassified this REQUIRED exam requirement:

[PASTE THE EXACT REQUIREMENT / RUBRIC ROW]

Treat the pasted exam text as authoritative.

1. add/correct the requirement
2. record its marks if stated
3. add its exact Done When
4. identify which existing milestone it belongs to
5. update dependencies/order if necessary
6. flag whether this changes CORE/MVP

Do NOT implement it yet.
Do NOT rewrite unrelated parts of TEST_SPEC.md.

OUTPUT:
Maximum 120 words.
Tell me only what changed in the plan.
```

Then continue.

---

# 6. IF YOU THINK OF SOMETHING EXTRA YOU WANT — GRAPHS, DASHBOARD, ETC.

There are two different situations.

## A. IT EARNS MARKS / SUPPORTS A RUBRIC ITEM

Treat it as required/high-value work and place it into the correct milestone.

Use:

```text
Update TEST_SPEC.md.

I want to satisfy this rubric requirement using the following implementation idea:

RUBRIC REQUIREMENT:
[PASTE REQUIREMENT]

IDEA:
[e.g. add a summary graph/dashboard]

Check whether this idea directly helps satisfy the requirement.

If YES:
- add it to the appropriate milestone
- keep the implementation minimal
- state the exact acceptance check

If NO:
- do not put it in required work
- put it under STRETCH IDEAS — NOT REQUIRED FOR MARKS

Do not implement anything yet.

OUTPUT:
Maximum 120 words.
```

## B. IT IS PURELY A NICE-TO-HAVE

Example:
- graphs are not required
- fancy dashboard
- animation
- extra filter
- additional statistics
- visual flourish

Do **not** let it distract from marks.

Use:

```text
Add this idea to the STRETCH IDEAS — NOT REQUIRED FOR MARKS section of TEST_SPEC.md:

[IDEA]

Estimate:
- implementation effort: LOW / MEDIUM / HIGH
- regression risk: LOW / MEDIUM / HIGH
- visual/user-value: LOW / MEDIUM / HIGH
- likely time cost in minutes

Do not implement it.

Recommend IMPLEMENT LATER or SKIP based on the remaining required work.

OUTPUT:
Maximum 100 words.
```

Only implement stretch work when:
- Core is safe
- high-value required features are safe
- tests are green
- you have comfortable time/credits

**A beautiful unmarked graph is worth less than an unfinished marked feature.**

---

# 7. CORE / MVP — BIG AGENT TASK

## MODE
**Agent + Auto**

## COPY THIS PROMPT

```text
Implement MILESTONE 1: the complete working CORE/MVP from TEST_SPEC.md.

AUTONOMY:
Continue through normal implementation, build, test and fixes WITHOUT asking for approval between routine steps.

Make conservative decisions based on:
1. the exam brief / TEST_SPEC.md
2. the existing repository architecture
3. existing libraries/conventions

STOP and ask me only if:
- two materially different interpretations of an exam requirement exist
- a destructive data/schema choice cannot safely be inferred
- a real secret/credential is required and missing
- requirements conflict
- continuing would require a major architecture change not supported by the brief

WORK STYLE:
- work end-to-end
- do NOT stop after every small file change
- modify all files reasonably needed for this milestone
- do not implement later optional/stretch features

GOAL:
Produce the simplest reliable implementation satisfying every CORE acceptance criterion.

RULES:
- follow TEST_SPEC.md exactly
- preserve all explicit exam constraints
- use existing architecture/libraries/conventions
- do not over-engineer
- do not refactor unrelated working code
- do not add unnecessary dependencies
- never invent or commit real secrets
- if safe local/demo configuration is required, use only what the brief allows

UI BASELINE:
If this is a user-facing application:
- establish a simple coherent visual baseline while building Core
- use existing styling/design tools already in the repo
- create/reuse consistent layout, spacing, typography, buttons, inputs, cards/tables and responsive container
- make Core screens presentable
- do NOT spend major time on decorative polish, animations or elaborate redesign
- do NOT add a heavy UI library unless already present or clearly justified

TESTING:
- use the existing test framework
- test important business behaviour where practical
- test-first where it meaningfully protects a requirement
- test-after is acceptable when faster and reliable
- for Docker/infrastructure/manual requirements, use supplied automarker/exact acceptance checks
- never weaken/delete a valid test just to make code pass

BEFORE RETURNING:
1. build/start the application
2. run relevant tests/automarker
3. fix failures you caused
4. verify every CORE Done When condition
5. leave the repo in a working state

OUTPUT STYLE:
No preamble.
No narration.
No repeated recap.
Do the work rather than explaining how you will do it.

Return only:
- CORE requirement IDs with PASS/FAIL
- tests/checks run and result
- changed file count
- blockers requiring my decision
- maximum 3 manual checks I should perform
```

---

# 8. CORE GATE — YES, TEST IT, BUT FAST

Target: **5–10 minutes**.

You are not performing the final audit yet.

Check:
- app starts
- main user journey works
- required persistence works
- supplied automarker / important tests pass
- no obvious server/browser errors
- required constraints are visibly satisfied

If Qoder already ran all relevant tests:
- run the supplied marker if one exists
- manually exercise the critical path
- do not rerun everything for no reason

## IF CORE PASSES

Commit + push immediately.

---

# 9. AI ATTRIBUTION — EVERY AI-ASSISTED CODE COMMIT

Course materials specify the trailer form:

```text
Assisted-by: <tool>[<model>]
```

For Qoder use the actual tool/model notation required by the exam/course.

Example:

```text
feat: complete core application

Assisted-by: Qoder[<MODEL>]
```

If Auto does not expose the underlying model:
- do NOT invent one
- use the exact notation prescribed by the exam/course
- if unclear, ask the lecturer/invigilator once

## TERMINAL EXAMPLE

```bash
git add .
git commit -m "feat: complete core application" \
  -m "Assisted-by: Qoder[<MODEL>]"
git push
```

## POWERSELL EXAMPLE

```powershell
git add .
git commit -m "feat: complete core application" -m "Assisted-by: Qoder[<MODEL>]"
git push
```

## IMPORTANT

- AI-assisted code commit → trailer
- do not substitute `Co-Authored-By` if the course requires `Assisted-by`
- do not use vague `AI assisted`
- check any Qoder-generated commit message before committing
- if exam requires an AI register/transcript/declaration too, follow it exactly
- never claim non-use if AI was used

---

# 10. RANK THE REMAINING WORK ONCE CORE IS SAFE

## MODE
**Ask + Efficient**

## COPY THIS

```text
Read TEST_SPEC.md and inspect the CURRENT repository.

CORE is working and protected by a commit.

Do not change files.

Rank all INCOMPLETE REQUIRED requirements by:
1. marks
2. implementation effort
3. regression risk
4. dependencies
5. confidence we can verify it

Return this table only:

Requirement | Marks | Effort | Risk | Dependency | Recommended order

Then state:
NEXT MILESTONE: [single best substantial milestone]

Ignore STRETCH IDEAS unless all required/high-value work is already complete.

OUTPUT:
Maximum 250 words.
No generic advice.
```

---

# 11. IMPLEMENT A MAJOR ADD-ON / MILESTONE

## MODE
**Agent + Auto**

## COPY THIS

```text
Implement the next recommended REQUIRED milestone from TEST_SPEC.md completely.

AUTONOMY:
Continue through routine implementation, build, tests and fixes WITHOUT asking me to approve normal steps.

Stop only for:
- genuine requirement ambiguity with materially different outcomes
- destructive/irreversible data choice
- missing real secret/credential
- conflicting requirements
- major architecture change not justified by the brief

WORK STYLE:
- this is one coherent implementation task
- do not stop after tiny edits
- use existing architecture/libraries
- modify all files reasonably required
- preserve all currently passing Core behaviour
- do not implement unrelated stretch ideas
- do not over-engineer
- do not add unnecessary dependencies
- do not weaken/delete valid tests
- do not invent secrets

UI:
Use the established visual baseline/components for any new screens.
Make the new feature visually consistent as you build it.
Do NOT spend time on final decorative polish yet.

TESTING:
- add meaningful tests where valuable
- test-first for risky business logic/regressions when practical
- otherwise implement efficiently and test immediately afterwards
- use supplied automarker/manual acceptance checks when authoritative

BEFORE RETURNING:
1. build/start if relevant
2. run focused tests/checks
3. run relevant regression tests
4. fix failures you caused
5. leave the repo working

OUTPUT STYLE:
No preamble or narration.
Return only:
- requirement IDs with PASS/FAIL
- tests/checks and result
- changed file count
- blockers
- maximum 3 manual checks
```

Then:
1. do the few manual checks
2. commit with required AI trailer
3. push
4. continue to the next high-value milestone

---

# 12. BEST UI STRATEGY — DO NOT CHOOSE EITHER EXTREME

## BAD EXTREME 1
“Make every feature beautiful before moving on.”

Why bad:
- burns time/tokens
- repeated styling work
- you may polish screens whose functionality later changes
- required marks remain unfinished

## BAD EXTREME 2
“Ignore UI completely until the final 30 minutes.”

Why bad:
- inconsistent components spread through the app
- final polish becomes a huge rewrite
- app may look obviously unfinished

## BEST STRATEGY

### DURING CORE
Create a **light visual baseline**:
- app shell / page container
- typography
- spacing
- colours if already supplied / sensible
- reusable buttons
- inputs/forms
- card/table/list treatment
- error/success/empty state pattern
- responsive basics

This is already built into the Core prompt.

### DURING FEATURES
Use the same baseline/components.
Make each new screen **clean and consistent**, not “award-winning”.

This is already built into the feature prompt.

### NEAR THE END
Run ONE dedicated UI/UX polish milestone across the finished application.

That gives you:
- consistency from the beginning
- minimal duplicate work
- a professional final pass
- no need for constant UI prompting

## SHOULD QODER CREATE A UI TEMPLATE AT THE START?

**Only a lightweight one, and preferably as part of Core — not as a separate design project.**

Do NOT burn a separate hour asking for:
- design exploration
- mood boards
- three themes
- custom component library
- elaborate design system
- animations

If the starter repo already has Tailwind, shadcn, MUI, Bootstrap or a design system:
**reuse it.**

If the brief includes screenshots/style requirements:
**follow those first.**

---

# 13. DEDICATED UI / UX POLISH PASS

Use when:
- important functionality is working
- required features are mostly safe
- you have roughly 45–90+ minutes left depending on exam state

## MODE
**Agent + Auto**

## COPY THIS

```text
The required functionality is now substantially complete.

Perform ONE focused UI/UX polish pass across the application.

AUTONOMY:
Make reasonable visual improvements without asking for approval between routine edits.

GOAL:
Make the submission look coherent, intentional and professionally finished WITHOUT changing required behaviour.

USE:
- the existing styling/design system
- existing reusable components
- the established visual baseline

IMPROVE WHERE RELEVANT:
- hierarchy
- spacing/alignment
- typography
- page width/layout
- navigation
- forms/labels
- buttons and states
- cards/tables/lists
- empty states
- errors/success feedback
- loading states
- responsive behaviour
- consistency across pages

DO NOT:
- change business logic
- redesign architecture
- remove functionality
- add a heavy new UI library
- rewrite stable components without reason
- add elaborate animations
- introduce new unrequired features

BEFORE RETURNING:
1. build/start the app
2. run relevant regression tests
3. fix any regression caused by the polish
4. leave functionality unchanged

OUTPUT STYLE:
No narration.
Return only:
- pages/components visually improved
- tests/checks result
- any remaining visual issue
- any functionality risk
Maximum 180 words.
```

---

# 14. OPTIONAL STRETCH FEATURE — ONLY AFTER MARKS ARE SAFE

If required work is safe and you still want the graph/dashboard/etc:

## FIRST ASK FOR A GO/NO-GO

```text
Read TEST_SPEC.md and inspect current status.

Evaluate the top item under:
STRETCH IDEAS — NOT REQUIRED FOR MARKS

Do not implement it.

Tell me:
- estimated time
- regression risk
- visual/user value
- whether it reuses current architecture
- whether implementing it now threatens any unfinished required work
- GO or SKIP

OUTPUT:
Maximum 100 words.
```

If GO:

```text
Implement this approved STRETCH feature:

[FEATURE]

AUTONOMY:
Implement, test and fix routine problems without asking for approval.

CONSTRAINTS:
- required functionality must remain unchanged
- reuse existing architecture/components
- no unnecessary dependencies
- keep scope minimal
- if it becomes materially larger than estimated, STOP and tell me before continuing

BEFORE RETURNING:
- run relevant regression tests
- verify the feature manually/automatically as appropriate

OUTPUT:
Only PASS/FAIL, tests/checks, changed file count, and any risk.
Maximum 120 words.
```

---

# 15. DEBUGGING — GIVE QODER THE EXACT FAILURE

Do not say:
`fix it`

## COPY THIS

```text
This exact requirement is failing:

[REQUIREMENT / DONE WHEN]

Command/check:
[COMMAND]

Exact error/output:
[PASTE]

Relevant logs:
[PASTE ONLY RELEVANT LOGS]

Diagnose the ROOT CAUSE first.

Then make the SMALLEST fix necessary.

AUTONOMY:
Run the failing check, implement the fix, rerun it, and run relevant regression tests without asking me to approve routine steps.

CONSTRAINTS:
- preserve currently passing requirements
- do not refactor unrelated code
- do not weaken/delete tests
- if practical, add a regression test that reproduces the bug before the fix
- do not change architecture unless the root cause genuinely requires it

OUTPUT STYLE:
No narration.
Return only:
- root cause in max 3 sentences
- fix made
- failing check now PASS/FAIL
- regression tests PASS/FAIL
- files changed
```

## Docker quick diagnosis

```bash
docker compose config
docker compose build
docker compose up -d
docker compose ps
docker compose logs app
docker compose logs db
```

Remember:
- container → container usually uses service name such as `db`, not `localhost`
- `docker compose down -v` deletes volumes/data

---

# 16. TESTING PHILOSOPHY

Use three levels.

```text
CORE complete
→ QUICK CORE GATE
→ commit/push

Each major milestone
→ focused check + relevant regression tests
→ commit/push

Near end
→ FULL TEST / AUDIT
```

## Test-first is especially worthwhile for
- calculations
- validation
- business rules
- APIs
- data transformations
- bugs/regressions
- behaviour Qoder keeps breaking

## Direct acceptance checks are often better for
- Docker/Compose
- infrastructure/startup
- UI appearance
- supplied automarker requirements
- end-to-end user flows when no good test harness exists

**Testing protects marks. Testing is not automatically the assignment.**

---

# 17. LUNCH CHECKPOINT

Before lunch aim for:

- [ ] repo created and pushes successfully
- [ ] Core working
- [ ] Core pushed
- [ ] useful optional/remaining marks completed
- [ ] tests currently green
- [ ] no mystery uncommitted work
- [ ] required AI trailers present
- [ ] TEST_SPEC accurately reflects requirements

Do not spend lunch re-planning the entire exam.

After lunch:

## MODE
**Ask + Efficient**

```text
Read TEST_SPEC.md and inspect the current repository.

Do not change files.

Return only:

COMPLETED:
- requirements + marks

INCOMPLETE:
- requirements + marks

CURRENT HEALTH:
- build
- tests
- known failures

NEXT:
- single highest-value substantial milestone

RISK:
- biggest current submission/regression risk

Ignore stretch ideas unless required work is effectively complete.

Maximum 220 words.
```

Then continue.

---

# 18. FINAL 60–75 MINUTES — FEATURE FREEZE MINDSET

Ask yourself:

**Is this next feature worth risking a working submission?**

If not, stop.

Final phase:

1. full tests / automarker
2. fix real failures
3. manual critical-flow walkthrough
4. final UI sanity check
5. README
6. AI attribution/declaration check
7. `git status`
8. push
9. clean clone
10. follow README
11. final push
12. verify remote

---

# 19. FINAL MARKER AUDIT

## MODE
**Ask + Efficient**

## COPY THIS

```text
Act as the final marker for this submission.

Read TEST_SPEC.md and inspect the CURRENT repository.

DO NOT modify anything.

Create this concise table:

Requirement | Marks | Evidence | Test/check | PASS/FAIL | Risk

Then identify:
1. missing marks
2. broken/incomplete behaviour
3. tests/automarker failures
4. README/setup problems
5. UI problems serious enough to affect usability/quality marks
6. AI attribution/declaration problems
7. secrets/configuration problems
8. files that should not be committed
9. clone/submission risks

Then give ONLY the THREE highest-value fixes remaining.

Do not suggest cosmetic refactoring unless it affects marks/usability.
Ignore unrequired stretch ideas.

OUTPUT:
Maximum 450 words.
```

Fix the highest-value issues only.

---

# 20. README / CLEAN-CLONE AUDIT

## MODE
**Agent + Auto** if fixes are needed, otherwise Ask is enough.

## COPY THIS

```text
Audit README.md against the ACTUAL repository and TEST_SPEC.md.

A marker must be able to start and test this project from a clean clone.

Check:
- prerequisites
- install command
- required environment/configuration
- safe example config only
- build/start command
- test/automarker command
- ports/URLs if relevant
- database setup if relevant
- required AI declaration/evidence
- no real secrets
- commands match the actual package scripts/files

AUTONOMY:
Make only the MINIMUM README/setup corrections required.
Do not change application behaviour.

Then give me the exact clean-clone command sequence to run.

OUTPUT:
No narration.
Maximum 220 words.
```

Then actually clean-clone if time permits.

---

# 21. GIT / GITHUB CHECKPOINT

## Typical checkpoint

```bash
git status
git diff
git add .
git commit -m "feat: <milestone>" -m "Assisted-by: Qoder[<MODEL>]"
git push
```

Verify:

```bash
git log -1 --oneline
git status
```

## Public marker clone check

```bash
git clone YOUR_PUBLIC_REPO_URL verify-exam
cd verify-exam
```

A public submission repo should not require the marker to possess your PAT or SSH private key simply to clone it.

Never commit:
- PAT
- GitHub token
- API key
- real service password
- `.env` with real secrets

---

# 22. QODER COMMIT / PUSH

Qoder can work with the local Git repository and its configured remote.

If you use its Review / commit / push interface:

Before committing:
1. inspect changed-file count
2. inspect unexpected/suspicious changes
3. ensure relevant validation passed
4. check branch/remote
5. write/check the commit message
6. include required `Assisted-by:` trailer

Do not blindly accept an autogenerated commit message if it omits course-required attribution.

---

# 23. LAB COMPUTER / GITHUB AUTH

Do not assume Git credentials configured on your home laptop will transfer to the lab PC.

Safest exam plan:
- know your GitHub username
- know your authentication method
- have a suitable PAT available if required
- authenticate only when necessary
- do not permanently store the PAT on a shared machine
- do not put a PAT in a repo URL, README or code
- verify push early in the exam, not at the deadline

---

# 24. IF QODER CHANGES TOO MUCH

Warning signs:
- small requirement changes 15–20 unrelated files
- unrelated refactor
- new dependency for trivial work
- deletes tests
- replaces working architecture
- rewrites setup unexpectedly

## COPY THIS

```text
Stop and review your current diff.

The change is broader than required.

REQUIREMENT:
[PASTE REQUIREMENT]

Reduce the implementation to ONLY what is necessary to satisfy this requirement.

Revert:
- unrelated refactoring
- unrelated formatting
- unnecessary dependencies
- changes to unrelated working behaviour

Preserve all currently passing requirements/tests.

Then rerun the relevant validation.

OUTPUT:
Only:
- reduced changed-file list
- PASS/FAIL of the requirement
- regression test result
Maximum 120 words.
```

---

# 25. IF AUTO IS STUCK

Use this escalation sequence:

1. give Auto the exact error/log
2. ask for root cause + smallest fix
3. if it repeats the same wrong approach, start a fresh diagnosis chat
4. reference `TEST_SPEC.md` + repo + exact failure
5. then use Performance
6. Ultimate only for genuine emergency

Do not spend 40 minutes letting Auto attempt the same fix repeatedly.

---

# 26. 8-HOUR TIME MAP

Adjust if the exam is unusually difficult, but protect final submission time.

## MORNING

### 0:00–0:20
- brief + rubric
- TEST_SPEC
- sanity check

### 0:20–2:00
- complete Core/MVP
- visual baseline included
- Core gate
- commit + push

### 2:00–3:40
- highest-value required milestones
- focused test
- commit + push

### 3:40–4:00
- stable pre-lunch state
- tests
- commit/push
- note next milestone

## LUNCH
Reset.

## AFTERNOON

### 4:00–5:30
- major remaining required features

### 5:30–6:30
- remaining good-value marks
- stretch feature only if genuinely safe

### 6:30–7:00
- dedicated UI/UX polish

### 7:00–7:30
- final marker audit
- high-value fixes only

### 7:30–8:00
- README
- full tests / automarker
- AI attribution check
- clean clone
- final commit/push
- verify remote

---

# 27. FINAL SUBMISSION CHECKLIST

- [ ] correct repository URL
- [ ] correct branch
- [ ] latest work committed
- [ ] latest work pushed
- [ ] AI-assisted code commits have correct `Assisted-by: <tool>[<model>]`
- [ ] required README AI declaration/evidence complete
- [ ] no PAT/API key/real secret committed
- [ ] app builds
- [ ] app starts
- [ ] main flow works
- [ ] required persistence works
- [ ] relevant tests pass
- [ ] supplied automarker passes as far as possible
- [ ] UI is coherent and usable
- [ ] README commands actually work
- [ ] marker can clone repo
- [ ] no important untracked files
- [ ] no accidental `node_modules`, build junk or secret `.env`
- [ ] final commit visible remotely before deadline

---

# 28. IF YOU FORGET EVERYTHING — REMEMBER THIS

```text
BRIEF + RUBRIC
      ↓
QODER PLAN ONCE
      ↓
SANITY CHECK
      ↓
BIG CORE BUILD
      ↓
QUICK PROOF
      ↓
COMMIT + PUSH
      ↓
BIG HIGH-VALUE FEATURE
      ↓
FOCUSED TEST
      ↓
COMMIT + PUSH
      ↓
REPEAT
      ↓
ONE UI POLISH PASS
      ↓
FINAL MARKER AUDIT
      ↓
README + CLEAN CLONE
      ↓
FINAL PUSH
```

### Three rules

**1. Plan once. Do not keep re-planning.**

**2. Give Qoder substantial coherent milestones and enough autonomy to finish them.**

**3. Protect working marks before chasing beauty or unmarked extras.**

Qoder is the implementation engine.

You are:
**requirements owner → technical lead → QA → marker.**
