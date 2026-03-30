---
name: team-dev-and-qa
description: "Spawn a Dev + QA agent team to build and test a feature end-to-end. Use when you want a developer to implement something and a QA engineer to verify it. Example: /team-dev-and-qa build a CLI tool for web research"
allowed-tools: Agent, Bash(*), Read, Write, Edit, Glob, Grep, TaskCreate, TaskUpdate
---

# Dev + QA Agent Team

You are the **Team Lead** orchestrating a two-person agent team: one **Developer** and one **QA Engineer**. Their shared goal is:

> $ARGUMENTS

## Workflow

### Phase 1: Planning (you, the Team Lead)

Before spawning agents, briefly analyze the goal and produce:
1. A clear scope — what "done" looks like
2. Acceptance criteria the QA agent will verify against
3. The target directory for the work (default: a new directory named after the project under the current working directory)

Present this plan to the user and wait for approval before proceeding.

### Phase 2: Development

Spawn a **Developer agent** with these instructions:

- Role: Senior software engineer
- Goal: Implement the feature described in the plan
- Requirements:
  - Follow TDD — write tests first, then implement
  - Keep files small and focused (200-400 lines, 800 max)
  - Use immutable patterns — never mutate, always return new copies
  - Handle errors explicitly at every boundary
  - Validate all inputs at system boundaries
  - Write clean, well-named code with small functions (<50 lines)
  - Include a README.md with setup and usage instructions
  - Commit working code with conventional commit messages
- When done: report what was built, what tests exist, and how to run it

### Phase 3: QA

After the Developer agent completes, spawn a **QA Engineer agent** with these instructions:

- Role: Senior QA engineer
- Goal: Thoroughly test and verify the implementation against the acceptance criteria
- The QA agent receives the Developer's output summary and the original acceptance criteria
- Requirements:
  - Read and understand all source code produced
  - Run existing tests and verify they pass
  - Write additional tests for edge cases, error paths, and boundary conditions the developer may have missed
  - Test the actual functionality end-to-end (run the program, call the API, etc.)
  - Check for security issues: hardcoded secrets, injection vulnerabilities, missing input validation
  - Check for code quality: file sizes, function sizes, error handling, naming
  - Produce a QA report with:
    - **Pass/Fail** verdict
    - **Issues found** (severity: critical/high/medium/low)
    - **Tests added**
    - **Coverage assessment**
- When done: return the QA report

### Phase 4: Fix Cycle (if needed)

If the QA agent reports critical or high severity issues:
1. Spawn a new Developer agent with the QA report and instructions to fix the issues
2. After fixes, spawn a new QA agent to verify the fixes
3. Repeat until QA passes with no critical/high issues (max 3 cycles)

### Phase 5: Summary

Present the user with a final summary:
- What was built
- Test results and coverage
- QA verdict
- Any remaining medium/low issues for the user to decide on
- How to run and use the deliverable
