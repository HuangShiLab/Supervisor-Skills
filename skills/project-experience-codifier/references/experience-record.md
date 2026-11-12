# Experience record template

## Table of contents

1. Incident record
2. Root-cause analysis
3. Gate conversion
4. Skill promotion review
5. Deidentification checklist

## Incident record

```markdown
### Incident EXP-001

- Date:
- Stage:
- Artifact:
- Frame or claim affected:

#### Trigger

State the observable event that exposed the failure.

#### Expected state

State what the locked scope, source table, figure caption, reviewer request, or
release gate required.

#### Actual state

State what the delivered artifact contained. Include exact values, panel
letters, file names, denominators, or commands where useful.

#### Missed signal

Identify the existing check, conversation, source file, or rendered artifact
that should have exposed the problem.

#### Repair

State the minimum change that restored correctness.

#### Preventive rule

State a binary condition for future work.

#### Evidence pointers

List source files, commits, messages, review IDs, logs, or rendered artifacts.

#### Deidentification

Record whether private names, sample IDs, paths, credentials, or unpublished
details were removed.
```

## Root-cause analysis

Answer these questions after the factual record is complete.

1. Which lifecycle stage failed?
2. Was the frame missing, ignored, or changed?
3. Was evidence absent, stale, unreadable, or misread?
4. Did the source and rendered artifact disagree?
5. Was feedback lost, merged, or answered without verification?
6. Did an automated check inspect the wrong layer?
7. Was the release path executed from a clean checkout?
8. Did a narrow result become a broad claim?

Write one root-cause phrase. Do not list every observable defect as a root
cause.

## Gate conversion

For each root cause, complete this table.

| Field | Entry |
|---|---|
| Gate ID | Stable short identifier |
| Binary question | Yes/no question answerable from artifacts |
| Evidence | File, command, rendered artifact, or ledger |
| Verification | Exact inspection or command |
| Failure state | What makes the answer no |
| Repair path | Minimum owner and action |
| Applies to | Manuscript, figure, table, code, benchmark, release, or response |

Bad gate:

> Improve figure checking.

Good gate:

> Render the final figure and confirm that every panel letter cited in the
> caption appears exactly once in the rendered image.

## Skill promotion review

| Question | Answer | Requirement |
|---|---|---|
| Does the lesson generalize? | yes/no | At least two projects or a severe transferable failure mode |
| Does it change a decision? | yes/no | It blocks, redirects, or requires evidence |
| Can it be checked without confidential data? | yes/no | The gate can run on a public or authorized packet |
| Does an existing skill cover it? | yes/no | If yes, extend the existing skill instead |
| Does it have a repair path? | yes/no | The failed state has a minimum fix |
| Is the failure binary? | yes/no | The answer is yes/no, not "probably" |

Promote only when every row is `yes`.

## Deidentification checklist

- Remove collaborator names unless attribution is required.
- Remove patient, sample, animal, or participant identifiers.
- Remove private hostnames, absolute paths, tokens, and credentials.
- Remove unpublished values that are not needed to explain the mechanism.
- Replace project-specific placeholders with generic roles.
- Preserve severity, denominator ambiguity, artifact layer, and repair rule.
- Record the license and source of any borrowed methodology.
