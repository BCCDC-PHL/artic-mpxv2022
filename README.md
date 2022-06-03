# primer-schemes

Primer schemes for real-time genome epidemiology

## About

The primer schemes in this repository were built using [Primal Scheme](https://primalscheme.com/) and are available for the following viruses:

- Monkeypox virus (mpxv-2022)

Within each virus directory, there are versioned sub-directories which each contain a versioned scheme for that virus.

The following files are available per scheme version:

| file extension     | about                                                                                  |
| ------------------ | -------------------------------------------------------------------------------------- |
| `.primer.bed`      | The coordinates of each primer in the scheme                                           |
| `.insert.bed`      | The coordinates of the expected amplicons that the scheme produces (excluding primers) |
| `.reference.fasta` | The sequence of the reference genome used for the scheme                               |
| `.tsv`             | Details on each primer in the scheme (name, sequence, length, GC, TM)                  |

For more information visit the [ARTIC network website](https://artic.network/).

## Notes

- There may be some additional files in the scheme directories - these are either deprecated and left for backward compatibility (e.g. `scheme.bed`), or are created by Primal Scheme [check here](https://github.com/aresti/primalscheme) for more info.
- The schemes are in BED format, which is a 0-based, half-open format. This means that reference sequence position counting starts at 0 and the chromEnd is not included in the primer sequence.

## Primer scheme file format

The `.scheme.bed` file has the following columns:

| column | name       | type         | description                                               |
| ------ | ---------- | ------------ | --------------------------------------------------------- |
| 1      | chrom      | string       | primer reference sequence                                 |
| 2      | chromStart | int          | starting position of the primer in the reference sequence |
| 3      | chomEnd    | int          | ending position of the primer in the reference sequence   |
| 4      | name       | string       | primer name                                               |
| 5      | primerPool | int          | primer pool<sup>\*</sup>                                  |
| 6      | strand     | string (+/-) | primer direction                                          |

<sup>\*</sup> column 5 in the BED spec is an int for score, whereas here we are using it to denote primerPool.