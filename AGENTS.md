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
│   ├── index.ts          # Main source file
│   └── index.test.ts     # Example test file
├── build/                # Build output directory (generated)
│   ├── index.js         # Bundled JavaScript
│   └── index.d.ts       # TypeScript declarations
├── esbuild/
│   └── build.mjs        # Build configuration (ESM)
├── .github/
│   └── workflows/
│       └── tests.yml    # CI/CD workflow example
├── tsconfig.json        # TypeScript config (extends @diplodoc/tsconfig)
├── tsconfig.publish.json # TypeScript config for publishing
├── vitest.config.mjs    # Vitest configuration
├── package.json         # Package configuration
└── README.md            # Package documentation
```

## Build System

The package uses **esbuild** for fast builds:

- Entry point: `src/index.ts`
- Output directory: `build/`
- Output files:
  - `build/index.js` - Bundled JavaScript (with sourcemaps)
  - `build/index.d.ts` - TypeScript declarations (generated via `tsc`)

Build process:
1. `build:js` - Bundles JavaScript using esbuild (ESM module)
2. `build:declarations` - Generates TypeScript declarations using `tsconfig.publish.json`
3. `build:clean` - Removes build directory (optional, run before build if needed)

The build script uses ESM (`build.mjs`) and outputs to `build/` directory for cleaner project structure.

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

The package uses **Vitest** for testing (recommended framework for Diplodoc platform):

- Configuration: `vitest.config.mjs`
- Test files: `src/**/*.test.ts` or `src/**/*.spec.ts`
- Coverage: Enabled via `@vitest/coverage-v8`

**Test Commands**:
- `npm test` - Run tests once
- `npm run test:watch` - Run tests in watch mode
- `npm run test:coverage` - Run tests with coverage report

**Example Test**: See `src/index.test.ts` for a basic test example.

For E2E tests, consider using Playwright (see `devops/testpack` for examples).

## Dependencies

### Runtime Dependencies

<!-- TODO: List runtime dependencies -->

### Dev Dependencies

- `@diplodoc/tsconfig` - TypeScript configuration
- `@diplodoc/lint` - Linting and formatting (added via `lint init`)
- `@vitest/coverage-v8` - Code coverage for Vitest
- `esbuild` - Fast JavaScript bundler
- `npm-run-all` - Run npm scripts in parallel
- `typescript` - TypeScript compiler
- `vitest` - Testing framework (recommended for Diplodoc platform)

## Important Notes

1. **Metapackage vs Standalone**: This package can be used both as part of the metapackage (workspace mode) and as a standalone npm package. All scripts must work in both contexts.

2. **Linting**: Linting infrastructure is managed by `@diplodoc/lint`. Run `npx @diplodoc/lint update` to sync configurations.

3. **Build Output**: The build outputs files to the `build/` directory. Update `package.json` `files` field if adding more output files.

4. **Type Exports**: Ensure `package.json` has correct `types` field pointing to declaration files in `build/` directory.

5. **Documentation**: Update this file and `README.md` with package-specific information after initialization.

6. **package.json Maintenance**: Periodically check that `package.json` fields (description, repository URL, bugs URL, etc.) are accurate and up-to-date. Verify that dependency versions are current and compatible with the project standards.

## CI/CD

The package includes GitHub Actions workflows:

- **tests.yml**: Runs tests, type checking, linting, and build on multiple platforms
- **security.yml**: Weekly security audits via npm audit
- **release.yaml**: Publishes package to npm when a release is created

## GitHub Integration

- **Issue templates**: Bug reports and feature requests (`.github/ISSUE_TEMPLATE/`)
- **Pull request template**: Standardized PR format (`.github/pull_request_template.md`)
- **Dependabot**: Automated dependency updates (`.github/dependabot.yml`)

## Documentation Files

- **SECURITY.md**: Security policy and vulnerability reporting
- **CONTRIBUTING.md**: Contribution guidelines and development workflow
- **AGENTS.md**: This file - guide for AI coding agents

## Additional Resources

- Metapackage `.agents/` - Platform-wide agent documentation
- `@diplodoc/lint` documentation - Linting and formatting setup
- `@diplodoc/tsconfig` - TypeScript configuration reference

