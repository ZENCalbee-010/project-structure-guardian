---
name: project-structure-guardian
description: Plan and verify repository structure for new projects, choose file placement for features and bug fixes, or audit an existing layout. Use when asked to scaffold a project, place or name files, map module ownership, prepare a file navigation guide, or check structural consistency.
---

# Project Structure Guardian

Make every file discoverable by responsibility and ownership. Respect repository instructions, framework entry points, and authorized scope.

## Inspect before editing

Read applicable `AGENTS.md`, project docs, manifests, and representative files. Use `rg --files`, `git ls-files` where available, and targeted symbol and import searches to find existing owners. Include relevant untracked source when safe and exclude dependencies, generated output, and secrets. Compare documentation with the actual tree and distinguish scaffold directories from implemented features.

Read [structure and placement](references/structure-and-placement.md) when selecting a layout, module, or filename. In existing projects prefer verified local patterns. Use the reference workspace as a starting point for compatible greenfield projects and adapt it to the stack and scale.

## New Project

Identify applications, framework entry points, domain owners, and actual code-sharing needs. Apply the reference boundaries where they fit. Create the directories needed by the requested scaffold. Add a README with verified setup, an AGENTS.md with placement rules, and navigation information. Read [team handoff](references/team-handoff.md) for examples and guidance on splitting docs as the project grows.

## Feature Development

For each proposed file, identify its responsibility and owner, search by names and implementation, and reuse or extend the existing owner where appropriate. Compare adjacent files for naming and placement. Add a folder only when it has a distinct responsibility or framework requirement. Trace each feature from its entry point to its implementation. Repeat the placement check after changes and update affected navigation docs. Confirm scope before changing architecture or moving many existing files, and explain import, build, and handoff impacts.

## Structure Audit

Run a read-only review. Follow [structure validation](references/structure-validation.md) to check placement, duplicates, naming, boundaries, discoverability, and documentation. Report findings with paths, observed evidence, impact, and a proposed fix. Request authorization before applying moves or deletions.

Use `$project-structure-guardian` with a request such as “choose locations for the ticket search feature” or “audit this repository's structure.”

