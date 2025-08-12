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

## Project Structure

This template adopts a **feature-based project structure** within the Next.js App Router, prioritizing scalability and maintainability. It leverages Next.js's powerful colocation capabilities and route groups to keep related code together, promoting a clear separation of concerns.

### Key Principles:

-   **Feature-Based Colocation**: Application logic, components, and utilities specific to a particular feature or route are colocated directly within their respective route segments in the `app/` directory. This makes features self-contained and easier to manage.
-   **Route Groups**: Used to organize routes by logical sections (e.g., `(marketing)`, `(dashboard)`) without affecting the URL path. This allows for distinct layouts and contexts for different parts of the application.
-   **Shared Code**: Truly generic and reusable components (e.g., UI elements from `shadcn/ui`), hooks, and utility functions are placed in top-level directories like `components/ui/` and `lib/`.

### Directory Layout:

```
.
├── app/
│   ├── (marketing)/             # Route group for marketing pages
│   │   ├── layout.tsx           # Marketing-specific layout
│   │   └── about/
│   │       ├── page.tsx         # About page
│   │       └── about-hero.tsx   # Colocated component for 'about'
│   ├── (dashboard)/             # Route group for dashboard features
│   │   ├── layout.tsx           # Dashboard-specific layout
│   │   ├── loading.tsx          # Dashboard-specific loading UI
│   │   ├── page.tsx             # Dashboard overview page
│   │   └── settings/
│   │       ├── page.tsx         # Settings page
│   │       └── profile-form.tsx # Colocated component for settings
│   ├── layout.tsx               # Root layout
│   └── globals.css              # Global styles
├── components/
│   └── ui/                      # Shared, reusable UI components (e.g., from shadcn/ui)
│       ├── button.tsx
│       └── sonner.tsx
├── lib/                         # Shared libraries and helper functions (e.g., API client, utils)
│   ├── actions.ts
│   ├── api-client.ts
│   ├── data.ts
│   └── utils.ts
├── public/                      # Static assets
│   └── ...
└── ... (other config files like package.json, tsconfig.json)
```

This structure ensures that as your application grows, its codebase remains organized, predictable, and easy to navigate.

## Customization

1. **Update package.json** - Change name, description, and author
2. **Configure Tailwind** - Modify design tokens in `app/globals.css`
3. **Add components** - Use shadcn/ui CLI to add more components
4. **Environment setup** - Add your environment variables as needed

## Deployment

This template includes GitHub Actions workflow for deployment via Coolify. To set up deployments:

1. First, install Coolify on your VPS by following the [Coolify installation guide](https://coolify.io/docs/installation)
2. Add your Coolify variables as GitHub repository secrets. Follow the [Coolify GitHub Actions documentation](https://coolify.io/docs/knowledge-base/git/github/github-actions) for complete setup instructions
