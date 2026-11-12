---
name: delivery-evidence-audit
description: >-
  Audits research deliverables after evidence, figures, tables, or reviewer
  edits change. Converts reviewer comments into numbered actions, reconstructs
  tracked changes, reconciles claims with source tables, checks statistical
  families and denominators, verifies raw-data provenance, and confirms that
  rendered figures contain every captioned panel. Use when revising an
  annotated manuscript, finalizing a benchmark result, preparing a document
  or repository release, or explaining why a figure, claim, or table changed.
license: CC-BY-NC-SA-4.0
---

# Delivery Evidence Audit

## Overview

A deliverable can pass phrase and checksum checks yet still fail because a caption cites a missing panel, a table retains an old number, a merged statistical family hides the denominator, or raw-file provenance cannot be traced. This skill audits the chain from source evidence to prose, figure, table, and rendered output. It is designed for the last revision before handoff, especially after external comments or tracked changes.

## When to use this skill

- A reviewer returns a commented or tracked-changes manuscript.
- A figure, table, or Results paragraph is split, merged, renumbered, or re-rendered.
- A claim depends on completed and intended sample counts, representative rows, or tool-specific call spaces.
- A metabolomics, genomics, survey, or benchmark deliverable needs raw-data provenance.
- A document or repository is about to be released to collaborators or reviewers.

## When NOT to use this skill

- The argument structure is still being invented; use `tech-paper-template` or `benchmark-paper-template`.
- The main issue is grammar and tone; use `paper-polish`.
- A full reviewer-style draft audit is needed; use `pre-submission-reviewer` after this evidence gate.

## Core procedure

### Step 1: Convert external review into an action ledger

For a commented document, extract every comment with an ID, author, request, and anchor. Do not rely on a visual read. For tracked changes, parse insertions and deletions separately, reconstruct the accepted text, and classify each request.

See: references/external-review-intake.md.

### Step 2: Reconcile claims and source evidence

For every quantitative claim, open the current source table and record its value, denominator, units, exclusions, and version. Regenerate the figure if any displayed value differs. Treat representative display rows differently from complete tests.

See: references/claim-and-statistical-families.md.

### Step 3: Check figure, caption, and table integrity

Compare the rendered artifact, not only the source file, with every captioned panel. Re-run or remove stale outputs. Renumber all dependent references in one atomic revision.

See: references/figure-caption-integrity.md.

### Step 4: Verify provenance and availability

Record input accessions, file counts and checksums, software versions, parameters, seeds, conversion tools, and transformations that lose identifiers. Distinguish public, controlled-access, internal, and planned deposits.

See: references/data-and-code-provenance.md.

### Step 5: Return an evidence disposition

For each claim, figure, table, and reviewer request, return one of:

1. `resolved`: source evidence and rendered artifact agree.
2. `revised`: evidence supports a narrowed or corrected statement.
3. `deferred`: a new task, owner, and date exist.
4. `blocked`: the required evidence or access is unavailable.
5. `rejected`: explain why the request is scientifically inappropriate.

Do not report completion while a critical claim or reviewer request is unresolved.

## Mandatory checks

1. Does every key claim cite current evidence?
2. Do source tables, figures, captions, and abstract agree?
3. Are statistical families, sample subsets, and correction families separate?
4. Are intended and completed counts distinguished?
5. Is every captioned figure panel present in the rendered artifact?
6. Is every old figure and table reference updated?
7. Are raw inputs, conversions, parameters, versions, and checksums traceable?
8. Are all reviewer comments and tracked changes dispositioned?
9. Are process details excluded from narrative prose unless needed for Methods?
10. Are unresolved issues listed in the delivery report?

## Failure modes to block

- A checksum passes while the rendered figure lacks a captioned panel.
- A representative row is described as the complete test set.
- A merged plot combines different effect families or sample subsets.
- A table is numbered by edit history rather than narrative order.
- A conversion produces generic feature names but the text does not state the limitation.
- A reviewer asks for a criterion and receives only a result.
- An old supporting table remains after a figure is split.

Use this audit before `pre-submission-reviewer` so that presentation review does not certify stale evidence.
