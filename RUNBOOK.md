# RUNBOOK.md — how-to-contribute

## Metadata

| Field | Value |
|---|---|
| **Owner** | Kevin P. Inscoe |
| **Last Updated** | 2026-06-19 |
| **Last Tested** | 2026-06-19 |
| **Expected Duration** | < 5 minutes |
| **Risk Level** | Low |
| **Repo** | github.com/kevinpinscoe/how-to-contribute |

---

## Purpose

> Covers how to maintain and publish the contribution guide held in this repo.
> This is a documentation-only repository — there is no build step, service, or
> runtime to operate.

---

## When to Use This Runbook

- **Use when:** updating `CONTRIBUTING.md`, the `README.md`, or other guidance
  in this repo, and publishing those changes.
- **Do NOT use when:** working on a downstream project that merely links here —
  follow that project's own runbook instead.

---

## Prerequisites

- [ ] Local clone at `~/Projects/public/how-to-contribute`
- [ ] `git` installed and SSH access to GitHub (`ssh -T git@github.com`)
- [ ] If `mise.toml` is present in the repo: run `mise install && mise doctor` before proceeding

---

## Stack

| Component | Details |
|---|---|
| **Language / Runtime** | None — Markdown documentation only |
| **External Services** | GitHub (`github.com/kevinpinscoe/how-to-contribute`) |
| **Databases / File Stores** | None |
| **Credentials / Secrets** | None |

---

## Step-by-Step Procedure

### Step 1 — Edit the guidance

**Why:** make the documentation change.

```bash
cd ~/Projects/public/how-to-contribute
vim CONTRIBUTING.md   # or README.md
```

**If this fails:** confirm you are in the repo root (`git rev-parse --show-toplevel`).

---

### Step 2 — Commit and push

**Why:** publish the change to GitHub so downstream projects pick it up.

```bash
git add -A
git commit -m "docs: <short description of the change>"
git push
```

**Expected output:** `git push` reports the branch is up to date with `origin/main`.

**If this fails:** check `git status` and resolve any conflicts, then retry.

---

## Verification

```bash
git -C ~/Projects/public/how-to-contribute log --oneline -3
git -C ~/Projects/public/how-to-contribute status
```

**Expected output:** your latest commit appears at the top of the log; the
working tree is clean.

**Success criteria:** changes are committed, pushed, and visible at
https://github.com/kevinpinscoe/how-to-contribute.

---

## Rollback Procedure

1. Identify the commit to revert: `git log --oneline`.
2. Revert it: `git revert <commit-sha>`.
3. Push the revert: `git push`.

---

## Escalation

| Condition | Contact | How |
|---|---|---|
| Repo access lost | Kevin P. Inscoe | kevin.inscoe@gmail.com |

---

## Troubleshooting

| Symptom | Likely Cause | Resolution |
|---|---|---|
| `git push` rejected | Local branch behind remote | `git pull --rebase` then push |
| SSH auth failure | Key not loaded | `ssh -T git@github.com`; add key with `ssh-add` |

---

## Logs

```bash
git -C ~/Projects/public/how-to-contribute log --oneline -20
```

---

## Maintenance Notes

- **Last game-day test:** 2026-06-19 (initial scaffold)
- **Next scheduled review:** as needed when contribution conventions change
- **Known drift risks:** downstream projects linking here may reference sections
  that are later renamed — keep section headings stable.
