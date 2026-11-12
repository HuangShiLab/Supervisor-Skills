# Work loop and stop conditions

## Unit loop

For every work unit, run the same sequence:

1. State the current task ID and its acceptance criterion.
2. Make the smallest persistent change that can be checked.
3. Run the relevant syntax, data, build, figure, table, or manuscript check.
4. Update the ledger status and artifact links.
5. Compare the remaining tasks with the goal.
6. Begin the next unfinished task unless a stop condition applies.

Do not wait for praise between units. Do not defer a check that can run now.
Do not mark work done because the output looks plausible.

## Stop conditions

Stop only for one of the following:

1. Every ledger task is `done` and the final delivery checklist passes.
2. A genuine fork requires the user to choose between materially different
   directions. Present all options, evidence, and consequences in one request.
3. A technical blocker persists after documented recovery attempts.
4. A required credential, dataset, approval, or external service is unavailable.
5. The user explicitly pauses the goal.

An incomplete result is not a stop reason by itself. Convert it into remaining
ledger tasks and continue.

## Blocker recovery protocol

Before reporting a blocker:

1. Reproduce the failure and capture the exact error.
2. Check whether the input path, version, permission, or seed changed.
3. Try at least one alternative implementation or runtime.
4. Try a smaller reproducible example.
5. Search repository logs, manifests, and provenance files for the last good state.
6. Record every attempted path and its result.

Report a blocker only with the failure mode, attempted repairs, affected tasks,
and the minimal external input needed to resume.

## Decision request protocol

When user input is unavoidable:

1. State the decision in one sentence.
2. List no more than three viable options unless the architecture requires more.
3. Give the evidence, cost, risk, and reversibility of each option.
4. Recommend one option unless the choice is purely authorial.
5. State which tasks remain blocked and which can continue independently.
