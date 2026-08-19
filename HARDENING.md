<!-- markdownlint-disable -->

# Hardening Report: redhat-actions--oc-login/v1.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **redhat-actions--oc-login/v1.3** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All workflow files reference external actions using mutable tag-based refs (e.g. @v1, @v4) instead of pinned 40-character commit SHAs. This exposes the workflows to supply-chain attacks if any referenced action's tag is moved to a malicious commit.

Affected references:
- ci-checks.yml: actions/checkout@v4 (×3), redhat-actions/common/bundle-verifier@v1, redhat-actions/common/action-io-generator@v1
- example-v3.yml: actions/checkout@v4, redhat-actions/openshift-tools-installer@v1
- example.yml: actions/checkout@v4
- link_check.yml: actions/checkout@v4, gaurav-nelson/github-action-markdown-link-check@v1
- multiplatform.yml: actions/checkout@v4, redhat-actions/openshift-tools-installer@v1
- security_scan.yml: actions/checkout@v4, actions/setup-node@v4, redhat-actions/openshift-tools-installer@v1, redhat-actions/crda@v1
- template.yml: redhat-actions/openshift-tools-installer@v1, redhat-actions/oc-login@v1

Locations:

- `.github/workflows/ci-checks.yml:13`
- `.github/workflows/ci-checks.yml:24`
- `.github/workflows/ci-checks.yml:30`
- `.github/workflows/ci-checks.yml:39`
- `.github/workflows/ci-checks.yml:44`
- `.github/workflows/example-v3.yml:17`
- `.github/workflows/example-v3.yml:20`
- `.github/workflows/example.yml:13`
- `.github/workflows/link_check.yml:18`
- `.github/workflows/link_check.yml:19`
- `.github/workflows/multiplatform.yml:23`
- `.github/workflows/multiplatform.yml:27`
- `.github/workflows/security_scan.yml:16`
- `.github/workflows/security_scan.yml:19`
- `.github/workflows/security_scan.yml:23`
- `.github/workflows/security_scan.yml:29`
- `.github/workflows/template.yml:15`
- `.github/workflows/template.yml:19`

### missing-permissions (severity: medium)

None of the 7 workflow files define a top-level `permissions:` block, and no individual job within any of these files defines a job-level `permissions:` block. Without explicit permissions, workflows run with the default (potentially broad) GITHUB_TOKEN permissions, violating the principle of least privilege.

Locations:

- `.github/workflows/ci-checks.yml:1`
- `.github/workflows/example-v3.yml:1`
- `.github/workflows/example.yml:1`
- `.github/workflows/link_check.yml:1`
- `.github/workflows/multiplatform.yml:1`
- `.github/workflows/security_scan.yml:1`
- `.github/workflows/template.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all 7 workflow files:

1. ci-checks.yml: Pinned actions/checkout@v4→SHA, redhat-actions/common/bundle-verifier@v1→SHA, redhat-actions/common/action-io-generator@v1→SHA. Added top-level `permissions: {}` and job-level `permissions: contents: read`.

2. example-v3.yml: Pinned actions/checkout@v4→SHA, redhat-actions/openshift-tools-installer@v1→SHA. Added top-level `permissions: {}` and job-level `permissions: contents: read`.

3. example.yml: Pinned actions/checkout@v4→SHA. Added top-level `permissions: {}` and job-level `permissions: contents: read`.

4. link_check.yml: Pinned actions/checkout@v4→SHA, gaurav-nelson/github-action-markdown-link-check@v1→SHA. Added top-level `permissions: {}` and job-level `permissions: contents: read`.

5. multiplatform.yml: Pinned actions/checkout@v4→SHA, redhat-actions/openshift-tools-installer@v1→SHA. Added top-level `permissions: {}` and job-level `permissions: contents: read`.

6. security_scan.yml: Pinned actions/checkout@v4→SHA, actions/setup-node@v4→SHA, redhat-actions/openshift-tools-installer@v1→SHA, redhat-actions/crda@v1→SHA. Added top-level `permissions: {}` and job-level `permissions: contents: read`.

7. template.yml: Pinned redhat-actions/openshift-tools-installer@v1→SHA, redhat-actions/oc-login@v1→SHA. Added top-level `permissions: {}` and job-level `permissions: contents: read`.

All original tag names preserved as inline comments (e.g., `# v4`, `# v1`) for readability.

