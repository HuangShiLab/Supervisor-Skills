# Claims, denominators, and statistical families

## Source-value gate

For each quantitative claim:

1. State the exact claim and its expected direction before checking evidence.
2. Open the current source table, not an old figure or legend.
3. Record the numerator, denominator, exclusions, units, software version, and seed.
4. Recompute the displayed statistic where feasible.
5. Compare abstract, Results, figure, caption, table, and source table.
6. Regenerate the figure if any value disagrees.

Distinguish:

- intended versus completed entries;
- paired versus unpaired observations;
- independent biological units versus technical replicates;
- failure-aware versus no-report-excluded scoring;
- tool-specific call spaces versus a common scoring space;
- primary analysis versus sensitivity or exploratory analysis.

## Statistical-family gate

Before combining associations:

1. Identify the feature family, such as metabolite classes, pathways, taxa, or phenotypes.
2. Identify the sample subset used by each family.
3. Identify the number of tests and the correction family.
4. Report total tests and significant positive and negative counts separately.
5. Keep plots and tables in separate families unless a prespecified pooled model exists.
6. State whether displayed rows are exhaustive or representative and give the selection rule.

For representative rows, specify whether they were selected by effect size,
significance, biological class, first authorship, or a prespecified index.
A representative row is not a prevalence estimate and must not be described as
"typical" unless that claim is tested.

## Contradiction protocol

When evidence disagrees with the expected direction:

1. Freeze inputs, code, parameters, and outputs.
2. Recompute the metric from the source table.
3. Attribute the mismatch to data, implementation, threshold, scope, statistics, or wording.
4. Report the mismatch explicitly.
5. Offer one of: a follow-up analysis, an algorithm or parameter change, a weaker claim, or a refutation statement.

Do not silently omit a result because it weakens the story.
