# QODER EXAM PLAYBOOK — FINAL
## COMS3011A | 30 min planning + 7.5 h coding + 1 h lunch

Use this version only tomorrow.

# THE WHOLE STRATEGY

**Plan once → Git immediately → big Core build → quick proof → commit/push → high-value milestones → UI polish → final audit → clean clone → final push.**

Do not split work into tiny Qoder tasks.

You are:
**requirements owner → technical lead → QA → marker**

Qoder is:
**implementation engine**

---

# 1. MODEL STRATEGY — UPDATED FOR CURRENT QODER TIERS

Use the rates shown in Qoder on the day if they differ.

## Efficient — ~0.3×
Use for:
- brief/rubric breakdown
- ranking remaining work
- status summaries
- final marker audit
- simple explanations

## Auto — ~0.5×
**DEFAULT IMPLEMENTATION TIER**

Use for:
- Core/MVP
- major features
- normal refactors
- full milestone implementation
- tests/build/fix loops
- final UI polish if it is not fighting you

Why:
- cheapest strong implementation option
- ideal for large autonomous jobs where you are not waiting on every intermediate reply

## Fast — ~0.8×
Use when **speed of interaction matters** or Auto has started becoming slow/awkward.

Best for:
- debugging while you are waiting on each reply
- UI iteration/tweaks
- a feature where you expect 2–3 quick back-and-forth rounds
- time-critical diagnosis
- Auto tried once and you want a stronger/faster second pass

The current Qoder notice says Fast replaces Performance, keeps high output quality, responds faster, and costs about 0.8×.

## Ultimate — ~2×
Emergency only:
- serious high-mark blocker
- Auto + Fast both failed
- very hard architecture/debugging problem

## SIMPLE RULE
**Efficient thinks. Auto builds. Fast rescues/iterates. Ultimate is emergency.**

Do not finish the exam with most of your credits unused while required marks are incomplete.

---

# 2. FILES TO BRING

Bring these four files through an allowed route such as Moodle:

- `QODER_EXAM_PLAYBOOK_FINAL.md`
- `AGENTS.md`
- `UI_DIRECTION.md`
- `COMMIT_STYLE.md`

At the start of coding, copy `AGENTS.md`, `UI_DIRECTION.md` and `COMMIT_STYLE.md` into the repository if exam rules permit.

These files reduce repeated prompting.

---

# 3. STACK RULE

If there is a starter repo:
**keep its stack unless the exam explicitly tells you otherwise.**

If greenfield and you are free to choose:
- JavaScript/TypeScript
- React/Next.js if available/familiar
- SQLite for simple single-app persistence
- PostgreSQL for real database/service requirements
- Docker only when useful/required

Because the firewall may restrict sites/packages:
- favour common installed tools
- reuse existing dependencies
- avoid niche libraries
- do not introduce a new framework during the exam

---

# 4. 30-MINUTE PLANNING PERIOD — NO CODE

The lecturer says planning/research is allowed but coding is not.

## 0–5 min
Read the whole brief/rubric yourself.

Mark:
- Core
- marks
- zero/major-penalty risks
- required stack
- submission rules

## 5–15 min — Qoder plan
Use **Ask + Efficient**.

```text
READ/PLAN ONLY. DO NOT IMPLEMENT OR MODIFY APPLICATION CODE.

Read the ENTIRE exam brief and rubric.

Create a concise scoring plan containing:

1. CORE/MVP requirements
2. every remaining required feature
3. marks for each item where stated
4. exact Done When / acceptance criteria
5. dependencies
6. required framework/database/infrastructure
7. supplied tests/automarkers
8. configuration/environment requirements
9. zero/major-penalty risks
10. README/submission rules
11. AI-attribution requirements
12. 3–5 SUBSTANTIAL implementation milestones

Milestones must be large coherent end-to-end chunks, NOT tiny edits.

For each milestone give:
- requirements
- marks protected
- Done When
- risk
- validation check

Also give:
- recommended order
- highest-value requirements by marks vs effort/risk
- biggest submission risks

For UI:
- follow UI_DIRECTION.md
- establish only a light visual baseline during Core
- do not invent a separate design system

OUTPUT:
Under 500 words.
No generic advice.
No implementation.
```

