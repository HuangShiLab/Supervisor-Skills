# Computational release audit workbook

## Table of contents

1. Claim register
2. Release inventory
3. Truth-set sheet
4. Benchmark sheet
5. Aggregate census sheet
6. Metric completeness and estimator-scope sheet
7. Event-level validation sheet
8. Availability sheet
9. Verdict and repair plan

## Claim register

| ID | Claim | Type | Scope | Evidence artifact | Status |
|---|---|---|---|---|---|
| CL01 |  | accuracy, sensitivity, runtime, scalability, prevalence, retrieval, assay, or biological |  |  | pass/blocker/revision/out-of-scope |
| CL02 |  |  |  |  |  |
| CL03 |  |  |  |  |  |

For each row ask:

- What exactly is measured?
- On which inputs and version?
- What is the denominator?
- What alternative explanation remains?
- Does the prose scope match the evidence scope?

## Release inventory

| Item | Version or hash | Location | License | Clean-checkout result |
|---|---|---|---|---|
| Method code |  |  |  | pass/fail |
| Analysis scripts |  |  |  | pass/fail |
| Container or environment |  |  | NA or path | pass/fail |
| Tests |  |  | NA | pass/fail |
| CLI example |  |  | NA | pass/fail |
| Archive DOI |  |  |  | resolves/fails/missing |

Record:

```bash
git checkout <tag-or-commit>
<install-command>
<test-command>
<minimal-cli-command>
```

Paste the command result or state why it was not executed.

## Truth-set sheet

| Truth set | Version | Label rule | Coordinate convention | Missing labels | Known limitation |
|---|---|---|---|---|---|

Answer:

1. Is the truth independent of the method under audit?
2. Does it support metric agreement, presence screening, coordinate recovery, or
   classification?
3. Are orientation, strand, contiguity, and minimum event size defined?
4. Are false labels distinguishable from absent labels?

## Benchmark sheet

Complete one sheet per comparison.

| Field | Entry |
|---|---|
| Benchmark ID |  |
| Claim tested |  |
| Population |  |
| Sampling rule and seed |  |
| Pairing or query rule |  |
| Split design |  |
| Comparator and version |  |
| Input normalization |  |
| Parameters |  |
| Metric and unit |  |
| Denominator |  |
| Hardware and threads |  |
| Runtime accounting |  |
| Negative control |  |
| Result |  |
| Evidence file |  |

Mark `BLOCKER` if any of the following are unclear:

- planned versus completed units;
- source-present versus held-out design;
- coordinate recovery versus presence screening;
- per-query versus batch runtime;
- different reference spaces;
- different event definitions.

## Aggregate census sheet

Use this sheet for large cohorts, databases, or all-versus-all surveys.

| Field | Entry |
|---|---|
| Database version |  |
| Sampling frame |  |
| Cluster or independence unit |  |
| Pair definition |  |
| Reported pairs |  |
| Complete-metric pairs |  |
| Threshold-passing pairs |  |
| Prevalence numerator |  |
| Prevalence denominator |  |
| Weighting rule |  |
| Top represented groups |  |
| Taxonomy mapping table |  |
| Uncertainty method |  |
| Sensitivity analysis |  |
| Evidence file |  |

Check:

1. Does the estimate generalize only to the sampled database version and
   quality filter?
2. Do highly represented taxa dominate an unweighted claim?
3. Can every named biological group be resolved to stable identifiers?
4. Does ANI, quality, GC, contiguity, or metadata stratification change the
   interpretation?

## Metric completeness and estimator-scope sheet

Use this sheet before reporting any prevalence, correlation, accuracy, or
sensitivity result derived from a large catalogue.

| Field | Entry |
|---|---|
| Catalogue denominator |  |
| Finite-metric denominator |  |
| Complete primary and covariate denominator |  |
| Threshold-passing denominator |  |
| Timing denominator |  |
| Excluded rows |  |
| Exclusion reason ledger |  |
| Prevalence numerator |  |
| Headline estimator |  |
| Sampling unit |  |
| Replacement rule |  |
| Replicates and seed |  |
| Uncertainty target |  |
| Sensitivity estimator |  |
| Dominant unit and leave-one-out estimate |  |
| Evidence file |  |

Record one row per estimate. For each row answer:

1. Does the prose denominator equal the finite-metric row count?
2. Are catalogue, metric-complete, threshold-passing, and timing counts
   distinguishable?
3. Is the bootstrap target the same statistic as the headline estimate?
4. Are pair-level prevalence and cluster-level sensitivity reported as distinct
   quantities?
5. Does the largest-unit removal result accompany the aggregate estimate?

## Event-level validation sheet

| Event class | Truth definition | Coordinate tolerance | TP | FP | FN | Precision | Recall | F1 |
|---|---|---|---:|---:|---:|---:|---:|---:|

Add rows by event size, orientation, region, genome quality, or comparator.

Answer:

1. Is a matched interval counted once or once per breakpoint?
2. Are multi-event regions resolved deterministically?
3. Are false positives separated by size, repeat content, or assembly artifact?
4. Does the paper distinguish event presence from coordinate recovery?

## Availability sheet

| Object | Identifier | Access route | Version | Resolves | License or restriction |
|---|---|---|---|---|---|
| Software |  |  |  |  |  |
| Analysis code |  |  |  |  |  |
| Reference data |  |  |  |  |  |
| Raw inputs |  |  |  |  |  |
| Metadata |  |  |  |  |  |
| Summary tables |  |  |  |  |  |
| Full result tables |  |  |  |  |  |
| Figure source data |  |  |  |  |  |

If a DOI is promised later, record:

1. the venue rule that permits delayed deposit;
2. the exact deposit trigger;
3. the responsible owner;
4. whether the current submission may proceed without it.

## Verdict and repair plan

Return this table as the final audit output.

| Gate | Status | Evidence pointer | Minimum repair |
|---|---|---|---|
| CM01 Claim register | pass/blocker |  |  |
| CM02 Software release | pass/blocker |  |  |
| CM03 Truth set | pass/blocker |  |  |
| CM04 Benchmark design | pass/blocker |  |  |
| CM05 Comparators | pass/blocker |  |  |
| CM06 Aggregate scope | pass/blocker |  |  |
| CM07 Biological mapping | pass/blocker |  |  |
| CM08 Evidence-type separation | pass/blocker |  |  |
| CM09 Availability | pass/blocker |  |  |
| CM10 Rendered package | pass/blocker |  |  |
| CM11 Metric-completeness denominators | pass/blocker |  |  |
| CM12 Estimator and uncertainty scope | pass/blocker |  |  |

Then state:

```markdown
Overall verdict: RELEASE READY or RELEASE BLOCKED

Blockers:
1. ...
2. ...

Minimum repair path:
1. ...
2. ...

Companion-paper candidates:
- ...

Narrative strengths to retain:
- ...
```
