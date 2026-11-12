# Deployment Configuration & Rollback Evidence

This project is a static Excel deliverable, so "deployment" means publishing a versioned release on GitHub and "rollback" means restoring a previous tagged version.

## Deployment configuration

| Item | Value |
|------|-------|
| Hosting | GitHub public repository (free tier) |
| Repository | `simple-expense-tracker-excel` |
| Branch | `main` |
| Release artifact | `Simple_Expense_Tracker.xlsx` |
| Versioning | Git tags (`v1.0.0`, `v1.0.1`, ...) |
| Cost | Free resources only |

### Deploy steps

```bash
git init
git add .
git commit -m "v1.0.0: Simple Expense Tracker with monthly summary and validation"
git branch -M main
git remote add origin https://github.com/<your-username>/simple-expense-tracker-excel.git
git push -u origin main
git tag -a v1.0.0 -m "Initial release"
git push origin v1.0.0
```

## Rollback procedure

If a later change breaks the workbook (wrong totals, failed validation), restore the last good tagged version without rewriting history:

```bash
# See available versions
git tag --list
git log --oneline

# Restore the workbook from the last good tag
git checkout v1.0.0 -- Simple_Expense_Tracker.xlsx
git commit -m "Rollback: restore workbook to v1.0.0"
git push
```

Alternative: `git revert <bad-commit-hash>` to undo one specific commit.

## Rollback evidence

Run the demonstration below after publishing and paste your real terminal output in this section (or add screenshots to `docs/`).

1. Make a deliberate bad edit (for example, change a `SUMIFS` formula so a Validation check shows FAIL), then commit and push it as `v1.0.1-bad`.
2. Run the rollback commands above.
3. Open the restored workbook and confirm the **Validation** sheet shows all PASS again.

### Evidence log

```text
# Paste output of: git log --oneline
# Paste output of: git tag --list
# Paste output showing the rollback commit
```

Screenshot of Validation sheet after rollback: `docs/rollback-validation.png`
