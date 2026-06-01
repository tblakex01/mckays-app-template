# Codebase Exploration Summary

## Purpose and Audience

This document provides a deep-dive reference for **new contributors**, **instructors**, and **developers** who need to understand the mckays-app-template codebase beyond the README. It complements (rather than duplicates) the README by capturing implementation details, schema definitions, and configuration specifics that change frequently during development.

Keep this document updated alongside code changes. When adding new server actions, database tables, environment variables, or configuration, reflect those changes here to maintain a single source of truth for internal codebase structure.

## Project Information

- **Name**: mckays-app-template
- **Version**: 0.1.0
- **Repository**: Takeoff app template (https://JoinTakeoff.com/)
- **Purpose**: Full-stack app template for teaching web development

## Tech Stack

### Frontend
- **Framework**: Next.js 15 (App Router)
- **Language**: TypeScript 5
- **Styling**: Tailwind CSS 3.4 with CSS variables
- **UI Components**: shadcn/ui (based on Radix UI primitives)
- **Animations**: Framer Motion, Embla Carousel
- **Forms**: React Hook Form + Zod validation
- **Themes**: next-themes

### Backend
- **Runtime**: Next.js Server Components + Server Actions
- **Database**: PostgreSQL (hosted on Supabase)
- **ORM**: Drizzle ORM
- **Connection**: postgres (node-postgres)

### Authentication
- **Provider**: Clerk

### Payments
- **Provider**: Stripe
- **Webhooks**: Stripe webhook handler at `/api/stripe/webhooks`

### Analytics
- **Provider**: PostHog

## Project Structure

```
├── actions/                  # Server actions
│   └── db/
│       ├── profiles-actions.ts
│       └── todos-actions.ts
├── app/                      # Next.js App Router
│   ├── (auth)/              # Auth route group (login/signup)
│   │   ├── layout.tsx
│   │   ├── login/[[...login]]/page.tsx
│   │   └── signup/[[...signup]]/page.tsx
│   ├── (marketing)/         # Marketing pages
│   │   ├── layout.tsx
│   │   ├── page.tsx         # Landing page
│   │   ├── about/page.tsx
│   │   ├── contact/page.tsx
│   │   └── pricing/page.tsx
│   ├── api/stripe/webhooks/route.ts
│   ├── todo/                # Protected todo app
│   │   ├── layout.tsx
│   │   ├── page.tsx
│   │   └── _components/todo-list.tsx
│   ├── globals.css
│   ├── layout.tsx           # Root layout
│   └── favicon.ico
├── components/
│   ├── ui/                  # shadcn/ui components
│   │   ├── form.tsx
│   │   ├── textarea.tsx
│   │   ├── sidebar.tsx
│   │   ├── tooltip.tsx
│   │   ├── popover.tsx
│   │   ├── hover-card.tsx
│   │   ├── sonner.tsx
│   │   ├── progress.tsx
│   │   ├── table.tsx
│   │   ├── toggle-group.tsx
│   │   ├── scroll-area.tsx
│   │   ├── pagination.tsx
│   │   ├── chart.tsx
│   │   ├── badge.tsx
│   │   ├── carousel.tsx
│   │   ├── command.tsx
│   │   ├── checkbox.tsx
│   │   ├── avatar.tsx
│   │   ├── accordion.tsx
│   │   ├── calendar.tsx
│   │   └── collapsible.tsx
│   ├── utilities/
│   │   ├── providers.tsx   # Theme and context providers
│   │   ├── posthog-provider.tsx
│   │   ├── posthog-pageview.tsx
│   │   ├── posthog-user-identity.tsx
│   │   ├── tailwind-indicator.tsx
│   │   └── theme-switcher.tsx
│   ├── landing/
│   │   ├── hero.tsx
│   │   └── features.tsx
│   ├── magicui/
│   │   ├── animated-gradient-text.tsx
│   │   └── hero-video-dialog.tsx
│   ├── sidebar/
│   │   ├── app-sidebar.tsx
│   │   ├── nav-main.tsx
│   │   ├── nav-projects.tsx
│   │   ├── nav-user.tsx
│   │   └── team-switcher.tsx
│   └── header.tsx
├── db/
│   ├── db.ts                # Database connection (drizzle-orm/postgres-js)
│   ├── drizzle.config.ts    # Drizzle Kit config
│   └── schema/
│       ├── index.ts
│       ├── profiles-schema.ts
│       └── todos-schema.ts
├── db/migrations/
│   ├── 0000_nostalgic_mauler.sql
│   └── meta/                # Migration snapshots
├── hooks/
│   ├── use-toast.ts
│   └── use-mobile.tsx
├── lib/
│   ├── utils.ts             # cn() utility (clsx + twMerge)
│   ├── stripe.ts
│   └── hooks/
│       ├── use-toast.ts
│       ├── use-copy-to-clipboard.tsx
│       └── use-mobile.tsx
├── prompts/
│   ├── v0.md
│   └── perplexity.md
├── public/
│   └── hero.png
├── types/
│   ├── index.ts
│   └── server-action-types.ts
├── .cursor/rules/           # Cursor AI rules (backend, frontend, auth, storage, analytics, payments)
├── .github/funding.yaml
├── .husky/pre-commit
├── components.json          # shadcn/ui configuration
├── middleware.ts            # Clerk middleware (protects /todo routes)
├── next.config.mjs
├── package.json
├── tailwind.config.ts
├── postcss.config.mjs
├── tsconfig.json
├── package-lock.json
├── .eslintrc.json
├── prettier.config.cjs
├── .env.example
├── .gitignore
├── .repo_ignore
├── .cursorrules
├── license
└── README.md
```

## Database Schema

### profiles Table
- `user_id` (TEXT, PK) - maps to Clerk user ID
- `membership` (ENUM: 'free', 'pro', default: 'free')
- `stripe_customer_id` (TEXT, nullable)
- `stripe_subscription_id` (TEXT, nullable)
- `created_at` (TIMESTAMP, default: now)
- `updated_at` (TIMESTAMP, auto-updated)

### todos Table
- `id` (UUID, PK, default: gen_random_uuid())
- `user_id` (TEXT, not null)
- `content` (TEXT, not null)
- `completed` (BOOLEAN, default: false)
- `created_at` (TIMESTAMP, default: now)
- `updated_at` (TIMESTAMP, auto-updated)

## Server Actions

- `createProfileAction` - Create a new user profile
- `getProfileByUserIdAction` - Get profile by user ID
- `updateProfileAction` - Update profile by user ID
- `updateProfileByStripeCustomerIdAction` - Update profile by Stripe customer ID
- `deleteProfileAction` - Delete profile by user ID

## Route Protection

- `/todo` and nested routes are protected via Clerk middleware
- Unauthenticated users are redirected to `/login`
- Root layout auto-creates a profile for authenticated users who don't have one

## Key Configuration Files

- `components.json` - shadcn/ui configuration (style, path aliases, Tailwind config)
- `tailwind.config.ts` - Tailwind CSS configuration
- `drizzle.config.ts` - Drizzle ORM configuration (points to `./db/schema/index.ts`)
- `postcss.config.mjs` - PostCSS configuration
- `.eslintrc.json` - ESLint configuration
- `prettier.config.cjs` - Prettier configuration
- `tsconfig.json` - TypeScript configuration
- `next.config.mjs` - Next.js configuration

## Available npm Scripts

| Script | Command | Description |
|--------|---------|-------------|
| dev | `next dev` | Start development server |
| build | `next build` | Build for production |
| start | `next start` | Start production server |
| lint | `next lint` | Run ESLint |
| lint:fix | `next lint --fix` | Auto-fix ESLint issues |
| format:write | `prettier --write ...` | Format with Prettier |
| format:check | `prettier --check ...` | Check formatting |
| type-check | `tsc --noEmit` | TypeScript check |
| clean | `npm run lint:fix && npm run format:write` | Clean code |
| analyze | `ANALYZE=true npm run build` | Bundle analysis |
| db:generate | `npx drizzle-kit generate` | Generate DB migrations |
| db:migrate | `npx drizzle-kit migrate` | Run DB migrations |
| prepare | `husky install` | Install git hooks |

## Environment Variables

Required environment variables (see `.env.example`):

### Database
- `DATABASE_URL` - Supabase PostgreSQL connection string

### Authentication (Clerk)
- `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY`
- `CLERK_SECRET_KEY`
- `NEXT_PUBLIC_CLERK_SIGN_IN_URL` (default: `/login`)
- `NEXT_PUBLIC_CLERK_SIGN_UP_URL` (default: `/signup`)

### Payments (Stripe)
- `STRIPE_SECRET_KEY`
- `STRIPE_WEBHOOK_SECRET`
- `NEXT_PUBLIC_STRIPE_PORTAL_LINK`
- `NEXT_PUBLIC_STRIPE_PAYMENT_LINK_YEARLY`
- `NEXT_PUBLIC_STRIPE_PAYMENT_LINK_MONTHLY`

### Analytics (PostHog)
- `NEXT_PUBLIC_POSTHOG_KEY`
- `NEXT_PUBLIC_POSTHOG_HOST`

## Notes

- The existing `README.md` already contains documentation for Tech Stack, Prerequisites, Environment Variables, Setup, Project Structure, Available Scripts, and Deployment sections.
- The app has two main sections: marketing pages (landing, about, contact, pricing) and authenticated app pages (todo app).
- Stripe webhook endpoint exists at `/api/stripe/webhooks` for handling subscription events.
- Profiles are auto-created on first authenticated visit.
- The template uses Cursor AI rules in `.cursor/rules/` for AI-assisted development guidance.
