<!-- markdownlint-disable -->

# Hardening Report: redhat-actions--oc-login/v2.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **redhat-actions--oc-login/v2.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Multiple workflow files reference GitHub Actions using mutable version tags (e.g. @v7, @v2) instead of pinned 40-character SHA commit hashes. This exposes the workflow to supply-chain attacks where a tag could be silently moved to point to malicious code.

Failing references:
- actions/checkout@v7 (used in all four workflow files)
- redhat-actions/common/bundle-verifier@v2
- redhat-actions/common/action-io-generator@v2
- lycheeverse/lychee-action@v2
- redhat-actions/openshift-tools-installer@v2

All should be pinned to full SHA digests, e.g. actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4

Locations:

- `.github/workflows/ci-checks.yml:31`
- `.github/workflows/ci-checks.yml:40`
- `.github/workflows/ci-checks.yml:44`
- `.github/workflows/ci-checks.yml:53`
- `.github/workflows/ci-checks.yml:58`
- `.github/workflows/example.yml:18`
- `.github/workflows/link_check.yml:19`
- `.github/workflows/link_check.yml:21`
- `.github/workflows/multiplatform.yml:27`
- `.github/workflows/multiplatform.yml:31`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all 10 unpinned action references across 4 workflow files to full 40-character SHA digests:
- actions/checkout@v7 → @11d5960a326750d5838078e36cf38b85af677262 # v4 (5 occurrences in ci-checks.yml x3, example.yml, link_check.yml, multiplatform.yml)
- redhat-actions/common/bundle-verifier@v2 → @ad38cc90ef0aa8ba71be3efaec1ef60fdf7853b3 # v2 (ci-checks.yml)
- redhat-actions/common/action-io-generator@v2 → @ad38cc90ef0aa8ba71be3efaec1ef60fdf7853b3 # v2 (ci-checks.yml)
- lycheeverse/lychee-action@v2 → @e7477775783ea5526144ba13e8db5eec57747ce8 # v2 (link_check.yml)
- redhat-actions/openshift-tools-installer@v2 → @ebd96c3fc72fc10a62663eac5e1421192152e6aa # v2 (multiplatform.yml)
Note: The workflows referenced actions/checkout@v7 which does not exist; pinned to the current stable v4 SHA instead.

