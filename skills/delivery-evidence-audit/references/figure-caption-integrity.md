# Figure, caption, and table integrity

## Panel gate

Check the rendered output at final page width, not only the source image.

1. Confirm that the file is generated from the current source tables.
2. Confirm that every caption letter A, B, C, and so on exists once in the image.
3. Confirm that every image panel appears in the caption.
4. Confirm that no embedded historical figure number remains.
5. Confirm that text remains legible after document scaling.
6. Confirm that colours, units, axes, n values, and panel titles are current.
7. Confirm that legend keys and panel order match the caption.
8. Confirm that PDF and raster exports contain the same panels.

A source-file checksum proves identity, not semantic agreement with the caption.

## Atomic revision rule

A panel split or merge is complete only when all of the following change together:

1. plotting code;
2. source table;
3. rendered PNG and PDF;
4. figure number and filename;
5. figure manifest or checksum record;
6. caption panel letters;
7. Results prose;
8. Methods if the analysis family changes;
9. linked supplementary tables;
10. all references to obsolete numbers.

Do not deliver a split figure with a combined table, or a new panel letter with
an old Results reference.

## Supplementary numbering

1. Order supplementary items by first narrative mention, not by edit history.
2. Renumber all dependent references in one operation.
3. Reject an order in which an unrelated earlier section interrupts a continuing evidence block.
4. Verify that each cited item exists once and that no obsolete number remains.
5. Keep source paths and internal run logs out of narrative prose unless required as reproducible Methods.

## Stale-output gate

Before release:

1. Remove or archive superseded figures and tables.
2. Mark historical outputs clearly if they must remain for audit.
3. Ensure that the current manifest does not point to obsolete assets.
4. Ensure that the document embeds the current, not cached, figure.