If creating `TEST_SPEC.md` during planning could count as coding, keep this plan in Qoder/chat notes and create the file only once coding begins.

## 15–22 min
Sanity-check against the real paper.

Only ask:
- missing requirement?
- wrong marks?
- required vs optional wrong?
- missed must/must-not?
- milestones too small?

## 22–27 min
Confirm final stack.

## 27–30 min
Decide:
- repo name
- first milestone
- first user flow you will manually test
- setup needed once coding starts

---

# 5. FIRST 5–10 CODING MINUTES — GIT FIRST

Lecturer explicitly flagged this.

1. Create/clone repo.
2. Check remote.
3. Prove push works.
4. Add `AGENTS.md`, `UI_DIRECTION.md`, `COMMIT_STYLE.md` if allowed.
5. Initial commit if appropriate.
6. Push.

Do not discover auth problems near the deadline.

---

# 6. IF THE PLAN MISSED A REQUIRED ITEM

```text
Update the plan / TEST_SPEC only.

You missed or misclassified this REQUIRED exam item:

[PASTE EXACT REQUIREMENT OR RUBRIC ROW]

Treat it as authoritative.

Update:
- requirement
- marks
- Done When
- dependencies
- milestone placement
- whether it changes Core

Do NOT implement yet.
Do NOT rewrite unrelated plan sections.

OUTPUT:
Maximum 120 words.
```

---

# 7. BIG CORE BUILD

Use **Agent + Auto**.

```text
Read:
- TEST_SPEC.md / approved exam plan
- AGENTS.md
- UI_DIRECTION.md

Implement the complete CORE/MVP milestone end-to-end.

AUTONOMY:
Proceed through normal implementation, build, tests and fixes WITHOUT asking me to approve routine steps.

Only stop for:
- genuine requirement ambiguity with materially different outcomes
- destructive/irreversible data choice
- missing real secret/credential
- conflicting requirements
- major architecture change not justified by the brief

RULES:
- satisfy exact Core acceptance criteria
- use existing stack/architecture
- do not over-engineer
- no unrelated stretch features
- no unnecessary dependencies
- no unrelated refactors
- never invent/commit real secrets

UI:
Follow UI_DIRECTION.md.
Establish a shared visual baseline while building Core.
Make Core presentable and consistent.
Do not spend major time on decorative polish yet.

TESTING:
- use existing test framework
- test important business behaviour where useful
- use supplied automarker/exact acceptance checks when more authoritative
- never weaken/delete valid tests merely to get green

BEFORE RETURNING:
1. build/start
2. run relevant tests/automarker
3. fix failures you caused
4. verify all Core Done When items
5. leave repo working

OUTPUT:
No preamble.
No narration.
Return only:
- requirement IDs PASS/FAIL
- tests/checks + result
- changed file count
- blockers
- maximum 3 manual checks for me
```

---

# 8. QUICK CORE GATE — 5–10 MIN

Check:
- app starts
- main workflow works beginning → end
- persistence works if needed
- tests/automarker pass
- no obvious console/server errors

Then commit + push.

Do not spend 45 minutes auditing Core.

---

# 9. USE THE APP EVERY ~60–75 MINUTES

Lecturer explicitly asked for this.

Keep it tiny:

**3-minute real-use checkpoint**
1. Open the app.
2. Run main workflow beginning → end.
3. Try newest feature once.
4. Fix obvious breakage before stacking more work.
5. Push if you reached a stable milestone.

This is not a giant testing ceremony.

---

# 10. AI-ASSISTED COMMIT FORMAT

Course material uses:

```text
Assisted-by: <tool>[<model>]
```

Example:

```text
feat: complete core workflow

Assisted-by: Qoder[<MODEL>]
```

Use exact notation required by the course/exam.
If Auto does not reveal a model, do not invent one.

See `COMMIT_STYLE.md`.

---

# 11. RANK REMAINING REQUIRED WORK

Use **Ask + Efficient**.

