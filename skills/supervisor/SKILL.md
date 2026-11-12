---
name: supervisor
description: >-
  Coordinates a research task from an explicit goal through an external
  task ledger, uninterrupted work loops, and a binary delivery review.
  Maintains durable state across sessions, records blockers and decisions,
  updates remaining work after each unit, and prevents premature completion.
  Use when the user asks an agent to continue work until completion, resume
  an interrupted research project, manage multistep deliverables, or enforce
  a pre-delivery checklist.
license: CC-BY-NC-SA-4.0
---

# Supervisor

## Overview

A long research deliverable fails more often from lost state than from lack of effort. This skill converts an explicit goal into an external ledger, keeps work moving through reviewable units, and blocks delivery until the goal and checklist pass. It complements writing and review skills by governing execution across sessions.

## When to use this skill

- The user asks the agent to continue until a manuscript, analysis, benchmark, or release is complete.
- Work resumes after an interruption and prior decisions live only in chat memory.
- A task has multiple dependent units, external blockers, or recurring reviewer feedback.
- A previous delivery was premature, incomplete, or failed after later review.
- A user wants every remaining task to have an owner, status, and acceptance criterion.

## When NOT to use this skill

- The user asks a single isolated question with no follow-on deliverable.
- The immediate need is prose quality; route to `paper-polish` or `pre-submission-reviewer`.
- The user wants to frame a new idea; route to `idea-evaluator`.
- A strategic decision requires user input before any further execution.

## Core procedure

### Step 1: Freeze the goal and completion rule

1. Write the final deliverable in one sentence.
2. Define completion by a pass or fail condition, not by effort.
3. Name the artifacts that must exist and the checks that must pass.
4. Identify constraints that must not change without user approval.

A goal such as "improve the paper" is not executable. Convert it to an
outcome such as "all reviewer comments have dispositions, all primary
figures match current sources, and all release checks pass."

### Step 2: Create an external ledger

Before execution, create a ledger file with task IDs, dependencies, status, and acceptance criteria. Store every draft, script, figure, and decision in the project rather than in conversation memory.

See: references/work-ledger.md for the ledger schema.

### Step 3: Work in reviewable units

For each unit:

1. Select the highest-priority unfinished task.
2. Execute the smallest complete slice that changes a persistent artifact.
3. Update the ledger immediately.
4. Run the unit-specific acceptance check.
5. Reassess remaining dependencies.
6. Continue to the next unit rather than waiting for approval unless a listed stop condition applies.

See: references/work-loop.md for stop conditions and recovery rules.

### Step 4: Run the delivery gate

A unit, milestone, or final deliverable is ready only after the binary checklist passes. Check scope, evidence, artifact integrity, reproducibility, unresolved reviewer comments, and stale outputs.

See: references/delivery-review.md for the mandatory checklist.

### Step 5: Report status cleanly

When stopping, state:

1. ledger status;
2. completed work;
3. exact stop reason;
4. unresolved blockers or decisions;
5. the first action to take when work resumes.

Do not report completion if any mandatory check is unresolved.

## Failure modes to block

- A goal exists only in conversation, so a resumed session loses the plan.
- A task is marked done although no persistent artifact or check exists.
- A blocker is asserted without trying the available recovery paths.
- A partial result is called final because it is usable.
- The ledger is updated but the deliverable is not, or the reverse.
- A reviewer request is addressed in prose but not entered in the action ledger.

## Relationship to other skills

Use `vibe-research-workflow` for AI-collaboration boundaries, `benchmark-paper-template` for evaluation structure, `pre-submission-reviewer` for final prose and presentation review, and `delivery-evidence-audit` for evidence-to-figure integrity. This skill governs the execution loop that connects those checks.

Before delivery, read `references/delivery-review.md` and compare the current output with the historical failure modes.
