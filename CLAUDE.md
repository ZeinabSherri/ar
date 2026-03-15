# Claude Instructions

## Project Overview
React + TypeScript product explorer with bilingual English/Arabic (LTR/RTL) support.

**Stack:** React, TypeScript, TanStack Query, i18next, CSS Modules, Vitest

## Commands
```bash
npm run dev       # Start dev server
npm run build     # Production build
npm test          # Run tests
```

## After Every Task

After completing any task, update this file under the **Task Log** section below:
- What was done
- Any decisions or trade-offs made
- Files changed

---

## Task Log

<!-- Add entries here after each task. Format:
### YYYY-MM-DD — <short description>
- What changed
- Why / decision made
- Files affected
-->

### 2026-03-15 — Complete caching strategy in useProducts hooks

- Added `GC_TIME` constant (10 minutes) alongside existing `STALE_TIME` (5 minutes)
- Added `gcTime: GC_TIME` to `useProducts` and `useProductById` query calls
- **Decision:** `gcTime` must always exceed `staleTime` — otherwise TanStack Query can garbage-collect cached data while it's still within the fresh window, forcing an unnecessary refetch when the user navigates back
- `useCategories` intentionally left without `gcTime` since its `staleTime: Infinity` means data never expires anyway
- **Files changed:** `src/features/products/hooks/useProducts.ts`

