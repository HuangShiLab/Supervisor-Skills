# Census metric completeness incidents

## Table of contents

1. CRM-001 catalogue and finite-metric denominators
2. CRM-002 estimator-target confusion
3. CRM-003 dominance hidden by aggregate prevalence
4. CRM-004 CI failed because the container lost image PATH
5. CRM-005 supplementary drift after prose strengthening
6. Derived release gates

These deidentified incidents came from one large microbial-census release. They
are retained as reusable release gates because each failure survived earlier
checks and was found only when prose, source tables, and catalogue QC were
audited together.

## Incident CRM-001: catalogue and finite-metric denominators

The release report stated that every structural pair had a finite metric. The
canonical pair table contained four rows with no shared landmarks, no finite
structural metric, and no usable orientation metric. The catalogue count was
correct, but the prevalence denominator was silently four units smaller than
the catalogue count.

**Expected state.** The catalogue count and prevalence denominator either
matched exactly or the exclusion rule and identifiers were reported.

**Actual state.** The prose used the catalogue count and an implied prevalence
denominator, while source rows had `NA` metrics for four pairs.

**Repair.** Preserve all emitted rows in the catalogue. Create an exclusion
ledger with both genome identifiers, shared-tag count, missing columns, and
exclusion reason. State the catalogue denominator and metric-complete
denominator separately in Results, Methods, QC, and the abstract.

**Reusable gate.** For every prevalence, correlation, or accuracy estimate,
the prose denominator must equal the row count in the cited finite-metric
table after documented exclusions.

## Incident CRM-002: estimator-target confusion

A cluster bootstrap produced an interval above the pair-weighted prevalence.
The calculation was correct, but the two numbers answered different questions.
The first asked what happens when species clusters are sampled with replacement;
the second asked what fraction of emitted pairs carry the event. Treating the
bootstrap interval as a confidence interval for the pair-weighted estimate would
have created a false inconsistency.

**Expected state.** Each uncertainty estimate states its sampling unit,
replacement rule, target statistic, seed, and interpretation.

**Actual state.** The number was valid, but the initial prose could have made
the estimator target look interchangeable with pair-level prevalence.

**Repair.** Report the pair-weighted estimate and Wilson interval as the primary
population estimate. Report cluster resampling and leave-one-largest-cluster-out
as sensitivity analyses. Name the largest cluster and the changed estimate.

**Reusable gate.** No bootstrap or sensitivity result may be called a
confidence interval unless its sampling design targets the same statistic as
the headline estimate.

## Incident CRM-003: dominance hidden by aggregate prevalence

An aggregate census was driven by a small number of very large clusters. A high
overall prevalence did not imply that typical species clusters had high
prevalence. Conversely, removing one dominant taxon could materially change the
pair-weighted estimate.

**Expected state.** Aggregate prevalence included a dominance or cluster-size
sensitivity analysis.

**Actual state.** The first release reported only the aggregate estimate and a
range across large clusters.

**Repair.** Add cluster-level bootstrap, leave-one-largest-cluster-out, and a
table of the largest absolute contributors. Separate pair-weighted prevalence
from cluster-level interpretation.

**Reusable gate.** Any census claiming taxon-specific behavior must report both
absolute contribution and prevalence, with a stated minimum cluster or pair
threshold.

## Incident CRM-004: CI failed because the container lost image PATH

The local build and all tests passed. Continuous integration failed because the
selected container image exposed the Rust toolchain at
`/usr/local/cargo/bin`, while the runtime PATH omitted that directory. A second
version choice was required because a dependency had adopted an edition feature
unsupported by the initially pinned toolchain.

**Expected state.** The tagged commit passes the same locked build and test
commands in the release environment.

**Actual state.** The tag initially pointed to a commit whose CI failed although
local tests passed.

**Repair.** Pin the container image, set `CARGO_HOME` and `PATH` explicitly,
use a toolchain version compatible with all locked dependencies, verify locally
in the same image, move the pre-release tag to the repaired commit, and require
a successful CI run before the release verdict.

**Reusable gate.** A version tag may be cited as reviewed only after CI success
on that exact commit.

## Incident CRM-005: supplementary drift after prose strengthening

New census analyses were added to the manuscript, but the submission-directory
copies initially retained the old supplementary set. Later revisions also left a
temporary editor lock file beside a submission DOCX.

**Expected state.** Every Supplementary Table cited in the prose exists in both
the canonical supplementary directory and the outgoing submission package.

**Actual state.** The canonical tables were updated, but package copies and
cleanup required a final audit.

**Repair.** Copy each new table into the submission directory, compare checksums
or bytes, regenerate rendered DOCX files from current Markdown, remove editor
lock files, and rerun path, reference, and rendered-page checks.

**Reusable gate.** Before delivery, every cited supplementary table must exist
in the outgoing package and the package must contain no editor lock or
temporary render artifact.

## Derived release gates

| Gate | Binary question | Evidence |
|---|---|---|
| CRM-G1 | Does every finite-metric denominator equal the cited evidence row count? | Source table, exclusion ledger, prose |
| CRM-G2 | Does every excluded unit have identifiers and an exclusion reason? | Exclusion ledger |
| CRM-G3 | Does every bootstrap result name its sampling unit, target statistic, replacement rule, and seed? | Methods and output metadata |
| CRM-G4 | Are pair-level prevalence and cluster sensitivity labelled as different estimators? | Results and Methods |
| CRM-G5 | Do absolute contribution and prevalence both support every taxon-specific claim? | Taxonomy and prevalence table |
| CRM-G6 | Does CI pass on the exact cited tag and commit? | CI log and remote ref |
| CRM-G7 | Does the outgoing package contain every cited supplementary table and no temporary artifacts? | Package manifest and directory listing |

Answer every gate `yes` or `no`. A single `no` blocks the release until the
corresponding incident repair is complete.
