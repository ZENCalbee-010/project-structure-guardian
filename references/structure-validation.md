# Structure validation

## Review after changes

- Review added, renamed, and modified files from the diff and working tree. Trace a representative feature from its route or public entry point to its module and tests.
- Check ownership, naming, filename case, dependencies, imports and exports, shared code consumers, and justification for new top-level or sibling folders.
- Follow the navigation guide as a new contributor. Check links, paths, and documented commands against source and configuration.
- Run relevant existing checks when the change warrants them. A scaffold may support path checks before it supports a build.

## Audit

Compare the actual file tree, imports, framework conventions, and applicable instructions. Review misplaced files, duplicate implementations, ambiguous folders, inconsistent names, overlapping module responsibilities, hard-to-find entry points, and stale docs. Confirm suspected duplicates by comparing behavior and callers. Treat intentional framework conventions, placeholders, and documented exceptions accordingly.

For each finding, record the current path and competing or expected location where applicable, the evidence, the practical effect, and a safe remediation. Identify uncertainties where the intended owner is unclear. Use this format:

| Path | Evidence and impact | Proposed change |
| --- | --- | --- |
| `apps/portal/src/helpers/format-label.ts` | Same implementation and callers' purpose as `apps/portal/src/utils/format-label.ts`. New contributors have two plausible owners. | Agree on utility ownership, update callers, verify imports and tests, and remove the redundant file after approval. |

Keep the audit read-only. Report which source areas and documentation were inspected and mention verification limits.

