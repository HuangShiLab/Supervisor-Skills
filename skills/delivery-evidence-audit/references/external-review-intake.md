# External review intake

## Comment ledger

For each reviewer comment, record:

1. comment ID;
2. author and timestamp;
3. exact request or question;
4. anchor text, section, figure, or table;
5. classification: substantive claim, scope restriction, presentation, process removal, or question;
6. disposition: resolved, revised, deferred, blocked, or rejected;
7. artifact changed;
8. check that proves resolution.

Do not paraphrase a reviewer into a narrower request. Preserve the original
wording in the ledger.

## Tracked-change reconstruction

For documents with tracked changes:

1. Parse insertions and deletions separately.
2. Reconstruct the accepted text by retaining insertions and excluding deletions.
3. Preserve the deleted text in a separate field or file for audit.
4. Separate reviewer-intended substance from formatting or process-note removal.
5. Do not edit modular source files from a visually inspected final DOCX alone.

## Disposition protocol

Classify every request as one of the following:

1. `resolve in prose`: answer in Results or Discussion and cite current evidence.
2. `resolve in Methods`: add a criterion, statistic, workflow, or access statement.
3. `resolve in figure or table`: change the artifact and every dependent reference.
4. `defer`: create a task with owner, scope, and date.
5. `reject`: state the scientific reason and evidence boundary.

Completion requires a disposition for every ID. If a comment asks "how many" or
"by what criterion", the answer must include the number or criterion, not a
qualitative assurance.
