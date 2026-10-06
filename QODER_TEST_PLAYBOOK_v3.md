# QODER TEST PLAYBOOK v3 — COMS3011A

Use this as a **static open-book note** during the test.

The key idea:
**Turn the test brief into a scoring map before Qoder builds anything.**
Qoder should never have to guess what “minimum functionality” means.

---

# 0. QODER MODES

## Use these by default
- **Ask + Efficient** → read brief, plan, debug, audit, compare against rubric.
- **Agent + Auto** → implement normal features.
- **Agent + Performance** → only if Auto genuinely struggles.
- **Ultimate / Experts / Quest** → avoid unless there is a very good reason.

## Main rhythm
1. Read brief yourself.
2. Ask Qoder to convert it into `TEST_SPEC.md`.
3. Verify `TEST_SPEC.md` against the real brief.
4. Implement CORE only.
5. Test CORE.
6. Commit + push.
7. Rank remaining features by **marks vs time/risk**.
8. Implement one coherent feature at a time.
9. Test + commit + push.
10. Freeze features ~25–30 min before the end.
11. Final audit.
12. Clean-clone test.
13. Final push.

---

# 1. START OF TEST — YOU READ FIRST

Spend about 2–3 minutes scanning the brief yourself.

Look specifically for:
- what must be built
- required stack
- required / core features
- optional features
- marks / weighting
- pass/fail or zero-risk items
- persistence requirements
- required database/services
- required environment variables
- secrets / credentials / API keys
- forbidden implementation choices
- README / run requirements
- test requirements
- submission requirements

Do not start coding before you know what earns marks.

---

# 2. FIRST QODER PROMPT — TURN THE PDF INTO A SCORING MAP

## MODE
**Ask + Efficient**

Attach the test brief / rubric **once**.

## PROMPT

```text
READ ONLY. Do not change any files.

Read the ENTIRE attached test brief and marking rubric.

I need you to convert it into a scoring-oriented implementation specification for a 2.5-hour test.

For EVERY requirement, extract:

- ID / short name
- whether it is REQUIRED / CORE / OPTIONAL
- marks or weighting, if given
- exact behaviour required
- exact constraints that must not be violated
- exact acceptance condition / "done when"
- dependencies on other requirements
- whether failure could block marking or cause major mark loss

Also identify EVERY required configuration value, including:
- environment variables
- database credentials
- API keys
- tokens
- external service URLs
- ports
- runtime versions

For each configuration value, state:
- whether it is a REAL SECRET or SAFE LOCAL/DEMO CONFIGURATION
- whether it must NOT be committed to Git
- whether it should be supplied via environment variable / .env / compose / other mechanism
- whether `.env.example` is required
- whether README setup instructions are required
- how the marker is expected to obtain/provide the value
- whether a clean clone can run without access to my private machine

Then output Markdown using EXACTLY these sections:

# CORE / MUST WORK
Everything required for the application to be considered functional or to avoid a zero / major penalty.

For each item use:
## C1 — <name>
Type:
Marks:
Requirement:
Constraints:
Done when:
Depends on:

# FEATURE BACKLOG
Every additional feature that earns marks.

For each item use:
## F1 — <name>
Marks:
Requirement:
Constraints:
Done when:
Depends on:

# CONFIGURATION / SECRETS
For every configuration item use:
## <name>
Type: REAL SECRET / SAFE LOCAL CONFIG / NORMAL CONFIG
Required:
How supplied:
Commit to Git: YES / NO
Marker setup:
Clean-clone impact:

# DO NOT VIOLATE
Every forbidden implementation choice, edge case, security mistake, or rule that an AI agent might accidentally break.

# PRIORITY ORDER
Give the best implementation order for a 2.5-hour test, prioritising:
1. pass/fail or zero-risk items
2. required core
3. high-mark / low-risk features
4. lower-value or risky features last

# FINAL SUBMISSION CHECK
Everything that must be true before submission, including:
- no real secrets, PATs, API keys, or production credentials committed
- required environment variables documented
- secret-containing `.env` files ignored
- `.env.example` present if needed
- clean clone can be run using the documented setup
- marker does not need my personal credentials unless the brief explicitly says so

Rules:
- Do not invent requirements.
- Do not remove awkward edge cases.
- Use the rubric wording closely.
- Do not invent secrets or credentials.
- Do not describe implementation unless the brief explicitly requires a specific implementation.
- Keep it concise enough to use as a working specification.
- Output Markdown only.
```

---

# 3. CREATE `TEST_SPEC.md`

Create a file in the test repo called:

`TEST_SPEC.md`

Paste Qoder’s Markdown output into it.

## VERY IMPORTANT
Spend 2–3 minutes comparing `TEST_SPEC.md` against the real brief.

