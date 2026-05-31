# Codebase Structure

This document provides a comprehensive overview of the project structure.

## Root Configuration Files

| File | Description |
|------|-------------|
| `package.json` | Project dependencies, scripts, and metadata |
| `tsconfig.json` | TypeScript configuration |
| `tailwind.config.ts` | Tailwind CSS configuration |
| `postcss.config.mjs` | PostCSS configuration for Tailwind CSS processing |
| `next.config.mjs` | Next.js configuration |
| `drizzle.config.ts` | Drizzle ORM configuration |
| `components.json` | Shadcn UI components configuration |
| `.env.example` | Example environment variables |
| `.eslintrc.json` | ESLint configuration |
| `prettier.config.cjs` | Prettier configuration |
| `middleware.ts` | Next.js middleware for Clerk auth |

## Directory Structure

### actions/

Server actions for database operations and external API interactions.

- **db/profiles-actions.ts** - User profile CRUD operations (create, get, update, delete)
- **db/todos-actions.ts** - Todo CRUD operations (create, get all, update, delete)
- **stripe-actions.ts** - Stripe subscription and customer management functions

### app/

Next.js 13+ App Router directory containing pages, layouts, and API routes.

- **(auth)/** - Authentication routes (login, signup) with Clerk integration
- **(marketing)/** - Public marketing pages (home, about, contact, pricing)
- **api/stripe/webhooks/** - Stripe webhook API endpoint
- **todo/** - Todo feature pages with todo list and layout
- **layout.tsx** - Root layout with providers, PostHog analytics, and toaster
- **globals.css** - Global CSS styles

### components/

Reusable UI components.

- **ui/** - Shadcn UI components (buttons, forms, dialogs, etc.)
- **header.tsx** - Main application header with navigation
- **landing/** - Landing page components (hero, features)
- **magicui/** - Animated UI components
- **sidebar/** - Sidebar navigation components
- **utilities/** - Utility components (theme switcher, providers, PostHog integration)

### db/

Database schema and migrations using Drizzle ORM.

- **db.ts** - Database connection setup
- **schema/profiles-schema.ts** - User profiles table schema
- **schema/todos-schema.ts** - Todos table schema
- **migrations/** - SQL migration files

### hooks/

Custom React hooks.

- **use-mobile.tsx** - Mobile viewport detection
- **use-toast.ts** - Toast notification hook

### lib/

Utility functions and library configurations.

- **utils.ts** - Class name merging utility (cn function)
- **stripe.ts** - Stripe client configuration
- **hooks/** - Additional hooks (copy to clipboard)

### types/

TypeScript type definitions.

- **server-action-types.ts** - ActionState generic type for server actions
- **index.ts** - Type exports

### docs/

Project documentation.

- **README.md** - Documentation index
- **structure.md** - This file
- **app.md** - App directory documentation
- **components.md** - Components documentation
- **lib.md** - Lib utilities documentation
- **db.md** - Database documentation
- **hooks.md** - Hooks documentation
- **actions.md** - Server actions documentation
- **types.md** - Type definitions documentation

### public/

Static assets served at the root URL.

- **hero.png** - Hero image for landing page

### prompts/

AI prompt templates.

- **perplexity.md** - Perplexity prompt
- **v0.md** - V0 prompt