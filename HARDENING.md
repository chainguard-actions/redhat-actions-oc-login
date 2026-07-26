<!-- markdownlint-disable -->

# Hardening Report: redhat-actions--oc-login/v2.0.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **redhat-actions--oc-login/v2.0.1** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Multiple workflow files reference GitHub Actions using mutable version tags instead of full 40-character commit SHA hashes, making them vulnerable to supply-chain attacks if the tag is moved.

ci-checks.yml: actions/checkout@v7 (×4), redhat-actions/common/bundle-verifier@v2, redhat-actions/common/action-io-generator@v2
example.yml: actions/checkout@v7
link_check.yml: actions/checkout@v7, lycheeverse/lychee-action@v2
multiplatform.yml: actions/checkout@v7, redhat-actions/openshift-tools-installer@v2

Locations:

- `.github/workflows/ci-checks.yml:37`
- `.github/workflows/ci-checks.yml:44`
- `.github/workflows/ci-checks.yml:52`
- `.github/workflows/ci-checks.yml:59`
- `.github/workflows/ci-checks.yml:63`
- `.github/workflows/ci-checks.yml:75`
- `.github/workflows/example.yml:18`
- `.github/workflows/link_check.yml:18`
- `.github/workflows/link_check.yml:20`
- `.github/workflows/multiplatform.yml:28`
- `.github/workflows/multiplatform.yml:33`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all mutable action tag references to full commit SHAs across four workflow files:

- .github/workflows/ci-checks.yml: actions/checkout@v7 (×4) → @3d3c42e5aac5ba805825da76410c181273ba90b1 # v7; redhat-actions/common/bundle-verifier@v2 and redhat-actions/common/action-io-generator@v2 → @ad38cc90ef0aa8ba71be3efaec1ef60fdf7853b3 # v2
- .github/workflows/example.yml: actions/checkout@v7 → @3d3c42e5aac5ba805825da76410c181273ba90b1 # v7
- .github/workflows/link_check.yml: actions/checkout@v7 → @3d3c42e5aac5ba805825da76410c181273ba90b1 # v7; lycheeverse/lychee-action@v2 → @e7477775783ea5526144ba13e8db5eec57747ce8 # v2
- .github/workflows/multiplatform.yml: actions/checkout@v7 → @3d3c42e5aac5ba805825da76410c181273ba90b1 # v7; redhat-actions/openshift-tools-installer@v2 → @ebd96c3fc72fc10a62663eac5e1421192152e6aa # v2

All SHAs were resolved via lookup_action_sha. Original tags preserved as inline comments.