Check:
- all CORE items present
- all FEATURE items present
- marks correct
- exact “Done when” conditions correct
- no constraints missing
- no invented requirements
- configuration/secrets classification makes sense
- Qoder has not invented credentials or assumed the marker has private values

Fix `TEST_SPEC.md` manually if necessary.

From this point onward, prefer:

`@TEST_SPEC.md`

instead of repeatedly attaching the full PDF.

---

# 4. REPO SETUP

If the lecturer gives you a starter repo, use that.

If you must create your own Gitea repo:

```bash
git clone https://sdp.ms.wits.ac.za/<username>/<repo-name>.git
cd <repo-name>
git status
git remote -v
```

Open that exact folder in Qoder.

Do not spend 30+ minutes coding before confirming the repo and remote are correct.

---

# 5. FIRST REAL BUILD — IMPLEMENT CORE ONLY

## MODE
**Agent + Auto**

## PROMPT

```text
Read @TEST_SPEC.md completely before changing anything.

Implement ONLY everything listed under:

# CORE / MUST WORK

Do NOT implement anything from # FEATURE BACKLOG yet.

GOAL:
Get every CORE acceptance condition passing as quickly and reliably as possible.

CONSTRAINTS:
- follow TEST_SPEC.md exactly
- follow every rule under # DO NOT VIOLATE
- follow # CONFIGURATION / SECRETS exactly
- never hard-code or commit real secrets, PATs, API keys, or production credentials
- if a required real secret/config value is missing, STOP and tell me exactly what is needed instead of inventing one
- do not add optional features yet
- do not add unnecessary dependencies
- do not refactor unrelated working code
- prefer simple, reliable implementation over clever architecture

WHEN FINISHED:
1. install/build/start the project as required
2. test every CORE item
3. run any existing relevant tests
4. report each CORE ID as PASS / FAIL
5. list every file changed
6. list any remaining CORE problem
7. report any configuration value the marker will need
8. stop

Do not move into FEATURE BACKLOG.
```

## AFTER IT FINISHES
Check:
- app starts
- each CORE item actually works
- persistence works if required
- files changed make sense
- tests/build pass
- no secrets accidentally appeared in tracked files

Then:

```bash
git status
git diff
git add .
git commit -m "feat: implement required core"
git push
```

---

# 6. DECIDE WHICH FEATURE TO DO NEXT

Do NOT blindly do features in numerical order.

Use:

**marks vs time/risk**

Example:
- F1 = 8 marks, likely 45 min, high risk
- F2 = 3 marks, likely 5 min, low risk
- F3 = 5 marks, likely 15 min, low/medium risk
- F4 = 7 marks, likely 20 min, medium risk

A sensible order may be:

F2 → F3 → F4 → only then consider F1

The goal is to maximise secure marks, not to attempt the fanciest feature.

---

# 7. ASK QODER TO RANK THE BACKLOG

## MODE
**Ask + Efficient**

Use this after CORE works.

```text
READ ONLY. Do not modify files.

Read @TEST_SPEC.md and inspect the current repository.

For every item in # FEATURE BACKLOG, estimate:

- marks available
- whether prerequisites are already satisfied
- implementation difficulty: LOW / MEDIUM / HIGH
- risk of breaking working CORE: LOW / MEDIUM / HIGH
- approximate relative effort: SHORT / MEDIUM / LONG
- whether it introduces new configuration/secrets
- whether it is a good next feature

Then recommend the best feature order to maximise reliable marks in the remaining time.

Do not recommend optional polish.
Do not change files.
Keep the answer short.
```

You make the final choice.

---

# 8. IMPLEMENT ONE FEATURE

## MODE
**Agent + Auto**

## PROMPT TEMPLATE

```text
Read @TEST_SPEC.md.

Implement FEATURE [ID] — [FEATURE NAME].

Use the exact requirement and Done When condition from TEST_SPEC.md.

CONSTRAINTS:
- preserve all currently working CORE behaviour
- follow every relevant rule under # DO NOT VIOLATE
- follow # CONFIGURATION / SECRETS
- never hard-code or commit real secrets
- if a required real secret/config value is missing, STOP and tell me what is needed instead of inventing one
- do not change unrelated features
- do not add unnecessary dependencies
- do not weaken or bypass existing requirements

WHEN FINISHED:
1. test this feature against its exact Done When condition
2. run the relevant existing tests
3. tell me PASS / FAIL for this feature
4. list the files changed
5. tell me exactly how I can manually verify it
6. report any new environment/configuration requirement
7. stop
```

Then check it yourself.

Checkpoint:

```bash
git status
git diff
git add .
git commit -m "feat: implement <feature>"
git push
```

---

# 9. GOOD FEATURE SIZE

## Good
- “Implement F3 Tags exactly as specified.”
- “Implement F4 REST API exactly as specified.”
- “Implement the required Docker setup.”
- “Implement sorting by all required fields.”

