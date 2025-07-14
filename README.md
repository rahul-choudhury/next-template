# Next.js Template

A Next.js starter template that allows you to quickly get started with a new React project. It uses the following:

- **Next.js 15** - Latest Next.js with App Router and Turbopack
- **React 19** - Latest React with TypeScript support
- **TypeScript** - Full type safety with strict configuration
- **shadcn/ui** - Beautiful, accessible components built on Radix UI
- **Tailwind CSS v4** - Latest Tailwind with CSS variables
- **Deployment Config** - Includes Dockerfile and Github Actions workflow for deployments

## Getting Started

### Using create-next-app (Recommended)

```bash
pnpm create next-app@latest --example https://github.com/rahul-choudhury/next-template
```

### Using git clone

```bash
git clone https://github.com/rahul-choudhury/next-template.git my-project
cd my-project
rm -rf .git
pnpm install
pnpm dev
```

## Deployment

This template includes GitHub Actions workflow for deployment via Coolify. To set up deployments:

1. First, install Coolify on your VPS by following the [Coolify installation guide](https://coolify.io/docs/installation)
2. Add your Coolify variables as GitHub repository secrets. Follow the [Coolify GitHub Actions documentation](https://coolify.io/docs/knowledge-base/git/github/github-actions) for complete setup instructions

## Customization

1. **Update package.json** - Change name, description, and author
2. **Configure Tailwind** - Modify design tokens in `app/globals.css`
3. **Add components** - Use shadcn/ui CLI to add more components
4. **Environment setup** - Add your environment variables as needed
