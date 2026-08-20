---
name: work-todo
description: Add, update, move, or complete work todos in this Obsidian vault. Use whenever the user asks to track a work task or add details to an existing work todo.
---

# Work Todo

Use `20 Work/TODO.md` as the task dashboard and `20 Work/Tasks/` for detail notes.

For a new task:
1. Create `20 Work/Tasks/YYYY-MM-DD - <short title>.md` using `90 Templates/Work Task.md` as the shape.
2. Fill only information the user provided; do not invent due dates, priority, or company facts.
3. Add one checkbox link to `20 Work/TODO.md`: `- [ ] [[Tasks/YYYY-MM-DD - <short title>|<short title>]]`.
4. Put it in `Next` by default, `Now` when the user says it is current/urgent, or `Waiting` when blocked.

For updates, keep the task note and dashboard status consistent. When completed, set `status: done`, mark the checkbox `[x]`, and move it to `Done`. Never delete completed tasks unless explicitly asked.
