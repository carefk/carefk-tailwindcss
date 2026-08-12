# GitHub Advisory: GHSA-4668-fm2j-m2hg - GitHub Actions channel input injection in Tailwind CSS

## Vector
GitHub Actions channel input injection in Tailwind CSS in GitHub Actions workflows enables RCE.

## Affected Component
- **Package ecosystem:** actions
- **Package name:** .github/workflows/ci.yml
- **Vulnerable version range:** all versions
- **CVSS:** 9.8 (Critical)

## PoC
```yaml
name: CI
on: pull_request
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
        with:
          ref: ${{ github.event.pull_request.head.ref }}
```

## Fix
Quote the ref: `ref: '${{ github.event.pull_request.head.ref }}'`
