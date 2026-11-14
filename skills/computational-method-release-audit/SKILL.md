---
name: computational-method-release-audit
description: >-
  Audits a computational method paper and its code-data release as one
  evidence system. Use when submitting or revising a method, benchmark, software note,
  or tool paper, or when reviewers may question versioning, benchmark truth,
  comparators, scalability, biological interpretation, metadata, or archived
  outputs. The skill produces release blockers, evidence maps, and minimum
  reproducibility repairs.
license: CC-BY-NC-SA-4.0
---

# Computational method release audit

## Purpose

A computational method is not ready when the manuscript reads well and the
benchmark numbers are strong. The manuscript, code, data, parameters, rendered
figures, benchmark truth sets, and archived outputs form one evidence system.
This skill audits whether the method release supports the stated claim at the
stated scale, for the stated biological or computational domain, under a clean
reproduction path.

The audit separates three questions:

1. What exact capability does the manuscript claim?
2. Which code, data, and parameter set produces the evidence?
3. Can a new user obtain the same decision-relevant output from the release?

## When to use

- A method paper is being prepared for journal or conference submission.
- A tool release claims accuracy, sensitivity, specificity, runtime, scalability,
  or biological discovery.
- Reviewers are likely to ask for versioned software, archived data, fair
  comparators, negative controls, or event-level validation.
- A benchmark mixes structural screening, coordinate recovery, classification,
  retrieval, and runtime measurements.
- A large census or database analysis must support both aggregate prevalence and
  taxon-specific interpretation.

## Inputs

Collect the following packet before scoring readiness.

| Input | Minimum requirement |
|---|---|
| Claim register | Headline claim, scope, domain, and excluded claims |
| Manuscript | Final prose, figures, captions, tables, supplement, and availability statements |
| Software | Version tag, commit, license, install path, CLI, tests, changelog, and archive DOI or planned DOI |
| Data | Input checksums, metadata, access statement, output schema, and archived result DOI or access route |
| Truth set | Source, construction rule, version, labels, coordinate conventions, and known limitations |
| Benchmarks | Pairing rule, held-out design, comparator versions, thresholds, metrics, denominators, hardware |
| Interpretability layer | Taxonomy, phenotype, sample, function, or domain mapping used by biological claims |
| Rendered package | Final PDF or HTML, figures, source data, and supplementary tables |

If an input is unavailable, mark the dependent audit item blocked rather than
assuming success.

## Procedure

### Step 1: Freeze the claim register

List every claim that must be supported before release. Separate the claim
type because each has a different evidence standard:

| Claim type | Required evidence |
|---|---|
| Accuracy or agreement | Paired truth labels, error metric, confidence or replicate design, denominator |
| Sensitivity and specificity | Case and control definitions, threshold rule, event-level or coordinate-level truth |
| Runtime | Same operation, input set, hardware, threads, amortization rule, and comparator version |
| Scalability | Measured scale points, memory, index size, query latency, and bottleneck |
| Biological prevalence | Sampling frame, cluster independence, taxonomy mapping, uncertainty |
| Retrieval or classification | Held-out family or query design, source-present control, calibrated threshold |
| Physical assay | Enzyme or protocol evidence, not only in silico simulation |

Rewrite any claim that combines incompatible evidence types. For example, do
not use a source-present rearrangement test to support de novo family
assignment, and do not use aggregate structural prevalence to identify a named
taxon without a mapping table.

### Step 2: Audit the software release

Check the repository as a release artifact, not as a working directory.

1. Confirm the exact tag or commit named in the manuscript exists remotely.
2. Confirm license, installation instructions, CLI help, minimal input, expected
   output, and changelog are public or included in the agreed package.
3. Run tests from a clean checkout.
4. Record compiler or runtime versions, parameters, seeds, threads, container
   image, and hardware class.
5. Confirm deterministic paths do not depend on local absolute paths, mutable
   database URLs, or unpinned reference data.
6. Confirm the release DOI resolves to the reviewed tag.

Mark release blocked if the manuscript names a version that cannot be checked
out, built, and exercised from the documented entry point.

### Step 3: Audit truth and labels

For each truth set, record:

1. provenance and version;
2. inclusion and exclusion rules;
3. coordinate system and orientation convention;
4. minimum event size, breakpoint tolerance, and missing-label policy;
5. whether truth is continuous, categorical, simulated, or independently
   validated;
