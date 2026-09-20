# Issue tracker for this repo — GitHub

Wayfinder's map and tickets live as **GitHub issues** on this repo, so the whole
group can read the decision record without running Claude or installing anything.

Use the `gh` CLI for every operation. It infers the repo from `git remote -v`
when run inside this clone.

## Wayfinding operations

- **Map** — one issue labelled `wayfinder:map`, holding Destination / Notes /
  Decisions-so-far / Fog.
  `gh issue create --label wayfinder:map --title "..." --body "..."`

- **Child ticket** — one issue per open decision. Put `Part of #<map>` at the
  top of the body and add it to the task list in the map body. Label it with
  its type: `wayfinder:research`, `wayfinder:prototype`, `wayfinder:grilling`,
  or `wayfinder:task`.

- **Blocking** — a `Blocked by: #<n>, #<n>` line at the top of the child body.
  A ticket is unblocked when every issue it names is closed.

- **Frontier** — list the map's open children, drop any with an open blocker or
  an assignee, take the first in map order.
  `gh issue list --state open --json number,title,body,labels,assignees`

- **Claim** — `gh issue edit <n> --add-assignee @me`. Do this before any work.

- **Resolve** — `gh issue comment <n> --body "<the answer>"`, then
  `gh issue close <n>`, then append a one-line gist plus link to the map's
  Decisions-so-far.

- **Read a ticket** — `gh issue view <n> --comments`

## Rules that override the upstream skill

1. **Sathvik's words stay verbatim.** A decision that came out of his mouth goes
   into the issue in a `>` quote block, unedited. Write scaffolding around it,
   never inside it. This is the whole reason the record is worth keeping.

2. **One question at a time** when grilling him. Never a form, never five at once.

3. **Nothing personal goes in this repo.** Groupmates can read every issue. His
   vault — ADHD profile, daily notes, money, DJ brand — stays in
   `~/Documents/obsidian/streamline`, which is private and stays that way.

4. **Mirror the state back to the vault.** When the map moves, update
   `~/Documents/obsidian/streamline/projects/capstone/log.md` with a
   `Next action:` line. That is what the morning brief reads.

5. **Write for the group, not just for him.** Someone who missed the session
   should understand a closed issue from its title and comments alone.
