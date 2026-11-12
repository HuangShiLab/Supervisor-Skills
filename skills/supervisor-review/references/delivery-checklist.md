# Binary delivery checklist

## Table of contents

1. Packet gates
2. Feedback gates
3. Scope gates
4. Evidence and statistics gates
5. Figure gates
6. Table gates
7. Manuscript and prose gates
8. Benchmark and comparison gates
9. Reproducibility and release gates
10. Delivery message gates

## Packet gates

| ID | Question | Answer |
|---|---|---|
| PK01 | Are the frame, target venue, and submission requirements frozen? | yes/no |
| PK02 | Is every artifact in the outgoing package identified by version or hash? | yes/no |
| PK03 | Is every evidence file mapped to the claim or panel it supports? | yes/no |
| PK04 | Is there a clean location from which the release path can be tested? | yes/no |
| PK05 | If any packet item is unavailable, is that gate marked blocked rather than assumed complete? | yes/no |

## Feedback gates

| ID | Question | Answer |
|---|---|---|
| FB01 | Does the ledger contain every comment, tracked change, prior correction, and open question? | yes/no |
| FB02 | Does each comment have a stable ID and exact location? | yes/no |
| FB03 | Does each actionable comment have `fixed`, `answered`, `rejected`, or `deferred`? | yes/no |
| FB04 | Does each rejection state a reason grounded in scope or evidence? | yes/no |
| FB05 | Does each verification field name the artifact or command that proves the disposition? | yes/no |

## Scope gates

| ID | Question | Answer |
|---|---|---|
| SC01 | Does the deliverable answer the locked research question? | yes/no |
| SC02 | Are all planned analysis axes represented or explicitly deferred? | yes/no |
| SC03 | Is every dataset substitution disclosed? | yes/no |
| SC04 | Are exploratory outputs excluded from the main claim or labelled exploratory? | yes/no |
| SC05 | Are companion-method, software, benchmark, and empirical claims separated? | yes/no |

## Evidence and statistics gates

| ID | Question | Answer |
|---|---|---|
| EV01 | Does every key claim cite a current source table or validation output? | yes/no |
| EV02 | Do prose, figure, table, and source file show the same value, unit, and rounding rule? | yes/no |
| EV03 | Is the expected signal direction stated before inspection? | yes/no |
| EV04 | Are planned, available, completed, filtered, tested, and timing-eligible units distinguished? | yes/no |
| EV05 | Are repeated measures, hosts, batches, or phylogenetically related units modeled or explicitly scoped out? | yes/no |
| EV06 | Are confidence intervals, uncertainty estimates, or deterministic reproducibility statements appropriate? | yes/no |
| EV07 | Is contradictory evidence reported rather than silently omitted? | yes/no |

## Figure gates

| ID | Question | Answer |
|---|---|---|
| FG01 | Has the final rendered figure been opened and inspected? | yes/no |
| FG02 | Does every captioned panel exist with the correct letter and content? | yes/no |
| FG03 | Are titles, legends, axis labels, units, and sample sizes readable at final page width? | yes/no |
| FG04 | Do figure numbers and in-text references match the submission order? | yes/no |
| FG05 | Have obsolete panel titles, historical versions, and duplicate summaries been removed? | yes/no |
| FG06 | Do colors, encodings, and statistical families avoid misleading visual pooling? | yes/no |
| FG07 | Do source-data files reproduce the plotted values and sample sizes? | yes/no |

## Table gates

| ID | Question | Answer |
|---|---|---|
| TB01 | Has every column, row group, and footnote been inspected in the final format? | yes/no |
| TB02 | Are headers, units, spaces, and missing-value codes unambiguous? | yes/no |
| TB03 | Are table numbers and in-text references consistent? | yes/no |
| TB04 | Are supplementary tables ordered by first narrative mention and renumbered everywhere? | yes/no |
| TB05 | Do totals, subtotals, and denominators reconcile with the source table? | yes/no |
| TB06 | Are comparator, cohort, feature space, and call space identified for every summary? | yes/no |

## Manuscript and prose gates

| ID | Question | Answer |
|---|---|---|
| MS01 | Does the abstract contain only claims supported by the current packet? | yes/no |
| MS02 | Does each Results paragraph interpret evidence rather than narrate build history? | yes/no |
| MS03 | Are reruns, scratch paths, internal tickets, and troubleshooting absent from manuscript prose? | yes/no |
| MS04 | Are terminology, input mode, feature space, call space, and sample count used consistently? | yes/no |
| MS05 | Do limitations define claim boundaries rather than provide unnecessary self-attack? | yes/no |
| MS06 | Are all accepted tracked changes incorporated and rejected changes documented? | yes/no |
| MS07 | Are references, figure citations, and table citations complete and in the required order? | yes/no |

## Benchmark and comparison gates

| ID | Question | Answer |
|---|---|---|
| BM01 | Do all methods receive the same immutable inputs and preprocessing? | yes/no |
| BM02 | Are parameter searches, version IDs, thresholds, and hardware settings recorded? | yes/no |
| BM03 | Are source-present, held-out, longitudinal, and cross-validation settings distinguished? | yes/no |
| BM04 | Are event-level, coordinate-level, sample-level, and set-level metrics separated? | yes/no |
| BM05 | Are negative controls and near-boundary cases represented where they test the claim? | yes/no |
| BM06 | Does the runtime comparison use the same operation, units, threads, and amortization rule? | yes/no |
| BM07 | Is sampling or taxonomic bias disclosed and addressed where it affects the estimate? | yes/no |

## Reproducibility and release gates

| ID | Question | Answer |
|---|---|---|
| RP01 | Does the clean checkout contain every required script, input pointer, fixture, and license? | yes/no |
| RP02 | Do documented commands complete without private path edits? | yes/no |
| RP03 | Are software, database, model, container, and reference versions pinned? | yes/no |
| RP04 | Are input checksums, parameters, seeds, threads, and runtime environment recorded? | yes/no |
| RP05 | Do tests cover the delivered claim, parser, renderer, statistical output, or export path? | yes/no |
| RP06 | Are raw data, metadata, large intermediates, and models deposited or access-controlled by statement? | yes/no |
| RP07 | Do code and data identifiers resolve to the exact reviewed version? | yes/no |
| RP08 | Are license, ethics, consent, provenance, and access restrictions stated where required? | yes/no |

## Delivery message gates

| ID | Question | Answer |
|---|---|---|
| DM01 | Is the verdict explicitly `READY` or `BLOCKED`? | yes/no |
| DM02 | Are failed gates listed before successful summaries? | yes/no |
| DM03 | Are unresolved feedback IDs listed in the message? | yes/no |
| DM04 | Is the minimum repair path ordered by release impact? | yes/no |
| DM05 | Does a blocked package explicitly remain a draft? | yes/no |
