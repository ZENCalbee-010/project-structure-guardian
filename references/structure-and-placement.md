# Structure and file placement

Source workspace `links-internal-platform-frontend` at commit `3834707`. Evidence includes `pnpm-workspace.yaml`, `turbo.json`, app manifests and configs, the tracked tree, and `CLAUDE.md`.

| Observed location | Responsibility |
| --- | --- |
| Root | Workspace manifests and tool configs such as `package.json`, `pnpm-workspace.yaml`, and `turbo.json`. GitLab CI, Dockerfile, and repository-wide docs also live here. |
| `apps/<app>/src/app/` | Next.js App Router entry points. Keep framework files and route folders here and place feature implementation with its owner. |
| `apps/<app>/src/features/` | App-owned business features. For a new feature, group related implementation by responsibility when the local pattern and size justify it. |
| `apps/<app>/src/{components,contexts,hooks,services,types,i18n,utils}/` | App-level UI, providers, hooks, integrations, types, localization and utility functions respectively. Prefer feature-local ownership when only one feature uses the code and the local pattern permits it. |
| `apps/<app>/public/` | App-specific static assets. App configs such as `next.config.ts` and `tsconfig.json` sit with the consuming app. |
| `packages/ui/src/{components,feedback,forms,layouts,primitives}/` | UI intended for multiple apps, grouped by role. |
| `packages/api-client/src/{clients,http,interceptors}/` | Shared backend clients and transport. App-specific orchestration belongs to its app or feature. |
| `packages/auth-client/src/{middleware,oidc,permissions,session}/` | Shared identity integration and session/permission handling. Framework-specific activation belongs at the consuming entry point. |
| `packages/types/src/{api,auth,common}/` | Shared contracts grouped by domain or purpose. |
| `packages/i18n/src/{config,locales}/` | Shared localization configuration and translations. |
| `packages/shared/src/{constants,enums,utils,validators}/` | Cross-app, domain-neutral building blocks. |
| `packages/config/{eslint,tailwind,typescript}/` | Shared tool configuration. |
| `docs/{architecture,authentication,deployment,frontend-guidelines}/`, `scripts/` | Repository-level knowledge and workspace scripts. App-only scripts stay with the owning app when supported by local conventions. |

Several directories contain only `.gitkeep`, and package barrels are empty. The tree has no demonstrated component filename pattern, feature internals, test convention, backend, or database layout. The README is a GitLab starter. The documented central OIDC/BFF relationship describes intent. Preserve the separation of frontend, API contracts, and data ownership. In projects with a backend, find its route, service, and persistence owners from actual code. Put schemas and migrations with the database owner using its tool's conventions. Find test placement from runner configuration and neighboring tests. For a new project, choose a stack-appropriate layout and document any convention you introduce.

## Naming

Prefer the repository's existing case and suffixes. The source uses lowercase directory names and kebab-case compound app/package names such as `customer-service` and `api-client`. It has TypeScript package entry files named `index.ts` where present, and app-local `@/*` aliases for `src/*`. Keep framework-reserved names such as `page.tsx` and `layout.tsx` when applicable. Use domain terms already used by routes and modules. Check case-sensitive paths and avoid ambiguous generic names. Establish any missing convention based on the stack and adjacent code.

## Boundaries

- Route or app entry points call their feature or integration owner. Keep dependency direction consistent with the repository and use package public exports where established. Check for deep imports and cycles when crossing boundaries.
- Move code into shared ownership when real consumers need a stable common interface. Keep app-specific behavior local. Keep shared packages independent of their consuming apps.
- Search existing utility and integration directories by symbol and behavior. Use the established location and avoid parallel `utils`, `helpers`, and `common` folders with overlapping responsibilities.
- Root placement needs workspace scope or a tool discovery requirement. Give other additions the narrowest useful owner.
- The exact app names, `@links-platform/*` scope, app rule to use `utils` over `lib`, central identity convention, and Thai-first localization are specific to the source workspace. Adopt these only where appropriate. A single app can keep equivalent boundaries within its own tree.

