# Next.js Template with shadcn/ui

## Tech Stack

- ⚡️ Next.js 15 with App Router
- 🎨 shadcn/ui components
- 📦 pnpm for package management
- 🐳 Docker configuration
- 🔄 GitHub Actions workflow (disabled by default)
- 🛠 TypeScript support
- 🎯 ESLint and Prettier configuration

## Installation

### Prerequisites

First, install pnpm globally:

```bash
npm install -g pnpm
```

And, run the following command: (substitute your project name)

```bash
npx create-next-app@latest your-project-name --example https://github.com/rahul-choudhury/next-template --use-pnpm
```

## GitHub Actions

The repository includes a GitHub Actions workflow that is disabled by default. To enable it:

1. Rename `.github/_workflows` to `.github/workflows`
2. Push the changes to your repository

The workflow includes Docker setup for building and deploying your application. To ensure the workflow works properly, set up a GitHub Actions runner on your server:

1. Follow the [official GitHub documentation](https://docs.github.com/en/actions/hosting-your-own-runners/managing-self-hosted-runners) to configure a self-hosted runner
2. Configure it as a service
3. Make sure Docker and Docker Compose are installed