```text
Read the approved exam plan / TEST_SPEC and inspect the CURRENT repo.

Core is working and protected.

Do not modify files.

Rank all INCOMPLETE REQUIRED requirements by:
1. marks
2. effort
3. regression risk
4. dependencies
5. confidence of verification

Return only:

Requirement | Marks | Effort | Risk | Dependency | Order

Then:
NEXT MILESTONE: [single best substantial milestone]

Ignore unrequired stretch ideas.

Maximum 250 words.
```

---

# 12. IMPLEMENT EACH MAJOR REQUIRED MILESTONE

Default: **Agent + Auto**.

If you expect rapid back-and-forth or Auto is dragging:
switch this task to **Fast**.

```text
Read:
- TEST_SPEC.md / approved exam plan
- AGENTS.md
- UI_DIRECTION.md

Implement the next recommended REQUIRED milestone completely.

AUTONOMY:
Proceed through routine implementation, build, tests and fixes without asking for routine approval.

Stop only for:
- genuine ambiguity
- destructive/irreversible choice
- missing real secret
- conflicting requirements
- unjustified major architecture change

RULES:
- preserve all passing Core behaviour
- use existing architecture/libraries
- modify all files reasonably required
- no over-engineering
- no unnecessary dependencies
- no unrelated stretch features
- do not weaken/delete tests
- do not invent secrets

UI:
Use the existing visual baseline.
Make new screens/components consistent while building.
Do not do final decorative polish yet.

BEFORE RETURNING:
1. build/start if relevant
2. run focused tests
3. run relevant regression checks
4. fix failures you caused
5. leave repo working

OUTPUT:
No narration.
Return only:
- requirement IDs PASS/FAIL
- tests/checks + result
- changed file count
- blockers
- maximum 3 manual checks
```

Then:
manual quick check → commit with AI trailer → push.

---

# 13. OPTIONAL IDEA / GRAPH / DASHBOARD

Do not silently add it to Core.

```text
Evaluate this unrequired idea against the CURRENT exam state:

[IDEA]

Do NOT implement it.

Tell me:
- does it directly earn/support rubric marks?
- estimated time
- regression risk
- user/visual value
- whether it reuses current architecture
- whether required work remains incomplete

Return:
GO LATER / SKIP / ACTUALLY SUPPORTS MARKED REQUIREMENT

Maximum 100 words.
```

Required marks beat unmarked beauty.

---

# 14. UI STRATEGY — DELIBERATE FROM THE START

Lecturer explicitly warned against generic AI styling:
- glass
- rounded everything
- purple
- gradients
- generic patterns

Use `UI_DIRECTION.md`.

## During Core
Establish:
- shell/layout
- typography
- spacing
- neutral + forest accent palette
- buttons
- inputs
- table/list/card treatment
- responsive basics

## During features
Reuse the same visual language.

## Near the end
One dedicated polish pass.

Do not fully beautify every feature individually.
Do not ignore UI until the final 20 minutes either.

---

# 15. FINAL UI POLISH

Default: **Agent + Auto**.
Use **Fast** if you are actively iterating visually and want faster rounds.

```text
Read UI_DIRECTION.md and inspect the finished application.

Perform ONE focused UI/UX polish pass.

GOAL:
Make it look intentionally designed and product-specific, NOT like a generic AI template.

Preserve all required behaviour.

Improve:
- hierarchy
- spacing/alignment
- typography
- navigation
- forms
- buttons/states
- tables/lists/cards
- empty/loading/error/success states
- responsiveness
- consistency
- product-specific information hierarchy

STRICTLY AVOID:
- purple/blue gradients
- glassmorphism
- glowing blobs
- giant centred hero sections
- pill badges everywhere
- excessive rounded cards
- gratuitous shadows
- three identical feature cards
- emoji as interface icons
- decorative elements with no product purpose

Do not:
- change business logic
- change architecture
- add a heavy UI library
- add new features
- introduce elaborate animation

Then:
1. build/start
2. run relevant regression tests
3. fix regressions caused by styling

OUTPUT:
Maximum 180 words.
Only:
- pages/components improved
- test result
- remaining visual issue
- functionality risk
```

---

# 16. DEBUGGING

First attempt: **Auto**.
If you are burning time / want quick iterations: **Fast**.
Ultimate only after both fail on a high-value blocker.