## Too small
- “Add one button.”
- “Change one variable.”
- “Add one CSS class.”

## Too large
- “Finish the entire rest of the exam.”
- “Build every remaining feature.”

One coherent feature at a time.

---

# 10. DEBUGGING / ERROR PROMPT

## MODE
Start with **Ask + Efficient** for diagnosis.

If the fix is obvious and contained:
**Agent + Auto**

## PROMPT

```text
This exact behaviour is failing.

WHAT I DID:
[steps / exact command]

EXPECTED:
[what should happen]

ACTUAL:
[what happened]

EXACT ERROR / OUTPUT:
[paste the full error]

Read @TEST_SPEC.md.

Diagnose the root cause first.

Then make the SMALLEST fix necessary.

CONSTRAINTS:
- preserve all currently working behaviour
- do not redesign the application
- do not add a dependency unless genuinely necessary
- preserve all TEST_SPEC.md requirements
- preserve # CONFIGURATION / SECRETS
- never hard-code or commit a real secret as a workaround
- if the error is caused by a missing required secret/config value, STOP and tell me exactly what value/configuration is expected and how it should be supplied
- do not suppress the error without fixing the cause

AFTER THE FIX:
1. rerun the failing command/check
2. run the relevant existing tests
3. explain the root cause in 2–3 sentences
4. list files changed
```

Never just say:

`fix it`

Give the exact error.

---

# 11. IF QODER MAKES A BAD CHANGE

```text
The last change is not acceptable.

Specific problem:
[describe exactly what is wrong]

Required behaviour:
[paste the exact requirement / Done When condition]

Correct only this problem.

Do not redesign the feature.
Do not modify unrelated working code.
Preserve all TEST_SPEC.md constraints.
Do not introduce or hard-code secrets.

After correcting it:
1. rerun the relevant check/tests
2. list files changed
3. stop
```

Useful Git checks:

```bash
git status
git diff
git log --oneline -5
```

---

# 12. MID-TEST RUBRIC CHECK

## MODE
**Ask + Efficient**

```text
READ ONLY. Do not modify files.

Read @TEST_SPEC.md and inspect the current repository.

Create a short table:

Requirement ID | PASS / PARTIAL / FAIL | Evidence | Smallest next action

Order the results by:
1. pass/fail blockers
2. CORE failures
3. highest-mark quick wins
4. lower-value work

Also flag:
- undocumented environment variables
- missing `.env.example` where required
- any likely committed secret
- anything that would stop a clean clone from running

Do not suggest refactors or polish unless they directly earn marks.
```

---

# 13. README / CONFIGURATION CHECK

## MODE
**Ask + Efficient** first.

```text
READ ONLY.

Read @TEST_SPEC.md and inspect the current repository.

Check whether README.md gives a marker everything needed to run this project from a clean clone.

Check:
- required runtime/version
- dependency install command
- environment setup
- every required environment variable
- whether `.env.example` is required and accurate
- exact start command
- exact test command
- Docker commands if required
- database/service setup
- any required seed/migration command
- whether the marker needs any value that is not documented
- whether any real secret has accidentally been documented or committed

Report only missing or incorrect items.
Do not modify files.
```

If changes are needed, switch to **Agent + Auto** and ask it to update only README / `.env.example` as required.

---

# 14. FEATURE FREEZE

About **25–30 minutes before the deadline**:

STOP adding ambitious new features.

From here:
- fix blockers
- verify rubric
- verify README
- verify environment setup
- verify tests
- clean clone
- final push

Do not start a risky feature late.

---

# 15. FINAL AUDIT

## MODE
**Ask + Efficient**

```text
READ ONLY. Do not modify anything.

Audit this repository against @TEST_SPEC.md line by line.

For every CORE and FEATURE requirement return:

ID
PASS / PARTIAL / FAIL
Evidence
Smallest action required if not PASS

Also specifically check:
- application installs and starts
- required functionality is reachable
- persistence works if required
- tests run from the documented command
- README matches the actual repository
- required files exist
- every required environment variable is documented
- `.env.example` exists and is accurate if needed
- secret-containing `.env` files are ignored
- no forbidden implementation choice from # DO NOT VIOLATE was used
- no real secrets, PATs, API keys, or production credentials appear committed
- Dockerfile/compose files do not bake real secrets into images
- marker can run the project from a clean clone using only documented setup
- no important uncommitted changes are being forgotten

Do not suggest optional improvements.
Only identify things that could lose marks.
Order problems from most dangerous to least dangerous.
```

Fix only genuine mark-losers.

---

# 16. CLEAN-CLONE TEST

From outside the working repo:

```bash
cd ..
git clone <YOUR-SUBMISSION-HTTPS-URL> final-check
cd final-check
```

