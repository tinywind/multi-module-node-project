# Multi-module Node project

Use Node.js 24 and pnpm. The dependency update was validated with pnpm 12.15.0.

Build the shared model before installing its file-based consumers:

```sh
pnpm install --frozen-lockfile
cd model && pnpm install --frozen-lockfile && pnpm build && cd ..
cd projectA && pnpm install --frozen-lockfile && cd ..
cd projectB && pnpm install --frozen-lockfile && cd ..
pnpm build:all
pnpm concurrently
```

Both consumers use the same compiled model and print their user information. All three TypeScript packages use version 7; the root lockfile includes patched transitive dependencies of npm-run-all.
