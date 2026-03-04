# Codex GitHub Workflow (Mandatory)

## Core rule
Source of truth for website code is GitHub only:
`https://github.com/egorande228/website-mob-cash-lama.git`

Local clone is temporary and used only while editing.

## Start work (temporary clone)
1. Clone when needed:
   - `git clone https://github.com/egorande228/website-mob-cash-lama.git`
2. Open the repo root.
3. Check branch/status:
   - `git status -sb`
   - `git remote -v`

## During work
1. Edit files only inside this repository clone.
2. Commit in small logical steps.
3. Push after each completed task:
   - `git push origin main`

## Finish work
1. Ensure remote is up to date and clean:
   - `git status -sb`
   - `git push origin main`
2. If no local copy is needed, remove the clone from the laptop.

## Strict constraints
1. Do not treat laptop folders as source of truth.
2. Do not keep unpushed changes locally.
3. Source of truth is GitHub only.

## Recovery / sync checklist
1. `git fetch origin`
2. `git status -sb`
3. If needed: `git pull --rebase origin main`
4. Continue edits.

## Cross-chat continuity
Any new chat/session can continue from a fresh clone after `git status` check.
