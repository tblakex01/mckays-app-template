# Mckay's App Template

This is a full-stack app template for courses on [Takeoff](https://JoinTakeoff.com/).

## Sponsors

If you are interested in sponsoring my repos, please contact me at [ads@takeoffai.org](mailto:ads@takeoffai.org).

Or sponsor me directly on [GitHub Sponsors](https://github.com/sponsors/mckaywrigley).

## Tech Stack

- IDE: [Cursor](https://www.cursor.com/)
- AI Tools: [V0](https://v0.dev/), [Perplexity](https://www.perplexity.com/)
- Frontend: [Next.js](https://nextjs.org/docs), [Tailwind](https://tailwindcss.com/docs/guides/nextjs), [Shadcn](https://ui.shadcn.com/docs/installation), [Framer Motion](https://www.framer.com/motion/introduction/)
- Backend: [PostgreSQL](https://www.postgresql.org/about/), [Supabase](https://supabase.com/), [Drizzle](https://orm.drizzle.team/docs/get-started-postgresql), [Server Actions](https://nextjs.org/docs/app/building-your-application/data-fetching/server-actions-and-mutations)
- Auth: [Clerk](https://clerk.com/)
- Payments: [Stripe](https://stripe.com/)
- Analytics: [PostHog](https://posthog.com/)

## Prerequisites

You will need accounts for the following services.

They all have free plans that you can use to get started.

- Create a [Cursor](https://www.cursor.com/) account
- Create a [GitHub](https://github.com/) account
- Create a [Supabase](https://supabase.com/) account
- Create a [Clerk](https://clerk.com/) account
- Create a [Stripe](https://stripe.com/) account
- Create a [PostHog](https://posthog.com/) account
- Create a [Vercel](https://vercel.com/) account

You will likely not need paid plans unless you are building a business.

## Environment Variables

```bash
# DB (Supabase)
DATABASE_URL=

# Auth (Clerk)
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=
CLERK_SECRET_KEY=
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/login
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/signup

# Payments (Stripe)
STRIPE_SECRET_KEY=
STRIPE_WEBHOOK_SECRET=
NEXT_PUBLIC_STRIPE_PORTAL_LINK=
NEXT_PUBLIC_STRIPE_PAYMENT_LINK_YEARLY=
NEXT_PUBLIC_STRIPE_PAYMENT_LINK_MONTHLY=

# Analytics (PostHog)
NEXT_PUBLIC_POSTHOG_KEY=
NEXT_PUBLIC_POSTHOG_HOST=
```

## Setup

Follow these steps to get the project running locally:

### 1. Clone the repository

```bash
git clone <repository-url>
cd mckays-app-template
```

### 2. Install dependencies

```bash
npm install
```

This will install all required dependencies including Next.js, React, TypeScript, and other libraries defined in `package.json`.

### 3. Set up environment variables

Copy the example environment file and fill in your credentials:

```bash
cp .env.example .env.local
```

Then edit `.env.local` and add the required values for:

- `DATABASE_URL` - Your Supabase PostgreSQL connection string
- `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY` and `CLERK_SECRET_KEY` - From your Clerk dashboard
- `STRIPE_SECRET_KEY` and related Stripe keys - From your Stripe dashboard
- `NEXT_PUBLIC_POSTHOG_KEY` and `NEXT_PUBLIC_POSTHOG_HOST` - From your PostHog project

### 4. Run the development server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser to see the application.

### 5. Run linting and type checking

Check for code quality issues:

```bash
npm run lint      # Run ESLint
npm run type-check  # Run TypeScript type checking
```

Fix linting issues automatically:

```bash
npm run lint:fix  # Auto-fix ESLint issues
npm run format:write  # Format code with Prettier
```

## Project Structure

```
├── app/              # Next.js app router (pages, layouts, API routes)
├── components/       # Reusable UI components
├── db/               # Database schema and migrations (Drizzle ORM)
├── hooks/            # Custom React hooks
├── lib/              # Utility functions and libraries
├── public/           # Static assets (images, fonts, etc.)
├── types/            # TypeScript type definitions
└── actions/          # Server actions
```

### Directory Details

- **`app/`** - Next.js 13+ app router directory containing pages, layouts, loading states, and API routes
- **`components/`** - Reusable UI components built with React and styled with Tailwind CSS
- **`db/`** - Database schema definitions, migrations, and Drizzle ORM configuration
- **`hooks/`** - Custom React hooks for state management and data fetching
- **`lib/`** - Utility functions, helper methods, and external library configurations
- **`public/`** - Static assets served at the root URL (images, favicon, etc.)
- **`types/`** - Shared TypeScript type definitions and interfaces
- **`actions/`** - Server actions for form submissions and data mutations

## Available Scripts

| Script | Description |
|--------|-------------|
| `dev` | Start the development server with hot reload |
| `build` | Build the application for production |
| `start` | Start the production server |
| `lint` | Run ESLint to check for code issues |
| `clean` | Run lint:fix and format:write together |
| `type-check` | Run TypeScript compiler to check types |
| `lint:fix` | Run ESLint with --fix to auto-fix issues |
| `format:write` | Format code with Prettier |
| `format:check` | Check code formatting without modifying files |
| `analyze` | Build with bundle analyzer to inspect bundle size |
| `db:generate` | Generate Drizzle ORM migrations |
| `db:migrate` | Run database migrations |

## Deployment

This template is configured for deployment to Vercel:

1. Push your code to a GitHub repository
2. Import the project in Vercel ([https://vercel.com/new](https://vercel.com/new))
3. Vercel will automatically detect the Next.js project and configure the build settings
4. Add your environment variables in the Vercel project settings
5. Deploy! Vercel will handle the build and deployment process

For more detailed deployment instructions, see the [Vercel Next.js documentation](https://vercel.com/docs/frameworks/next.js).

## Documentation

For more detailed documentation on specific parts of the codebase, see the [docs/](./docs) folder:

- [Project Structure](./docs/structure.md) - Detailed directory and file structure
- [App Directory](./docs/app.md) - Routes, layouts, and API endpoints
- [Components](./docs/components.md) - Reusable UI components
- [Database](./docs/db.md) - Schema and migrations
- [Actions](./docs/actions.md) - Server actions
- [Hooks](./docs/hooks.md) - Custom React hooks
- [Types](./docs/types.md) - TypeScript type definitions
- [Lib Utilities](./docs/lib.md) - Utility functions