```text
This exact requirement is failing:

[REQUIREMENT]

Command/check:
[COMMAND]

Exact error/output:
[PASTE]

Relevant logs:
[PASTE ONLY RELEVANT LOGS]

Diagnose ROOT CAUSE first.

Then make the SMALLEST fix.

AUTONOMY:
Run failing check → fix → rerun → relevant regression tests without asking routine approval.

CONSTRAINTS:
- preserve passing requirements
- no unrelated refactor
- do not weaken/delete tests
- add a regression test first if useful/practical

OUTPUT:
- root cause max 3 sentences
- fix
- failing check PASS/FAIL
- regression PASS/FAIL
- files changed
```

---

# 17. LUNCH CHECKPOINT

Before lunch:
- repo/push working
- Core working
- Core pushed
- useful required marks completed
- real app workflow usable
- tests green enough to continue
- no mystery uncommitted work

After lunch use **Ask + Efficient**:

```text
Read TEST_SPEC / approved plan and inspect current repo.

Do not change files.

Return only:

COMPLETED:
- requirements + marks

INCOMPLETE:
- requirements + marks

HEALTH:
- build
- tests
- known failures

NEXT:
- single highest-value substantial milestone

RISK:
- biggest current submission/regression risk

Maximum 220 words.
```

---

# 18. FINAL 60–75 MINUTES

Feature-freeze mindset.

Do not risk a working submission for low-value extras.

Order:
1. full tests/automarker
2. fix real failures
3. manual end-to-end workflow
4. final UI sanity/polish
5. README
6. AI attribution check
7. git status
8. push
9. clean clone
10. follow README
11. final push
12. verify remote

---

# 19. FINAL MARKER AUDIT

Use **Ask + Efficient**.

```text
Act as the final marker.

Read exam plan / TEST_SPEC and inspect CURRENT repo.

Do NOT modify anything.

Return:

Requirement | Marks | Evidence | Test/check | PASS/FAIL | Risk

Then list:
1. missing marks
2. broken/incomplete behaviour
3. test/automarker failures
4. README/setup problems
5. serious usability/UI issues
6. AI attribution/declaration problems
7. secrets/config problems
8. files that should not be committed
9. clone/submission risks

Then give ONLY the THREE highest-value fixes remaining.

Ignore unrequired stretch ideas.

Maximum 450 words.
```

---

# 20. README / CLEAN CLONE

```text
Audit README.md against the actual repo and exam plan.

A marker must be able to run/test it from a clean clone.

Check:
- prerequisites
- install
- required config
- safe example config only
- start/build command
- tests/automarker
- ports/URLs
- DB setup
- required AI declaration
- no real secrets
- commands match actual repo

Make only MINIMUM README/setup corrections.
Do not change app behaviour.

Then give exact clean-clone commands.

Maximum 220 words.
```

---

# 21. CODING TIME MAP

## Planning — 30 min
No code.
Brief → rubric → Qoder plan → sanity check → stack decision.

## Programming starts

### First 5–10 min
Git setup + prove push.

### Next ~1h45
Core/MVP + visual baseline.

### 5–10 min
Core gate + push.

### Rest of morning
Highest-value required milestone(s).

### Lunch
Reset.

### Afternoon first ~2h
Major required milestones.

### Next ~45–60 min
Remaining high-value marks.

### Next ~30–40 min
UI polish.

### Final ~60 min
Audit → fixes → README → clean clone → final push.

---

# 22. FINAL CHECKLIST

- [ ] Git remote/push works
- [ ] latest required work pushed
- [ ] correct branch
- [ ] AI trailers present where required
- [ ] no PAT/API key/real secret committed
- [ ] app builds
- [ ] app starts
- [ ] main workflow works
- [ ] persistence works where required
- [ ] relevant tests/automarker pass
- [ ] app does not look like generic AI template
- [ ] README commands work
- [ ] marker can clone
- [ ] no important untracked files
- [ ] no node_modules/build junk/secret .env
- [ ] final remote commit visible before deadline

---

# 23. IF YOU FORGET EVERYTHING

**1. Git early. Push stable milestones.**

**2. Efficient thinks. Auto builds. Fast rescues/iterates. Ultimate is emergency.**

**3. Required marks first; deliberate UI second; unmarked extras last.**
