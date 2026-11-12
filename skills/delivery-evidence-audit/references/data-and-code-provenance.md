# Data and code provenance

## Inputs

For each input, record:

1. source database, accession, vendor, or internal collection;
2. file count, format, and sample or feature selection rule;
3. checksum manifest or immutable identifier;
4. date of retrieval or version;
5. access class: public, controlled access, institutional archive, or planned deposit;
6. mapping between filenames and biological samples.

For instrument data, also record:

1. acquisition instrument class or vendor format;
2. acquisition software where known;
3. conversion tool and version;
4. conversion date;
5. feature identifiers retained or lost;
6. any mapping needed to restore original names.

If conversion reduces compound, gene, genome, or sample names to generic labels,
state that limitation and the maximum achievable resolution. Do not present
precursor classes, bins, or generic transitions as individually named features.

## Processing

Record the complete execution state:

1. software commit, release, container, or binary hash;
2. parameters and reference database versions;
3. random seeds and number of resamples;
4. hardware or runtime environment when timing is reported;
5. inclusion and exclusion filters;
6. output table, checksum, and generation script.

Separate measured runtime from projected runtime. State whether timing includes
alignment, database construction, I/O, parallel overhead, and post-processing.

## Availability statement

Use one of four concrete states:

1. `public`: repository, archive, accession, and version.
2. `controlled access`: application route and access conditions.
3. `internal`: archive location, checksum manifest, and owner.
4. `planned deposit`: repository, scope, and trigger, such as submission or acceptance.

Do not use "available on request" as the sole statement for data required to
reproduce a primary result.

## Release gate

Before delivery:

1. Run checks from a clean checkout or fresh working directory.
2. Verify that no required file depends on an undocumented private path.
3. Verify that every large output has a checksum or deposit plan.
4. Verify that the reported source files match the embedded artifact.
5. Verify that no credential or participant identifier appears in public outputs.
