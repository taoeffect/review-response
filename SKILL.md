---
name: review-response
description: "Use when the user asks to respond to, address, or work through a code review for a task — e.g. 'respond to the review for task <task name>', 'address review <review file>', or 'work through the review issues'."
---

# Review Response

This skill guides you through addressing issues from a review file, one issue at a time, in the context of a task.

## Required information

Two pieces of information are needed:

- `<task name>` - the name of the task the review belongs to (tasks live in `.agents/tasks/<task name>/`).
- `<review file>` - the review file name (e.g. `REVIEW-1.md`). Reviews are stored in `.agents/review/<task name>/`.

If the user did not specify the `<task name>` in their prompt, STOP and ask the user to provide it before doing anything else — you need it to locate both the task and the review file.

If the user did not specify the `<review file>`, look in `.agents/review/<task name>/`:
- If there is exactly one review file, use it.
- If there are multiple (or none), STOP and ask the user which review file to use (or where it's located).

## Procedure

1. Load the `tasks` skill (read its SKILL.md and follow it for all task/TODO/STEP file conventions).
2. Review the task `<task name>` for context (read its `PLAN.md`, `KNOWLEDGE.md` if it exists, and any other files if needed)
3. Read the review file at `.agents/review/<task name>/<review file>`.
4. Work through the review **one issue at a time**. For each issue:
   1. Investigate whether it is a legitimate, real, important issue.
   2. If legitimate: create a TODO for it in `TODOs.md` and a corresponding `STEP-<N>.md` file, then complete that TODO. As part of the last subtask, mark the issue in the review file as addressed (check its checkbox).
   3. If not legitimate: mark the issue in the review file as 'dismissed', with a brief note explaining why.
5. After handling one issue, stop and wait for further instruction from the user (they will likely ask you to handle the next issue, possibly in a new_session). Do not proceed to the next issue unless instructed otherwise.
