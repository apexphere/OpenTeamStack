# OpenTeamStack

Installable agent team skills for Claude Code. Spawn coordinated multi-agent teams with a single `/team-*` command.

## Install

```bash
git clone https://github.com/apexphere/OpenTeamStack.git
cd OpenTeamStack
./setup
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

Add a new skill directory at the project root:

```
team-your-team/
  SKILL.md
```

Then add the skill name to the `for` loop in `setup` and re-run `./setup`.

## Project Structure

```
OpenTeamStack/
├── setup                    # Symlink skills into Claude Code
├── team-dev-and-qa/
│   └── SKILL.md             # Dev + QA team skill
└── README.md
```

## License

MIT
