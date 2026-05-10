# Vrumm Skill Pack 🏎️

> *Because typing `git checkout -b fix-that-annoying-bug-that-should-not-exist upstream/staging` is not a personality trait.*

Vrumm is a Claude Code skill pack that handles the boring git ceremony so you can focus on the part where you pretend to know what you're doing.

---

## Skills

### `/vrumm` — Create a branch

Asks you two questions a toddler could answer, then creates a branch like a responsible adult.

1. **fix or feat?** — Did you break something or are you adding something that will break later?
2. **From main or staging?** — Do you like stability or living dangerously?

```
/vrumm auth-timeout
```

Result: `fix-auth-timeout` branched off `upstream/staging`. Done. Go code.

---

### `/vrumm-go` — Commit › Push › Open PR

The finish line. Stages your files, writes the commit message (with correct prefix, automatically, like an adult), pushes, and opens the PR.

```
/vrumm-go corrige validação de token expirado
```

Result: commit `fix: corrige validação de token expirado`, pushed, PR open. You look like you know git.

---

## Why

Because the average developer runs the following sequence at least 4 times per day:

```bash
git fetch upstream           # forgot to do this
git checkout -b feat-thing upstream/main
# ... codes for 20 minutes ...
git add .                    # added node_modules, oops
git commit -m "wip"          # commit message archaeology will judge you
git push origin HEAD
gh pr create --base main --title "wip" --body ""
```

Vrumm doesn't judge. Vrumm just fixes it.

---

## Installation

Drop the `.claude-plugin/` folder into your Claude Code plugins directory, or install via the Claude Code plugin registry.

---

## Name

**Vrumm** is the sound a branch makes when it accelerates away from `upstream/main` at the speed of `git checkout`. 

*It is not a typo of "vroom". It has two m's. This is intentional and non-negotiable.*
