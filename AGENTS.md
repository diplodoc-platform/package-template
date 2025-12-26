<!-- TEMPLATE SECTION - This section will be removed after running init.sh -->
<!-- ============================================================================ -->
<!-- TEMPLATE: Package Template Documentation -->
<!-- ============================================================================ -->

# AGENTS.md - Package Template

This file is part of the `@diplodoc/package-template` package. After running `./init.sh`, the template section below will be removed, and only the package-specific section will remain.

## Template Overview

The `@diplodoc/package-template` provides a starting point for creating new packages in the Diplodoc metapackage. It includes:

- TypeScript configuration extending `@diplodoc/tsconfig`
- Build setup with esbuild
- Basic package structure
- Scripts for building and type checking

## Template Usage

1. Clone the template repository
2. Run `./init.sh <package-name>` to initialize
3. The script will:
   - Replace `package-template` with your package name
   - Initialize linting via `@diplodoc/lint init`
   - Install dependencies
   - Remove template files

<!-- END TEMPLATE SECTION -->
<!-- ============================================================================ -->

# AGENTS.md

A guide for AI coding agents working on this package.

## Package Overview

<!-- TODO: Add package description after initialization -->

This package is part of the Diplodoc metapackage. It provides [describe functionality].

## Setup Commands

```bash
# Install dependencies
npm install

# Build the package
npm run build

# Type check
npm run typecheck
```

## Development Commands

```bash
# Build in watch mode (if configured)
npm run watch

# Run tests (if configured)
npm test

# Lint code
npm run lint

# Fix linting issues
npm run lint:fix
```

## Package Structure

```
package-name/
├── src/
│   └── index.ts          # Main source file
├── esbuild/
│   └── build.js         # Build configuration
├── tsconfig.json        # TypeScript config (extends @diplodoc/tsconfig)
├── package.json         # Package configuration
└── README.md            # Package documentation
```

## Build System

The package uses **esbuild** for fast builds:

- Entry point: `src/index.ts`
- Output: `index.js` (bundled, minified)
- Type declarations: `index.d.ts` (generated via `tsc`)

Build process:
1. `build:js` - Bundles and minifies JavaScript
2. `build:declarations` - Generates TypeScript declarations

## TypeScript Configuration

Extends `@diplodoc/tsconfig` with:
- Target: ES2022
- Module: ES2022
- Declaration files enabled

## Linting and Code Quality

Linting is configured via `@diplodoc/lint`:

- ESLint for JavaScript/TypeScript
- Prettier for code formatting
- Stylelint for CSS/SCSS (if applicable)
- Git hooks via Husky
- Pre-commit checks via lint-staged

Configuration files are automatically managed by `@diplodoc/lint`:
- `.eslintrc.js`
- `.prettierrc.js`
- `.stylelintrc.js` (if CSS/SCSS files exist)
- `.editorconfig`
- `.lintstagedrc.js`
- `.husky/pre-commit`

## Testing

<!-- TODO: Add testing information if tests are added -->

Currently, the package has a placeholder test script. Consider adding tests using:
- **Vitest** (recommended for new packages)
- Jest (if migrating from existing setup)
- Playwright (for E2E tests)

## Dependencies

### Runtime Dependencies

<!-- TODO: List runtime dependencies -->

### Dev Dependencies

- `@diplodoc/tsconfig` - TypeScript configuration
- `@diplodoc/lint` - Linting and formatting (added via `lint init`)
- `esbuild` - Fast JavaScript bundler
- `npm-run-all` - Run npm scripts in parallel
- `typescript` - TypeScript compiler

## Important Notes

1. **Metapackage vs Standalone**: This package can be used both as part of the metapackage (workspace mode) and as a standalone npm package. All scripts must work in both contexts.

2. **Linting**: Linting infrastructure is managed by `@diplodoc/lint`. Run `npx @diplodoc/lint update` to sync configurations.

3. **Build Output**: The build outputs `index.js` and `index.d.ts` in the package root. Update `package.json` `files` field if adding more output files.

4. **Type Exports**: Ensure `package.json` has correct `types` field pointing to declaration files.

5. **Documentation**: Update this file and `README.md` with package-specific information after initialization.

## Additional Resources

- Metapackage `.agents/` - Platform-wide agent documentation
- `@diplodoc/lint` documentation - Linting and formatting setup
- `@diplodoc/tsconfig` - TypeScript configuration reference

