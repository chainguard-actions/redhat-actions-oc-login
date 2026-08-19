<!-- markdownlint-disable -->

# Hardening Report: redhat-actions--oc-login/v1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **redhat-actions--oc-login/v1** was hardened automatically. 14 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All uses: references in this workflow use mutable tags instead of pinned 40-character SHA commit hashes, making the workflow vulnerable to supply-chain attacks if the referenced action is compromised or the tag is moved. Unpinned references: actions/checkout@v4, redhat-actions/common/bundle-verifier@v1, redhat-actions/common/action-io-generator@v1.

Locations:

- `.github/workflows/ci-checks.yml:13`
- `.github/workflows/ci-checks.yml:23`
- `.github/workflows/ci-checks.yml:30`
- `.github/workflows/ci-checks.yml:42`
- `.github/workflows/ci-checks.yml:49`

### unpinned-uses (severity: high)

All uses: references in this workflow use mutable tags instead of pinned 40-character SHA commit hashes. Unpinned references: actions/checkout@v4, redhat-actions/openshift-tools-installer@v1.

Locations:

- `.github/workflows/example-v3.yml:20`
- `.github/workflows/example-v3.yml:23`
- `.github/workflows/example-v3.yml:33`

### unpinned-uses (severity: high)

All uses: references in this workflow use mutable tags instead of pinned 40-character SHA commit hashes. Unpinned references: actions/checkout@v4.

Locations:

- `.github/workflows/example.yml:13`
- `.github/workflows/example.yml:17`

### unpinned-uses (severity: high)

All uses: references in this workflow use mutable tags instead of pinned 40-character SHA commit hashes. Unpinned references: actions/checkout@v4, gaurav-nelson/github-action-markdown-link-check@v1.

Locations:

- `.github/workflows/link_check.yml:16`
- `.github/workflows/link_check.yml:17`

### unpinned-uses (severity: high)

All uses: references in this workflow use mutable tags instead of pinned 40-character SHA commit hashes. Unpinned references: actions/checkout@v4, redhat-actions/openshift-tools-installer@v1.

Locations:

- `.github/workflows/multiplatform.yml:24`
- `.github/workflows/multiplatform.yml:28`

### unpinned-uses (severity: high)

All uses: references in this workflow use mutable tags instead of pinned 40-character SHA commit hashes. Unpinned references: actions/checkout@v4, actions/setup-node@v4, redhat-actions/openshift-tools-installer@v1, redhat-actions/crda@v1.

Locations:

- `.github/workflows/security_scan.yml:14`
- `.github/workflows/security_scan.yml:17`
- `.github/workflows/security_scan.yml:22`
- `.github/workflows/security_scan.yml:28`

### unpinned-uses (severity: high)

All uses: references in this workflow use mutable tags instead of pinned 40-character SHA commit hashes. Unpinned references: redhat-actions/openshift-tools-installer@v1, redhat-actions/oc-login@v1.

Locations:

- `.github/workflows/template.yml:14`
- `.github/workflows/template.yml:19`

### missing-permissions (severity: medium)

This workflow has no top-level permissions: key and no job-level permissions: keys on any job. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad. Add a top-level permissions: block with the minimum required scopes.

Locations:

- `.github/workflows/ci-checks.yml:1`

### missing-permissions (severity: medium)

This workflow has no top-level permissions: key and no job-level permissions: keys on any job. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad.

Locations:

- `.github/workflows/example-v3.yml:1`

### missing-permissions (severity: medium)

This workflow has no top-level permissions: key and no job-level permissions: keys on any job. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad.

Locations:

- `.github/workflows/example.yml:1`

### missing-permissions (severity: medium)

This workflow has no top-level permissions: key and no job-level permissions: keys on any job. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad.

Locations:

- `.github/workflows/link_check.yml:1`

### missing-permissions (severity: medium)

This workflow has no top-level permissions: key and no job-level permissions: keys on any job. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad.

Locations:

- `.github/workflows/multiplatform.yml:1`

### missing-permissions (severity: medium)

This workflow has no top-level permissions: key and no job-level permissions: keys on any job. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad.

Locations:

- `.github/workflows/security_scan.yml:1`

### missing-permissions (severity: medium)

This workflow has no top-level permissions: key and no job-level permissions: keys on any job. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad.

Locations:

- `.github/workflows/template.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all 7 workflow files: (1) Pinned all action references to full 40-character SHA commit hashes with original tags preserved as comments. Actions pinned: actions/checkout@v4→34e114876b0b11c390a56381ad16ebd13914f8d5, actions/setup-node@v4→49933ea5288caeca8642d1e84afbd3f7d6820020, redhat-actions/openshift-tools-installer@v1→144527c7d98999f2652264c048c7a9bd103f8a82, redhat-actions/common@v1→a7e9fd367034e38805280ad71d9cc35e2d9f6f9d, gaurav-nelson/github-action-markdown-link-check@v1→5c5dfc0ac2e225883c0e5f03a85311ec2830d368, redhat-actions/crda@v1→6310ee94a6ac8f76b4152b7267c6cd7f1277052c, redhat-actions/oc-login@v1→5eb45e848b168b6bf6b8fe7f1561003c12e3c99d. (2) Added top-level 'permissions: contents: read' block to all 7 workflow files (ci-checks.yml, example-v3.yml, example.yml, link_check.yml, multiplatform.yml, security_scan.yml, template.yml).

