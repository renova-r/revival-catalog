# Renova publication spec

Version 1.0 · 2026-11-12

This spec turns a verified archived R package into a versioned GitHub and R-universe release. The pilot was prettyR; later releases use the same evidence and layout.

## Inputs

Each release starts with the original CRAN source, the accepted repaired source, their hashes, the original license and authors, and the repair archive's check logs and frozen behavior comparisons. The repair archive remains unchanged.

The publication coordinator records the packages in the authorized batch. Preparation and verification can run in parallel; publication follows a verified release review.

## Repository layout

```text
renova-r/
  .github/profile/README.md             Organization home
  revival-catalog/README.md             Package directory and installation
  revival-catalog/docs/                 Publication spec
  renova-r.r-universe.dev/packages.json Pinned release registry
  <package>/                           One repository per R package
    DESCRIPTION
    README.md
    NEWS.md
    COPYING or LICENSE                 Original license and notices
    R/, man/, src/, ...                 Package source
```

Each package repository begins with an original-source import followed by the accepted repair and release preparation. Existing original notices and citation files are retained.

## Release preparation

1. Extract original and repaired sources with the trusted archive reader. Verify both against the accepted archive hashes.
2. Assign a Renova version by converting CRAN's hyphen separator to a dot and appending `.9001`, for example `2.2-3` → `2.2.3.9001`. Increment the last component for subsequent Renova releases. Use the immutable tag `renova-<version>`.
3. Preserve the original author, maintainer, license and citation metadata. Add `Compatibility updates by Renova.` to the end of `Description` and directly after the README's purpose sentence. Project leadership belongs on the organization home.
4. Keep the README short: purpose, Renova attribution, the actual repair, installation, and original authors/license. NEWS records the final diff, including metadata-only changes. A stale optional Date removal is described as a metadata change.
5. Add the applicable license text and retain existing notices. Remove a stale source MD5 file. Exclude repository-only documentation from the R build when appropriate.
6. Review the complete delta from the accepted repair. Publication preparation changes versioning, attribution, licensing files and release documentation; any further code repair returns to the repair workflow.

## Release verification

Package execution uses the pinned container runner and the shared concurrency limit. Build, check, install, examples, tests and behavior capture run inside containers.

- Build the exact versioned source into a source tarball and record its SHA-256.
- Run `R CMD check --as-cran` and installation in the declared target environment. Record actual flags, R version, platform, dependency setup and any omitted manual or vignette checks.
- Require zero ERRORs and WARNINGs. Read every NOTE and include a short remark for each remaining finding.
- Capture the existing frozen cases using the trusted runner. Compare with both the accepted repaired target and the archived historical baseline, using the original seeds, cases and tolerances.
- Require all comparable cases to match. Record the number of cases and concrete results, including packages that have no dedicated test directory.
- Bind the release review to the source commit and tarball hash. Verify that the committed packaged files match the checked source; excluded README-only changes are recorded separately.

R-generated packaging metadata is reviewed explicitly. For example, rebuilding a cached R data file may update its serialization writer version; the serialized object payload must still match, and the exact difference is recorded.

A failed check or comparison leaves the candidate held with its diagnostics. Existing evidence, thresholds and baseline inputs stay fixed.

## Public release

Create a public package repository under `renova-r`, push the reviewed source and immutable tag, and create a GitHub Release with:

| Asset | Contents |
| --- | --- |
| `<package>_<version>.tar.gz` | The locally built and checked source package |
| `validation.json` | Version, source commit, tarball hash, environment, check counts, frozen-case results and NOTE remarks |
| `R-CMD-check.log` | The check log with local private paths removed |

The release description states the actual change and validation results in a few lines. Public evidence contains no credentials, host paths or private operational records.

Verify uploaded asset names, sizes and hashes through the GitHub API. On an interrupted write, inspect the remote tag or release before retrying. Published tags and assets remain immutable; corrections receive a new version.

## R-universe deployment

Give the installed R-universe GitHub app access to the new public package repository, then update the registry:

```json
[
  {
    "package": "prettyR",
    "url": "https://github.com/renova-r/prettyR",
    "branch": "renova-2.2.3.9001"
  }
]
```

The registry pins a release tag. R-universe builds its own artifacts from that source; its tarball hash can differ from the local GitHub asset because it adds generated documentation and metadata.

After updating the registry, use the universe sidebar's **Check for package updates** button to start a sync. Record the resulting workflow IDs; an already queued sync or build is followed through instead of triggered again.

Record each platform's reported check result and the deployment result. A green workflow alone is insufficient to establish that the public installation endpoint works. Verify:

1. The package page displays the intended Renova version and source repository.
2. The repository's `src/contrib/PACKAGES` index lists that version.
3. A source-package download succeeds and matches the hash in that index.
4. Platform binaries and check results are reported for the platforms actually built.

First deployment can briefly return a cached 404 while a new universe is registered. Retry ordinary public requests after cache refresh; record GitHub-published and R-universe-available as separate states.

Add the package to the catalog after its GitHub release exists, and mark its R-universe availability once these endpoint checks succeed.

## Installation

```r
install.packages("prettyR", repos = c(
  Renova = "https://renova-r.r-universe.dev",
  CRAN = "https://cloud.r-project.org"
))
```

For an exact archived Renova version, install its GitHub release tag with `remotes::install_github("renova-r/prettyR@renova-2.2.3.9001")`.

## Completion record

The release ledger records the CRAN source version and archive date, original and repaired source hashes, Renova commit and tag, local release hash, checks and NOTE remarks, frozen-case comparison, GitHub release URL, registry commit, R-universe build URL and endpoint verification time.

The workflow ends with a published catalog entry and working installation endpoint for the authorized batch. CRAN submission and author correspondence are separate project actions.