Follow ONLY the README.

Typical checks:

```bash
npm install
npm test
npm run dev
```

Or whatever the brief requires.

If environment configuration is required:
- use only the documented values/process
- do not copy hidden files from your original working directory
- confirm `.env.example` is sufficient if one is expected

If Docker is required:

```bash
docker compose config
docker compose build
docker compose up -d
docker compose ps
```

Pretend you are the marker.

---

# 17. FINAL GIT CHECK

Before the deadline:

```bash
git status
git remote -v
git log --oneline -5
git push
```

Make sure:
- correct repo
- correct branch
- latest work committed
- latest commit pushed
- correct submission URL
- no secret-containing files accidentally staged/committed

Optional quick tracked-file check:

```bash
git status
git diff --cached
```

---

# 18. GITEA / PAT EMERGENCY

If push fails:

```bash
git push
git remote -v
```

If credentials are needed:

```bash
git config --global credential.helper store
git push
```

Then:
- Username = Gitea username
- Password = PAT

Never put the PAT in:
- source code
- README
- `TEST_SPEC.md`
- Qoder
- committed `.env`
- Dockerfile
- compose file
- committed URLs

On Windows, an old saved credential may be in:

```text
C:\Users\<username>\.git-credentials
```

If a PAT is exposed, revoke it and create a new one.

---

# 19. DOCKER QUICK COMMANDS

Only if required/useful:

```bash
docker compose config
docker compose build
docker compose up -d
docker compose ps
docker compose logs
docker compose restart
docker compose down
```

Destroy volumes too:

```bash
docker compose down -v
```

Remember:
- `Dockerfile` = image recipe
- image = packaged app
- container = running image
- `compose.yml` = multiple services
- volume = persistent data
- another Compose service is reached by its service name, not `localhost`
- Docker can CONSUME secrets/configuration, but it does not make hard-coded secrets safe
- never bake real secrets into an image

---

# 20. CONFIGURATION / SECRETS RULE

## Safe local/demo config
Example:
- local Postgres username/password for a disposable Docker Compose database
- local port number
- test-only database name

These may be committed if the brief expects a reproducible local stack and they are not real-world credentials.

## Real secrets
Examples:
- Gitea/GitHub PAT
- API keys
- Supabase service-role key
- AWS/Azure credentials
- real production DB password

Never commit these.

Typical pattern:

```text
.env            ← real values, ignored
.env.example    ← variable names/placeholders, committed
README.md       ← explains how marker supplies values
```

Docker may receive them at runtime:

```yaml
environment:
  API_KEY: ${API_KEY}
```

But do NOT do:

```dockerfile
ENV API_KEY=real-secret-here
```

---

# 21. CONTEXT / CREDIT RULES

- Attach the full PDF once.
- Convert it into `TEST_SPEC.md`.
- Use `@TEST_SPEC.md` for the rest of the test.
- Use **Ask + Efficient** for planning/debugging/audits.
- Use **Agent + Auto** for implementation.
- Use Performance only when genuinely necessary.
- Do not repeatedly ask Qoder to rediscover the same context.
- Do not generate Repo Wiki / Knowledge Cards during the test unless essential.
- If a chat becomes huge or changes topic, start a fresh chat and reference `@TEST_SPEC.md`.

---

# 22. QUEST?

Default workflow:

**Ask → Agent → test → commit**

Use Quest only if:
- CORE already works
- you have a clearly isolated larger feature
- you know exactly what you want
- there is enough time to review its spec and result

Do NOT begin with:

`Here is the exam PDF. Build everything in Quest.`

---

# 23. 2.5-HOUR TIMELINE

## 0–10 min
- read brief
- Ask + Efficient
- create and verify `TEST_SPEC.md`
- confirm configuration/secrets requirements
- repo ready

## 10–40 min
- Agent + Auto
- implement CORE only
- test
- first commit + push

## 40–105 min
- rank feature backlog
- implement highest-value sensible features
- one feature at a time
- test + commit + push

## 105–120 min
- mid-test audit
- tests
- README/configuration
- quick remaining mark wins

## 120–145 min
- feature freeze
- final audit
- clean-clone test
- fix blockers only

## 145–150 min
- `git status`
- `git log`
- `git push`
- verify submission URL
- stop making risky changes

---

# 24. TEST MANTRAS

**Qoder does not know what “minimum” means unless TEST_SPEC defines it.**

**CORE first.**

**Then maximise marks per time/risk.**

**Rubric wording beats your assumptions.**

**One coherent feature → check it → commit it.**

**Exact error beats “fix it”.**

**Never invent or hard-code a missing real secret.**

**Docker solves reproducibility, not secret storage.**

**Working > fancy.**

**A change not pushed is not safely submitted.**

**Clean clone + README = marker reality.**
