# TypeScript Engineering Standard

## 1. Scope
Applies to all TypeScript codebases (React frontends, Node.js services, tooling scripts) owned by MicroHack teams.

## 2. Language & Tooling
- Target **TypeScript 5.x** with `strict` mode enabled. Disallow `any` except in typed utility wrappers reviewed by the Architecture Council.
- Use `pnpm` or `npm` workspaces with a single `package.json` + `tsconfig.json` per package. Hoist shared configs in `/config` where helpful.
- Enforce linting via `eslint` + `@typescript-eslint` preset; adopt `prettier` for formatting consistency.

## 3. Project Structure
```
src/
  components/
  features/
  services/
  hooks/
  lib/
  types/
public/
tests/
```
- Co-locate unit tests next to implementation (`*.test.ts[x]`).
- Maintain `types/` for shared interfaces and API contracts to avoid circular imports.

## 4. Coding Conventions
- Prefer functional, stateless components. Use hooks for shared logic; avoid class components unless required.
- Keep components small (<200 lines). Split UI and data-fetch responsibilities.
- Use `Zod` or `io-ts` for runtime validation of external data; treat APIs as untrusted.
- Provide exhaustive switch statements; add `never` guards to catch unhandled cases.

## 5. State & Data Flow
- Favor React Query or SWR for remote data caching; avoid bespoke fetch wrappers unless necessary.
- For global state, use Redux Toolkit or Zustand with typed selectors; document state shape in `specs/**/DATA_MODELS.md`.
- Keep GraphQL/REST clients typed via code generation (OpenAPI, GraphQL Code Generator) to align with Specification by Example contracts.

## 6. Testing
- Adopt **Testing Library** for UI tests emphasizing user behavior.
- Mock network boundaries with MSW (Mock Service Worker) and keep scenario coverage aligned with PRD examples.
- For logic-heavy modules, use Jest (or Vitest) with `ts-jest`/ESM support; enforce coverage thresholds (lines 80%, statements 80%, branches 70%).

## 7. Security & Performance
- Sanitize user inputs before rendering (escape HTML, guard dangerouslySetInnerHTML).
- Enable Content Security Policy (CSP) headers in deployments.
- Use code splitting (dynamic `import()`) for feature modules to keep first paint under target budgets.
- Monitor bundle size; fail CI if compressed bundle exceeds agreed threshold without waiver.

## 8. Documentation & Specs
- Keep Storybook (or equivalent) stories updated for major components; treat them as living documentation tied to Specification by Example scenarios.
- Mirror API contracts in `specs/**/contracts/` and regenerate client types whenever the backend spec changes.
- Record architectural decisions (state management choices, caching strategy) as ADRs in `specs/**/decisions/`.
- Maintain `docs/IMPLEMENTATION_LOG.md` and `docs/COMMON_ERRORS.md` for operational insights.

## 9. CI/CD Expectations
- Run `eslint`, `prettier --check`, unit tests, type checks (`tsc --noEmit`), and dependency scans in CI.
- Block merges on failing checks; require visual regression baseline updates to be reviewed by design/UX partners.

## 10. Accessibility
- Enforce WCAG 2.1 AA compliance using lint rules (`eslint-plugin-jsx-a11y`), manual testing with screen readers, and automated scans (axe-core) for key flows.
