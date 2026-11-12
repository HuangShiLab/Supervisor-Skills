---
name: supervisor-review
description: >-
  Runs a binary pre-delivery review for manuscripts, figures, tables,
  benchmark packages, revised documents, repository changes, and reviewer
  responses. Use when the user asks for a final check, claims that work is
  complete, prepares a submission, or must resolve external comments. The
  skill blocks release until scope, evidence, rendered artifacts,
  reproducibility, and feedback dispositions are explicitly verified.
license: CC-BY-NC-SA-4.0
---

# Supervisor review

## Purpose

Supervisor review is a release gate, not another style review. It asks whether
the exact deliverable is complete, supported, internally consistent, and usable
by the intended reader. A claim checker, source-file hash, or local test can
pass while a rendered figure omits a captioned panel, a table disagrees with its
source, an embedded review comment remains unanswered, or a clean checkout
cannot reproduce the result. This skill therefore audits the delivered
artifacts as a system before any final claim.

The verdict is binary. If one mandatory gate fails, the deliverable is
`BLOCKED`. It must be labelled as a draft, with the failed gate IDs, a minimum
repair path, and the unresolved items.

## When to use

- The user asks whether a manuscript, figure, table, analysis, benchmark, or
  repository change is ready.
- A previous message or commit says "final", "submission-ready", "complete", or
  "fixed".
- A commented or tracked-changes document must be edited.
- A benchmark result or release package is about to be sent to a collaborator,
  reviewer, journal, conference system, or public repository.
- A prior correction must be checked across every downstream figure, table, and
  prose claim.

## Required packet

Collect, or explicitly request, the following items before issuing a final
verdict.

1. **Frame**: the locked project frame, scope statement, research question, or
   submission requirement.
2. **Artifacts**: every file the user will receive, including rendered PDF,
   DOCX, figures, tables, source data, cover letter, repository link, and
   archive DOI where applicable.
3. **Evidence**: current source tables, logs, statistical output, benchmark
   records, provenance files, and validation rules.
4. **Feedback**: every prior user correction, coauthor comment, reviewer
   comment, tracked change, and open question.
5. **Release environment**: a clean checkout or fresh copy, installation steps,
   commands, expected outputs, tests, and version identifiers.

Do not substitute a partial packet silently. If an item is missing, mark the
associated gate `BLOCKED` and identify the exact missing file or decision.

## Procedure

### Step 1: Freeze the review packet

Record the commit IDs, document versions, figure files, table files, source
data, command versions, and package contents under review. Do not permit files
to change while the verdict is being produced. If later changes arrive, rerun
the affected gates.

### Step 2: Build the feedback disposition ledger

Create one numbered row for every prior correction, comment, tracked change, or
question. For each item record:

| Field | Required content |
|---|---|
| ID | Stable identifier such as `C01` |
| Source | Reviewer, coauthor, user, automated check, or prior incident |
| Location | Page, section, figure, table, file, line, or rendered panel |
| Request | The exact actionable request, not a paraphrase that loses scope |
| Disposition | Fixed, answered, rejected with reason, or deferred with owner |
| Verification | The artifact and command that prove the disposition |

For a commented or tracked-changes OOXML document, extract
`word/comments.xml`, `w:ins`, and `w:del` rather than relying on a visual read.
Reconstruct the accepted text and deleted text separately. Preserve comment IDs
and never merge several reviewer requests into one disposition.

See: references/external-review-intake.md for the OOXML extraction and
reconstruction worksheet.

### Step 3: Map scope, claims, and evidence

For every headline claim, figure, table, and repository deliverable, identify
the frame cell or submission requirement it supports. Reject output that is
technically correct but outside the agreed scope unless it is clearly labelled
as exploratory or deferred.

Check that:

- each result names the correct sample, genome, feature, event, call, or pair
  space;
- denominators distinguish planned, available, completed, filtered, tested, and
  timing-eligible units;
