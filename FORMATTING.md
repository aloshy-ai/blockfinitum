# Code Formatting Guidelines

This project uses ESLint and Prettier to enforce consistent code formatting across all packages and applications.

## Automatic Formatting

The project is set up with the following automation:

1. **Pre-commit Hooks**: Files are automatically formatted when you commit them
2. **Turbo Pipeline**: Run `bun format` to format all files in the monorepo
3. **Workspace-specific**: Each package/app has its own format script

### Pre-commit Hooks

The project uses Husky and lint-staged to automatically format code before committing:

- **When**: Every time you run `git commit`
- **What**: Only the files you're committing (staged files)
- **How**: Runs ESLint fix and Prettier on the appropriate file types

If the hooks aren't running correctly, try these troubleshooting steps:

```bash
# Ensure husky is installed correctly
bun run prepare

# Make sure the pre-commit hook is executable
chmod +x .husky/pre-commit

# Test lint-staged manually
npx lint-staged --verbose

# Tell Git to use the .husky directory for hooks
git config core.hooksPath .husky
```

You can temporarily bypass pre-commit hooks with:

```bash
git commit --no-verify -m "Your commit message"
```

## Manual Formatting

You can manually format files using the following commands:

```bash
# Format all files in the monorepo
bun format

# Format only using Prettier
bun format:prettier

# Format only using ESLint
bun format:eslint

# Format files in a specific workspace
cd apps/web
bun format
```

## ESLint Configuration

The ESLint configuration is shared across the monorepo through the `@repo/eslint-config` package. The configuration includes:

- TypeScript support
- React/Next.js rules
- Integration with Prettier
- Turbo-specific rules

## Adding New Rules

To add or modify ESLint rules:

1. Edit the appropriate configuration file in `packages/eslint-config`:

   - `base.js`: Base rules for all projects
   - `next.js`: Next.js specific rules
   - `react-internal.js`: React component library rules

2. Run `bun format` to apply the changes across the monorepo

## VSCode Integration

For the best development experience, install the ESLint and Prettier extensions for VSCode and add the following to your workspace settings:

```json
{
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "eslint.validate": [
    "javascript",
    "javascriptreact",
    "typescript",
    "typescriptreact"
  ]
}
```

## Cursor IDE Integration

Cursor IDE is based on VSCode and supports the same settings and extensions. This project already includes a `.cursor/settings.json` file with the correct configuration.

When you open the project in Cursor IDE, it will automatically use these settings:

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": "explicit"
  },
  "eslint.validate": [
    "javascript",
    "javascriptreact",
    "typescript",
    "typescriptreact"
  ]
}
```

To use these settings:

1. Install the ESLint and Prettier extensions for Cursor
2. Cursor will automatically use the project's `.cursor/settings.json` configuration
3. Formatting will be applied on save and when you commit your changes

You can install the Cursor extensions directly from the VS Code Marketplace, as Cursor is compatible with VS Code extensions.
