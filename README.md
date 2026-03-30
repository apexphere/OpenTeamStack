# OpenTeamStack

Installable agent team skills for Claude Code. Spawn coordinated multi-agent teams with a single `/team-*` command.

## Install

```bash
claude plugin install github.com/apexphere/OpenTeamStack
```

## Available Teams

### `/team-dev-and-qa`

Spawns a **Developer** and **QA Engineer** working together toward a goal.

```
/team-dev-and-qa build a CLI tool for web research on crypto trading techniques
```

**What happens:**
1. **Team Lead** analyzes the goal, defines scope and acceptance criteria, asks for your approval
2. **Developer agent** implements the feature using TDD
3. **QA agent** tests the implementation, writes additional tests, produces a report
4. **Fix cycle** — if QA finds critical/high issues, dev fixes and QA re-verifies (up to 3 rounds)
5. **Summary** — final report with verdict, test results, and usage instructions

## Creating New Teams

Add a new skill directory under `skills/`:

```
skills/
  team-your-team/
    SKILL.md
```

The `SKILL.md` frontmatter must include `name: team-your-team` and a `description` explaining when to use it. See existing teams for examples.

## Local Development

Test the plugin locally:

```bash
claude --plugin-dir ./OpenTeamStack
```

## License

MIT
