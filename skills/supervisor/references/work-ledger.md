# Work ledger schema

## Purpose

An external ledger replaces chat memory. It should be readable after a session
restart, a collaborator handoff, or a context reset.

## Required fields

Create one row per task with:

1. `ID`: stable short identifier, such as `T01`.
2. `Task`: one concrete action or deliverable.
3. `Depends on`: preceding task IDs or external inputs.
4. `Status`: `todo`, `doing`, `done`, or `blocked`.
5. `Acceptance criterion`: the observable condition for `done`.
6. `Artifacts`: files, tables, figures, reports, or commits produced.
7. `Notes`: decisions, owners, seeds, versions, or links needed to resume.

## Ledger discipline

1. Write the ledger before executing the first task.
2. Split tasks until each has a binary acceptance criterion.
3. Keep dependency IDs explicit; do not infer order from narrative.
4. Mark a task `done` only after its criterion passes.
5. Mark a task `blocked` only after recording attempted recovery paths.
6. Add newly discovered work as a numbered task; do not absorb it silently.
7. Preserve superseded decisions with a timestamp rather than deleting them.
8. Commit the ledger alongside the artifacts it tracks when the project is under version control.

## Session recovery order

1. Read the goal.
2. Read the ledger.
3. Confirm that every `done` task has its promised artifact.
4. Reopen any `done` task whose acceptance check now fails.
5. Select the first unfinished task that has no unresolved dependency.
6. If a decision is missing, assemble one concise decision request with candidate options and consequences.
