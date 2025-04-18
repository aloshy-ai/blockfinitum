# Blockfinitum

This is a Turborepo monorepo using bun as the package manager.

## Prerequisites

- [Node.js](https://nodejs.org/en/) (>=18)
- [bun](https://bun.sh/) (1.2.8 or compatible)

```sh
# Install bun
curl -fsSL https://bun.sh/install | bash
```

## Getting Started

Clone the repository and install dependencies:

```sh
git clone https://github.com/aloshy-ai/blockfinitum.git
cd blockfinitum
bun install
```

## What's inside?

This Turborepo includes the following packages/apps:

### Apps and Packages

- `apps/blog`: a [Next.js](https://nextjs.org/) app
- `apps/web`: another [Next.js](https://nextjs.org/) app
- `packages/ui`: a shared React component library (@repo/ui)
- `packages/eslint-config`: shared ESLint configs (@repo/eslint-config)
- `packages/typescript-config`: shared TypeScript configs (@repo/typescript-config)

Each package/app is 100% [TypeScript](https://www.typescriptlang.org/).

### Utilities

This Turborepo has some additional tools already setup for you:

- [TypeScript](https://www.typescriptlang.org/) for static type checking
- [ESLint](https://eslint.org/) for code linting
- [Prettier](https://prettier.io) for code formatting
- [Husky](https://typicode.github.io/husky/) for Git hooks

### Commands

From the root directory, you can run:

```sh
# Build all apps and packages
bun build

# Develop all apps and packages
bun dev

# Run linting
bun lint

# Format code
bun format
```

You can also use Turbo to run commands for specific packages or apps:

```sh
# Run dev for a specific app
bun dev --filter=web

# Build a specific package
bun build --filter=@repo/ui
```

### Remote Caching

> [!TIP]
> Vercel Remote Cache is free for all plans. Get started today at [vercel.com](https://vercel.com/signup?/signup?utm_source=remote-cache-sdk&utm_campaign=free_remote_cache).

Turborepo can use a technique known as [Remote Caching](https://turbo.build/docs/core-concepts/remote-caching) to share cache artifacts across machines, enabling you to share build caches with your team and CI/CD pipelines.

By default, Turborepo will cache locally. To enable Remote Caching you will need an account with Vercel. If you don't have an account you can [create one](https://vercel.com/signup?utm_source=turborepo-examples), then enter the following commands:

```
cd my-turborepo
npx turbo login
```

This will authenticate the Turborepo CLI with your [Vercel account](https://vercel.com/docs/concepts/personal-accounts/overview).

Next, you can link your Turborepo to your Remote Cache by running the following command from the root of your Turborepo:

```
npx turbo link
```

## Useful Links

Learn more about the power of Turborepo:

- [Tasks](https://turbo.build/docs/core-concepts/monorepos/running-tasks)
- [Caching](https://turbo.build/docs/core-concepts/caching)
- [Remote Caching](https://turbo.build/docs/core-concepts/remote-caching)
- [Filtering](https://turbo.build/docs/core-concepts/monorepos/filtering)
- [Configuration Options](https://turbo.build/docs/reference/configuration)
- [CLI Usage](https://turbo.build/docs/reference/command-line-reference)
