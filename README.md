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

1. Clone the repository
2. Copy `.env.example` to `.env.local` and fill in the environment variables from above
3. Install dependencies: `npm install`
4. Run the development server: `npm run dev`
5. Run linting: `npm run lint`
6. Run type checking: `npm run type-check`

## Project Structure

- `app/` - Next.js app router
- `components/` - Reusable UI components
- `db/` - Database schema and migrations (Drizzle ORM)
- `hooks/` - Custom React hooks
- `lib/` - Utility functions and libraries
- `public/` - Static assets
- `types/` - TypeScript type definitions
- `actions/` - Server actions

## Available Scripts

- `dev` - Run development server
- `build` - Build for production
- `start` - Start production server
- `lint` - Run ESLint
- `clean` - Run lint:fix and format:write
- `type-check` - Run TypeScript type checking
- `lint:fix` - Run ESLint with --fix flag
- `format:write` - Format code with Prettier
- `format:check` - Check code formatting with Prettier
- `analyze` - Build with bundle analyzer
- `db:generate` - Generate Drizzle ORM schema
- `db:migrate` - Run Drizzle ORM migrations

## Deployment

This template is configured for deployment to Vercel:

1. Push your code to a GitHub repository
2. Import the project in Vercel (https://vercel.com/new)
3. Vercel will automatically detect the Next.js project and configure the build settings
4. Add your environment variables in the Vercel project settings
5. Deploy! Vercel will handle the build and deployment process

For more detailed deployment instructions, see the [Vercel Next.js documentation](https://vercel.com/docs/frameworks/next.js).