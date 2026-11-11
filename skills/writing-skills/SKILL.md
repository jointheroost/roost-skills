---
name: writing-skills
description: "How a Roost bot writes a good skill: the standard name, a description that says when to use it, when to add scripts or reference files, the create_skill and update_skill tools, and a short test before the skill is used. Use it when the person asks a bot to make, change, or improve a skill, or when a bot sees a task that it will do again and again."
license: Apache-2.0
metadata:
  version: "1.0.0"
  category: productivity
---

# Writing skills

A skill is a folder with a `SKILL.md` file and the files it uses. A bot reads the skill when its description matches the work. A good skill is short, specific, and tested.

## When to make a skill

Make a skill when the same kind of work comes back and needs the same steps, rules, or files each time. Do not make a skill for a one-time task, or for a fact about the person (use a memory for that).

## The name

- Use the Agent Skills name: 1 to 64 characters, lowercase letters, digits, and single dashes. Examples: `weekly-review`, `invoice-check`.
- Name the work, not the bot: `expense-report`, not `sable-helper`.
- Names are unique on the hub. Call `list_skills` first, and change an existing skill instead of making a second one.

## The description

The description decides when a bot loads the skill. Write one or two sentences, at most 1024 characters:

1. Say what the skill does.
2. Say when to use it, with the words the person says ("when the person asks for a weekly review").

Bad: "Helps with documents." Good: "Fill and check PDF forms. Use it when the person sends a PDF form or asks to fill one in."

## The body

- Start with one line on the goal.
- Give the steps in order. One action per step.
- Give the rules that always apply (what never to do, which tools to use).
- Say what "done" looks like: the output, its length, and where it goes.
- Keep `SKILL.md` under about 500 lines. Move long details into `references/<topic>.md` and say in `SKILL.md` when to read each file.

## Files beside SKILL.md

| Folder | Use it for |
|---|---|
| `references/` | Long instructions, tables, or examples that a bot reads only when it needs them. |
| `assets/` | Templates and files that the output uses (a document template, a logo). |
| `scripts/` | Code that a bot runs when the same steps must be exact every time (a converter, a check). |

Add a script only when written steps are not enough. A script runs on a node with the bot's own access, so keep it small, read only what it needs, and write only inside the working folder. Do not download code in a script. Roost shows a warning for skills with scripts that are not from Roost skills.

Paths in `SKILL.md` are relative to the skill folder, for example `scripts/check.py`.

## Make or change the skill

- **New skill:** call `create_skill` with `name`, `description`, and `body` (the text after the frontmatter). Then turn it on for a bot with `update_bot` and its `skills` list.
- **Change a skill:** call `update_skill` with only the fields that change. A change to a skill from a repository is a local change: the person sees "Changed here", and Roost asks before an update replaces it.
- A turn that a member started cannot make or change skills. Ask the owner.

## Test it before it is used

1. Read the skill again with `read_skill`, as a bot that sees it for the first time.
2. Try one real example: follow the steps and check that the result matches "done".
3. Try one example that should not use the skill, and check that the description does not match it.
4. Fix what was unclear, then tell the person what the skill does and which bots have it.

## Evals and packaging

For evals with many test prompts, benchmarks, and packaging a skill for other tools, use the `skill-creator` skill from Roost skills.