- expected effect direction is stated before checking the observed result;
- contradictory evidence is visible, not relegated to an unread appendix;
- repeated or non-independent observations use the intended uncertainty model;
- comparator methods operate on the same inputs and comparable call spaces.

### Step 4: Audit rendered artifacts, not only source files

Open the delivered PDF, DOCX, HTML, notebook export, or rendered figure. Compare
what the reader sees with the prose, captions, and source tables. Source files
can pass checks while the rendered output fails.

Check that:

- captioned panels all exist and have the expected letters;
- figure and table numbers match every in-text reference;
- no obsolete title, version, date, panel number, or historical result remains;
- fonts, tick labels, legend text, and table entries survive page scaling;
- dense exploratory panels are moved to the supplement when they obscure the
  main result;
- each statistical family, cohort, and normalization is visually separated
  where pooling would mislead;
- supplementary tables are ordered by first narrative mention and consistently
  renumbered.

### Step 5: Audit writing and internal terminology

Remove process narration from manuscript prose. Rerun histories, scratch paths,
HPC job IDs, git troubleshooting, and build attempts belong in the repository or
methods log unless they are required reproducibility identifiers.

Verify that the abstract and conclusion contain only current, source-supported
claims. Ensure that the same object is not called a read, feature, gene,
cluster, contig, MAG, strain, species, pair, event, or sample inconsistently.
Every optional limitation must define a claim boundary or address evidence that
materially affects interpretation.

### Step 6: Reproduce the release path

Use a clean checkout or fresh output directory. Run the documented install,
build, test, figure, table, and archive commands. Check that:

- every required file resolves from the public or agreed release packet;
- software versions, commits, parameters, input checksums, container images,
  and output hashes are recorded;
- deterministic workflows contain no private absolute paths or unpinned mutable
  references;
- tests cover the delivered behavior, not only unrelated utility functions;
- large data, metadata, models, and outputs are deposited or governed by an
  explicit access statement;
- the claimed code and data DOIs resolve to the exact released versions.

### Step 7: Return a binary release verdict

Return one of two verdicts.

**READY** requires every mandatory gate to be `yes`, every feedback ID to have
a disposition, and every delivered artifact to have been inspected in its
final rendered or packaged form.

**BLOCKED** applies whenever a mandatory item is `no` or unknown. The report
must include:

1. verdict: `READY` or `BLOCKED`;
2. failed gate IDs and evidence pointers;
3. missing packet items;
4. unresolved comment IDs;
5. minimum repair path, ordered by release impact;
6. explicit statement that a blocked output is a draft, not a final release.

## Mandatory gates

Use the detailed binary worksheet in
`references/delivery-checklist.md`. The high-level gates are:

| Gate | Mandatory question |
|---|---|
| SR1 | Does the exact artifact match the locked frame and submission scope? |
| SR2 | Does every feedback ID have a verified disposition? |
| SR3 | Does every key claim have current, correctly denominated evidence? |
| SR4 | Do rendered figures and tables match captions, prose, and source data? |
| SR5 | Is the prose free of process leakage and unsupported claims? |
| SR6 | Does a clean checkout or fresh package reproduce the release path? |
| SR7 | Are unresolved issues disclosed rather than omitted from the delivery? |

## Failure protocol

When a gate fails:

1. Do not call the deliverable complete.
2. Label it `DRAFT - BLOCKED BY SUPERVISOR REVIEW`.
3. List the failed gate IDs first.
4. Provide the shortest repair that can make the package releasable.
5. Separate defects that block release from improvements that can follow after
   submission.
6. Ask whether the user wants repair, a scope change, or a different
   deliverable.

## Quality rules

- Every mandatory question has a binary answer.
- Every answer names an artifact, not an intention.
- Every rejected reviewer request receives a reason.
- Every number is checked in prose, table, figure, and source table.
- Every rendered artifact is opened.
- Every clean release path is executed where feasible.
- Every unresolved issue appears in the delivery message.
