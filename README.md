## How to start

```bash
# Clone this repo to new folder
git clone git@github.com:diplodoc-platform/package-template.git new-package
cd new-package

# Init repo with new package name
./init.sh new-package
```

The `init.sh` script will:
- Replace `package-template` with your package name in `package.json` and `README.md`
- Initialize linting with `@diplodoc/lint init` (adds lint scripts, configs, and Git hooks)
- Install dependencies
- Update git remote URL
- Remove template files (`init.sh`, `README-template.md`)

After initialization, you'll have a fully configured package with:
- TypeScript configuration extending `@diplodoc/tsconfig`
- ESLint, Prettier, and Stylelint configured via `@diplodoc/lint` (added automatically)
- Git hooks via Husky (configured automatically)
- Build scripts using esbuild
- Type declarations generation

## Next Steps

1. Update `README.md` with your package description
2. Update `package.json` description and repository URL
3. Add your code to `src/index.ts`
4. Configure exports in `package.json` if needed
5. Add tests (consider using Vitest as recommended in `.agents/style-and-testing.md`)

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

## Development Workflow

1. Make changes in `src/`
2. Run `npm run build` to build
3. Run `npm run lint` to check code quality
4. Run `npm run typecheck` to verify types
5. Commit changes (pre-commit hook will run linting automatically)
