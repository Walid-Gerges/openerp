# Branching Strategy

This repository follows a **version-based branching strategy** aligned with Odoo's official release model.

## Branch Types

### 1. Version Branches (Stable Series)

Each major (and some minor) Odoo release is maintained in its own long-lived branch:

| Branch | Odoo / OpenERP Release |
|--------|------------------------|
| `5.0`  | OpenERP 5.0            |
| `6.0`  | OpenERP 6.0            |
| `6.1`  | OpenERP 6.1            |
| `7.0`  | OpenERP 7.0            |
| `8.0`  | Odoo 8.0               |
| `9.0`  | Odoo 9.0               |
| `10.0` | Odoo 10.0              |
| `11.0` | Odoo 11.0              |
| `12.0` | Odoo 12.0              |
| `13.0` | Odoo 13.0              |
| `14.0` | Odoo 14.0              |
| `15.0` | Odoo 15.0              |
| `16.0` | Odoo 16.0              |
| `17.0` | Odoo 17.0              |
| `18.0` | Odoo 18.0              |
| `19.0` | Odoo 19.0              |

Each version branch contains all code specific to that release and receives only bug fixes and security patches (no new features) after its initial release. Pull requests targeting a stable version must be submitted against the corresponding version branch.

### 2. `master` Branch

The `master` branch represents the **next upcoming release** under active development. New features, API changes, and significant refactors are merged here first. Once a new version is released, a new version branch is cut from `master` (e.g., `20.0`).

### 3. Feature / Topic Branches

Short-lived branches used for developing individual features, fixes, or tasks. They follow naming conventions such as:

- `copilot/<description>` – branches created by the Copilot coding agent
- `<username>/<description>` or `<type>/<description>` – contributor branches

These branches are merged into the appropriate version branch or `master` via a pull request and are deleted after the merge.

## Workflow Summary

```
master  ──────────────────────────────────▶  (next release)
   │
   └─── 19.0  ──────────────────────────▶  (bug fixes / security patches only)
   └─── 18.0  ──────────────────────────▶  (bug fixes / security patches only)
   └─── ...
   └─── 5.0   ──────────────────────────▶  (legacy, minimal maintenance)
```

1. **New features** → open a PR against `master`.
2. **Bug fixes for a specific version** → open a PR against the relevant version branch (e.g., `19.0`). Fixes may be forward-ported to newer branches manually or via automation.
3. **Security patches** → backported to all actively supported version branches.

## Choosing the Right Target Branch

When submitting a pull request, select the target branch as follows:

- Bug fix for an existing stable release → target the matching version branch (e.g., `18.0`).
- New feature or breaking change → target `master`.
- Patch that applies to multiple versions → submit against the oldest affected version; maintainers will forward-port as needed.

For more details, see [CONTRIBUTING.md](CONTRIBUTING.md).