6. whether the truth method itself has fragmentation, contiguity, or repeat
   limitations.

Preserve the scope of the truth method. A pairwise alignment signal can support
agreement or inversion-presence screening. It does not automatically prove
coordinate-level recovery, complete event recall, biological mechanism, or
functional consequence.

### Step 4: Audit benchmark design

Use one row per benchmark. The benchmark name is insufficient without the
sampling rule and denominator.

| Audit item | Requirement |
|---|---|
| Sampling frame | Population, version, quality filter, random seed, and exclusion rule |
| Pairing rule | All pairs, representative pairs, matched pairs, or weighted census |
| Denominator | Reported, tested, complete-metric, high-identity, threshold-passing, or timing-eligible units |
| Split design | Training, validation, held-out, source-present, longitudinal, and external sets |
| Comparators | Exact versions, inputs, preprocessing, parameters, and comparable output space |
| Metrics | Unit, direction, calibration, uncertainty, and tie handling |
| Negative control | Near-clonal, mutation-only, fragment-only, or biologically expected stable case |
| Runtime scale | Digestion, indexing, query, memory, end-to-end, per-pair, and wall-clock distinctions |

Reject comparisons that pool:

- assembly fragments with complete genomes;
- predicted classes with exact families;
- source-present retrieval with held-out generalization;
- coordinate recovery with orientation-presence screening;
- indexed and non-indexed modes;
- different reference spaces or event definitions.

### Step 5: Audit aggregate and subgroup results

For each census, cohort, or database-scale result, verify:

1. the numerator and denominator are explicit;
2. cluster or species independence is handled appropriately;
3. highly represented taxa are not allowed to dominate an unweighted claim;
4. every biological group name maps to a stable identifier;
5. anonymous cluster IDs used internally are translated for reader-facing claims;
6. confidence or uncertainty is reported for estimates intended to generalize;
7. ANI, quality, completeness, contamination, GC, assembly contiguity, and
   functional stratification are represented where they can alter interpretation.

If the full-scale analysis is structural but a biological interpretation is
taxon-specific, add the minimum interpretability table rather than restating
the aggregate result.

### Step 6: Audit metric completeness and estimator scope

Large-census releases often have two different denominators: the catalogue
denominator and the finite-metric denominator. Do not let a polished summary
hide this distinction. For every reported prevalence, correlation, accuracy,
or runtime estimate, record:

1. catalogue units planned or emitted;
2. units with a usable primary metric;
3. units with complete primary and covariate metrics;
4. units retained by thresholds;
5. units included in timing or other secondary analyses;
6. the reason each excluded unit is missing, such as no shared landmarks, an
   unalignable pair, a failed digest, missing ANI, or absent metadata.

Then separate estimators that answer different questions:

| Estimator | Appropriate interpretation |
|---|---|
| Pair-level prevalence | Prevalence among the emitted or metric-complete pair population |
| Cluster-level prevalence | Median or mean behavior of clusters after a stated size rule |
| Cluster bootstrap | Sensitivity to resampling clusters with unequal pair counts |
| Leave-one-cluster-out | Sensitivity to the largest absolute contributor |
| Quality-stratified estimate | Robustness after assembly-quality filters |
| ANI-stratified estimate | Structural prevalence within a sequence-divergence band |

A bootstrap interval is not a confidence interval for a different estimator.
If resampling large clusters gives 31% while the pair-weighted estimate is 28%,
report both as distinct quantities, not as inconsistent estimates of the same
target. Name the sampling unit, replacement rule, seed, and whether the
resampling target is pair prevalence, cluster prevalence, or another statistic.

Do not describe a catalogue as complete when the numerator is drawn only from
metric-complete units. Use wording such as "62,872,901 emitted pairs; 62,872,897
metric-complete pairs" rather than silently reducing the denominator. Add a
small exclusion ledger with unit identifiers and exclusion reasons whenever the
excluded count is nonzero.

### Step 7: Audit event-level and biological validation

Separate each layer:

1. **Metric agreement**: does the tool score approach the reference score?
2. **Presence screening**: does it flag whether a class of event exists?
3. **Coordinate recovery**: does it recover breakpoint or interval boundaries?
4. **Orientation recovery**: does it recover direction consistently?
5. **Mechanism or phenotype**: is there independent biological evidence?

