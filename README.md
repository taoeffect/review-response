# Review Response

An agent skill to work through a code review one issue at a time — investigating each issue, addressing legitimate ones via the `tasks` skill workflow (TODO + STEP files), and dismissing the rest.

## Installation

```
$ npx skills add taoeffect/review-response
```

## Usage

1. Have a task set up under `.agents/tasks/<task name>/` (see the `tasks` skill)
2. Have a review file stored at `.agents/review/<task name>/<review file>` (e.g. created by the `code-review` skill)
3. Run this skill (tell the LLM: `run the 'review-response' skill for task '<task name>' with review '<review file>'`)

If you omit the task name or review file, the skill will ask you for them (the review file is auto-detected if there's exactly one).
