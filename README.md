# Roost skills

Skills for Roost bots, in the [Agent Skills](https://agentskills.io/specification) format. Each skill is a folder with a `SKILL.md` file and the files it uses.

Roost includes this repository in every hub as **Roost skills**. Its skills show in the catalog on the Skills screen in Marketplace. A skill does nothing until you add it to your hub and turn it on for a bot.

## Use it in Roost

You do not need to do anything. Every Roost hub reads this repository and checks it for updates every 6 hours. Roost never updates a skill by itself: a skill with a newer version shows **Update**, and you choose when to apply it.

To hide these skills, open **Marketplace > Skills**, open the **Roost skills** card menu, and select **Turn off**. Skills that you already added stay.

To add another skill repository, select **Add repository** on the Skills screen and paste its GitHub link, for example `https://github.com/owner/repo`.

## What is here

| Skill | What it does | Scripts |
|---|---|---|
| `weekly-review` | Sums up the week from tasks, mail, calendar, and usage. | No |
| `inbox-triage` | Sorts new mail, drafts simple replies, and flags the rest. | No |
| `release-notes` | Writes release notes from merged pull requests. | No |
| `writing-skills` | Teaches a bot how to write and test a good skill. | No |
| `docx`, `pdf`, `pptx`, `xlsx` | Make, read, and change Word, PDF, PowerPoint, and Excel files. | Yes (Python) |
| `frontend-design`, `canvas-design`, `algorithmic-art`, `theme-factory` | Design work: web pages, posters, generative art, and themes. | `algorithmic-art` has a template |
| `web-artifacts-builder`, `webapp-testing`, `mcp-builder` | Build web artifacts, test web apps, and build MCP servers. | Yes |
| `internal-comms` | Write status reports, updates, and other internal notes. | No |
| `skill-creator` | Make, test, and package skills with evals. | Yes (Python) |

Scripts run on a node with the bot's own access, through the harness (for example Claude Code or Codex). Roost does not run them on the hub. Bots that run on the hub can read a skill but cannot run its scripts.

## Layout

```
skills/<name>/SKILL.md     The skill
skills/<name>/...          Its scripts, references, and assets
index.json                 Categories, icons, and order for the Roost catalog
NOTICE                     Attribution and the list of changed files
THIRD_PARTY_NOTICES.md     Notices for third-party software, from anthropics/skills
LICENSE                    Apache License 2.0
```

`index.json` is optional for any skill repository. Roost reads it if it is there. The categories are `coding`, `design`, `data-analytics`, `documents`, `productivity`, `research`, `automation`, and `other`. Icons are [Lucide](https://lucide.dev/icons) names.

## Where the skills come from

- `weekly-review`, `inbox-triage`, `release-notes`, and `writing-skills` are written for Roost.
- The other 13 skills are Agent Skills by Anthropic, PBC, copied from [anthropics/skills](https://github.com/anthropics/skills) at commit `2c5958e`. Each keeps its `LICENSE.txt` (Apache License 2.0). The only change is in each `SKILL.md` frontmatter: a comment line and the fields `metadata.version` and `metadata.upstream`. `NOTICE` lists them.
- Anthropic's `brand-guidelines`, `academy-guide`, and `discernment-nudge` are about Anthropic itself, so they are not here. `doc-coauthoring` has no license file, so it is not here.

## Add a skill to this repository

Open a pull request with a new folder under `skills/`. A skill needs:

- A `SKILL.md` with `name` (1 to 64 characters: lowercase letters, digits, and single dashes; the same as the folder name) and `description` (what it does and when to use it, at most 1024 characters).
- `metadata.version` in the frontmatter. Raise it when the skill changes.
- At most 200 files and 10 MB, with no file over 5 MB. No links and no native programs.
- An entry in `index.json`.

Someone reads every new skill and every script before it is merged.

## License

Apache License 2.0. See `LICENSE` and `NOTICE`.