For event-level claims, report true positive, false positive, false negative,
precision, recall, F1, coordinate tolerance, and false discovery by event size.
For biological claims, name the closed genome, longitudinal cohort, known
rearrangement system, or curated functional mapping that carries the result.

A controlled simulation may prove mechanism sensitivity. It does not by itself
prove real-sample prevalence. A large observational census may prove prevalence.
It does not by itself prove causality or assay performance.

### Step 8: Audit data and code availability

Confirm that the availability statement names exact objects:

| Object | Required identifier |
|---|---|
| Software | Version tag, commit, license, repository, archive DOI |
| Method paper source | Repository, commit, or archive snapshot |
| Raw inputs | Archive, accession, controlled-access route, or vendor statement |
| Metadata | Schema, identifiers, sample mapping, provenance |
| Reference databases | Version, checksum, license, and access route |
| Summary results | Source table, schema, and archive DOI |
| Full pair or event tables | Archive DOI, size, compression, query path, or formal access statement |
| Figure source data | Exact plotted values and units |

A promise to deposit before publication may satisfy a submission workflow only
if the venue explicitly permits it and the manuscript states the release
condition. Otherwise it is a release blocker.

### Step 9: Audit the rendered package

Open the final PDF, HTML, or submission preview. Check:

- figure panels and captions match;
- runtime and memory units match prose, figure, table, and methods;
- benchmark names and denominators are identical everywhere;
- supplementary tables are ordered by first mention;
- repository, commit, tag, and DOI strings match the availability statements;
- no local path, job ID, scratch name, rerun narrative, or unresolved version
  number appears in manuscript prose.

### Step 10: Produce readiness verdict

Classify every audit item as:

| Status | Meaning |
|---|---|
| PASS | Current evidence and release path satisfy the claim scope |
| BLOCKER | The claim or release cannot be trusted until repaired |
| REVISION STRENGTH | Supports robustness or reviewer response, not initial-release blocking |
| OUT OF SCOPE | Belongs in another paper, tool, or companion method |

Then output:

1. overall verdict: `RELEASE READY` or `RELEASE BLOCKED`;
2. claim-by-claim evidence map;
3. blockers with exact missing artifact and minimum repair;
4. strengths that should lead the narrative;
5. claims to narrow or split;
6. companion-paper candidates;
7. clean-checkout command log or reason it was not run.

## Readiness gates

| Gate | Mandatory condition |
|---|---|
| CM01 | Every headline claim names its evidence table and scope |
| CM02 | Software tag, tests, install path, CLI, and archive DOI or explicit venue-approved plan are present |
| CM03 | Truth-set version, coordinate convention, and label limitations are recorded |
| CM04 | Benchmark denominators and split designs are unambiguous |
| CM05 | Comparators use the same task and comparable output space |
| CM06 | Aggregate claims distinguish structural prevalence from biological interpretation |
| CM07 | Reader-facing biological groups resolve to stable identifiers and metadata |
| CM08 | Event-level, presence-level, coordinate-level, and runtime claims are separated |
| CM09 | Data and code availability identifiers resolve to the reviewed release |
| CM10 | The rendered package matches the final source tables and prose |
| CM11 | Catalogue, metric-complete, threshold-passing, and timing denominators are separated |
| CM12 | Sampling unit, estimator, replacement rule, seed, and uncertainty target are stated for every bootstrap or sensitivity result |

## Failure protocol

If any mandatory gate fails:

1. Do not declare the method or paper release ready.
2. Label the package `DRAFT - RELEASE BLOCKED`.
3. State the failed gate, missing artifact, and affected claim.
4. Give the minimum repair path.
5. Move out-of-scope material to a companion tool or future revision rather than
   diluting the central method claim.

## Common failure modes

- A passing local test does not prove the public checkout works.
- A strong source-present benchmark does not prove held-out family retrieval.
- A dense aggregate census does not identify a taxon without a mapping table.
- A fast per-query runtime is not an end-to-end batch benchmark.
- A structural correlation is not coordinate-level event recovery.
- A software commit hash is not a durable release identifier.
- A promise of future data deposit is not a resolving DOI.
- A complete catalogue does not imply a complete finite-metric denominator.
- A cluster bootstrap interval does not validate a different pair-weighted
  estimate.
- A quality-stratified mode count does not establish prevalence unless the
  prevalence denominator and numerator are also reported.

See: references/census-metric-incidents.md for deidentified incidents and the
minimum gates derived from them.
