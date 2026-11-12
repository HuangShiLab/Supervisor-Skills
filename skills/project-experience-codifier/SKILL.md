---
name: project-experience-codifier
description: >-
  Converts recurring project corrections, reviewer findings, failed releases,
  benchmark traps, and process lessons into reusable agent skills, incident
  records, and binary acceptance gates. Use when one repository keeps making
  the same class of mistake, a postmortem must become an enforceable workflow,
  or project knowledge should transfer beyond a single document or collaboration.
license: CC-BY-NC-SA-4.0
---

# Project experience codifier

## Purpose

Project experience becomes useful only when it changes the next decision. A
postmortem that says "communicate earlier", "be more careful", or "improve
quality" does not survive the next deadline. This skill converts observed
failures and successful recoveries into named failure modes, evidence-backed
rules, binary gates, and skill-ready documentation. It preserves the mechanism
of the lesson without exposing private names, confidential data, or unrelated
project history.

## When to use

- The same correction appears in more than one review or delivery.
- A user finds an issue after the work was called complete.
- An automated checker passed although a rendered artifact or release path
  failed.
- A benchmark design choice caused ambiguity in denominators, comparators, or
  claimed performance.
- A repository contains valuable incident knowledge only in chat history,
  commit messages, review notes, or an individual's memory.
- A project-specific checklist should become a transferable skill.

## When not to use

- The event is unique and cannot improve a future decision.
- The lesson is already represented by an existing skill.
- The proposed rule depends on private identities, confidential data, or a
  one-off infrastructure path.
- The evidence supports only a hypothesis about what failed.

## Procedure

### Step 1: Assemble experience sources

Read the minimum evidence needed to reconstruct the lesson:

1. user corrections and follow-up questions;
2. coauthor and reviewer comments;
3. tracked-change dispositions;
4. failed and passing check output;
5. rendered artifacts, not only source files;
6. commit history, release notes, and issue threads;
7. benchmark parameters and validation records;
8. repository checks from a clean checkout.

Do not use memory as the sole source. Each incident must have at least one
artifact pointer, even if the pointer is an internal review message that will
later be deidentified.

### Step 2: Write one incident record per failure

Use the template in `references/experience-record.md`. For each incident,
record the observable trigger, expected state, actual state, missed signal,
repair, and preventive rule. Keep records factual and specific. Avoid blame.

A useful incident record contains:

| Field | Requirement |
|---|---|
| ID | Stable, project-local identifier |
| Stage | Planning, data, analysis, figure, table, prose, review, release, maintenance |
| Trigger | Observable event that exposed the issue |
| Expected | What the locked frame or claim required |
| Actual | What the delivered artifact contained |
| Missed signal | Which existing check, file, or conversation should have caught it |
| Repair | Minimum change that restored correctness |
| Rule | Binary condition future work can enforce |
| Deidentification | Private names, paths, and data removed or generalized |

### Step 3: Separate root causes from symptoms

Group incidents by mechanism rather than surface wording. Common mechanisms
include:

- **Scope drift**: the output answers a different question or adds an unplanned
  axis.
- **Denominator ambiguity**: planned, available, completed, filtered, tested,
  and timing-eligible units are conflated.
- **Source/render mismatch**: source data support one state while the rendered
  artifact shows another.
- **Comment loss**: a visual read misses embedded comments or tracked changes.
- **Silent contradiction**: negative or weak evidence exists but is omitted.
- **Unreproducible release**: a clean checkout cannot locate or run the
  release path.
- **Overgeneralized claim**: evidence supports a narrow setting but prose
  claims a broader setting.
- **Process leakage**: workflow history appears as manuscript substance.
- **Stale downstream artifact**: one correction does not propagate to all
  figures, tables, captions, and summaries.

If two incidents share the same root cause and repair rule, merge them into one
failure mode with both evidence pointers.

### Step 4: Convert each rule into a binary gate

For each mechanism, write a question with a verifiable answer. Avoid "adequate",
"careful", "clear", and "reasonable" unless accompanied by a measurable
condition. Prefer:

- "Does the rendered caption cite a panel absent from the rendered image?"
- "Does the source table value equal the prose value after the stated rounding?"
- "Does every reviewer comment ID have a fixed, answered, or rejected
  disposition?"
- "Does a clean checkout run the documented release command without private
  path edits?"
- "Do the comparator and primary method use the same input set and call space?"

Each gate needs:

1. stable ID;
2. mandatory yes/no question;
3. evidence artifact;
4. verification command or inspection procedure;
5. failure path;
6. owner or repair role.

### Step 5: Decide whether the lesson deserves a skill

Promote a lesson to a skill only when all conditions hold:

1. It generalizes beyond one project or artifact.
2. It changes a concrete decision, not merely reporting tone.
3. It has occurred more than once or would plausibly cause a severe release
   failure.
4. It can be checked without confidential material.
5. It does not duplicate an existing skill.
6. It has a binary failure state and a repair path.

If the lesson is domain-specific but transferable, place it in a specialized
audit skill. If it applies before every delivery, place it in a release-gate
skill. If it guides project management, keep it as a reusable checklist rather
than forcing it into a manuscript skill.

### Step 6: Draft the skill architecture

Create the smallest architecture that passes the promotion test:

| Component | Content |
|---|---|
| Name | Kebab-case action or object name |
| Description | Capability, trigger conditions, and Use when clause |
| Inputs | Minimum packet required for a trustworthy result |
| Procedure | Ordered steps with decisions and evidence checks |
| Gates | Binary checks with IDs |
| Output | Verdict, findings, evidence pointers, and repair path |
| References | Deep worksheets, templates, or incident taxonomy |
| Failure protocol | What blocks delivery and how to recover |

Keep the main `SKILL.md` executable and under the repository line limit. Move
long examples, record templates, and domain-specific worksheets to
`references/*.md`.

### Step 7: Deidentify and attribute

Remove private collaborator names, patient or sample identifiers, internal
paths, credentials, unpublished results, and details that do not change the
transferable rule. Preserve the mechanism and severity. If a lesson comes from
an existing methodology, repository, handbook, or collaborator, state the
attribution required by the target license.

### Step 8: Validate the candidate skill

Run the proposed skill against the original incident and one unrelated
scenario.

The original incident test asks:

- would the new gate have blocked the failed delivery?
- does it point to the missing evidence?
- does it prescribe a minimum repair?

The transfer test asks:

- can another project answer the gate without private context?
- is the failure mode still meaningful?
- is the output binary rather than advisory?

Then run repository linters, link checks, and any skill-format validation
before proposing the contribution.

## Output format

Return four sections.

### Experience matrix

| ID | Root cause | Evidence pointer | Preventive gate | Existing coverage |
|---|---|---|---|---|

### Candidate skills

| Name | Trigger | Core gate | Promotion rationale | Overlap decision |
|---|---|---|---|---|

### Skill blueprint

For each promoted skill, provide the proposed directory, description, inputs,
procedure, gates, output, references, and failure protocol.

### Implementation plan

List files to add or edit, checklist IDs, lint commands, validation scenarios,
attribution requirements, and any unresolved confidentiality question.

## Quality rules

- Every retained lesson has at least one evidence pointer.
- Every named failure mode has a binary gate.
- Every proposed skill has a non-overlap decision.
- Every private identifier is removed or explicitly gated.
- Every checklist item is answerable from artifacts, not optimism.
- Every output distinguishes mandatory release gates from optional improvements.
