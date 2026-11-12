# External review intake worksheet

Use this worksheet before editing a commented or tracked-changes document. The
goal is to preserve every source of feedback and every accepted or rejected
text state before prose is rewritten.

## OOXML intake

1. Copy the original DOCX into a versioned review archive.
2. Extract `word/comments.xml` and record `w:comment` IDs, authors, dates, and
   anchored ranges.
3. Extract `w:ins` and `w:del` runs from `word/document.xml`.
4. Reconstruct two candidate states:
   - accepted text, with insertions retained and deletions removed;
   - rejected text, with insertions removed and deletions retained.
5. Map each anchored range to section, paragraph, sentence, figure, table, or
   source-data file.
6. Split a long comment into one row for each independent request.

## Comment ledger

| ID | Author | Location | Exact request | Classification | Disposition | Verification |
|---|---|---|---|---|---|---|
| C01 |  |  |  |  |  |  |
| C02 |  |  |  |  |  |  |
| C03 |  |  |  |  |  |  |

Use these classification values:

- `claim`: the requested change alters a factual or statistical claim.
- `scope`: the requested change narrows, broadens, or redirects the project.
- `presentation`: the requested change affects wording, layout, readability, or
  ordering without changing meaning.
- `evidence`: the request requires a new or clearer source table, statistic,
  metadata record, or provenance item.
- `process`: the request asks for removal of build history or internal detail.
- `question`: the request requires an answer but not necessarily a text change.

## Disposition rules

- Never merge comment IDs even when one edit resolves several comments.
- Never mark a comment fixed without naming the final artifact.
- Never reject a comment without a reason tied to frame, evidence, or venue
  scope.
- Never leave a question open while claiming final delivery.
- If one comment affects figures, tables, captions, abstract, methods, source
  data, and repository text, create one disposition row per affected artifact.

## Final reconstruction check

After edits, compare the outgoing document with:

1. the original text;
2. the accepted-text reconstruction;
3. the rejected-text reconstruction;
4. the comment ledger;
5. the current source tables and rendered figures.

Report each comment as `resolved`, `rejected`, or `deferred`. A final verdict
requires `resolved` or `rejected` for every actionable comment. Deferred items
force a `BLOCKED` verdict unless the user explicitly agrees that the deferred
item is outside the current release.
