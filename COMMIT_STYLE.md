# COMMIT_STYLE.md — Git + AI Attribution

Commit stable milestones regularly.

## Subject examples

```text
feat: complete core workflow
feat: add reporting filters
fix: persist edited records correctly
test: cover validation rules
docs: add run and test instructions
style: polish responsive layout
```

Use a short imperative summary.

---

# AI-ASSISTED CODE

Course material uses:

```text
Assisted-by: <tool>[<model>]
```

For Qoder:

```text
Assisted-by: Qoder[<MODEL>]
```

Use exact course/exam notation.
If Auto does not expose the underlying model, do not invent one.

## Bash

```bash
git add .
git commit -m "feat: complete core workflow" \
  -m "Assisted-by: Qoder[<MODEL>]"
git push
```

## PowerShell

```powershell
git add .
git commit -m "feat: complete core workflow" -m "Assisted-by: Qoder[<MODEL>]"
git push
```

Do not substitute `Co-Authored-By` if the course requires `Assisted-by`.

---

# GOOD CHECKPOINTS

Commit/push:
- after Core is stable
- after each substantial required milestone
- before lunch
- after significant UI polish
- before final clean-clone check
- final verified submission

Do not commit broken states merely because an hour passed.

---

# BEFORE COMMIT

```bash
git status
git diff
```

Check:
- expected files only
- no `.env` with real secrets
- no PAT/API key
- no node_modules
- no accidental build junk
- relevant tests/checks pass

---

# FINAL CHECK

```bash
git status
git log -1 --oneline
git remote -v
```

Confirm the latest commit is visible on the remote before the deadline.
