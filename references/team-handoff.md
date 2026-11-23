# Team handoff

For a new project, document verified commands and entry points in README.md. Keep AGENTS.md as the canonical placement policy for Codex. If CLAUDE.md exists, align substantive rules and link to AGENTS.md for shared policy where practical. Keep tool-specific context in its owning file.

Place the navigation map in the README for small projects. Use `docs/project-structure.md` for a larger layout and `docs/module-map.md` if ownership and entry points need a separate map. Add architecture documentation only when needed to explain boundaries or dependency direction. Verify every documented path against real files and update affected docs when ownership or placement changes.

## Example AGENTS.md

Adapt these rules to the new repository and link its actual navigation guide.

```markdown
# File placement

- Inspect applicable instructions, the module tree, and nearby files.
- Search by name, symbol, and behavior before creating or duplicating code.
- Reuse the responsible module and use its naming and import conventions.
- Keep feature files near their owner. Share code when multiple consumers need it.
- Preserve framework entry points and module boundaries.
- Verify file placement and imports before completion. Update the navigation guide when paths or ownership change.
- Explain affected callers, builds, and docs and obtain approval before major architecture changes or bulk moves.
```

## Example File Navigation Guide

This example points to existing paths in the reference scaffold. Replace the rows with real entry points and owners in the target project.

| I need to… | Start here |
| --- | --- |
| Locate the portal's routes | `apps/portal/src/app/` |
| Locate customer service features | `apps/customer-service/src/features/` |
| Change platform admin's app config | `apps/platform-admin/next.config.ts` |
| Locate shared HTTP transport | `packages/api-client/src/http/` |
| Locate shared identity integration | `packages/auth-client/src/oidc/` |
| Check workspace package discovery or task ordering | `pnpm-workspace.yaml` and `turbo.json` |

The listed route, feature, transport, and identity directories are scaffold locations in the reference. For implemented modules, include the exact entry file, implementation path, relevant tests, and owning team if known.

