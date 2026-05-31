# App Directory

This directory contains the Next.js app router structure, including routes, layouts, and API routes.

## Subdirectories

- `(auth)` - Authentication routes (login, signup)
- `(marketing)` - Marketing pages (about, contact, pricing)
- `api` - API routes (e.g., Stripe webhooks)
- `todo` - Todo feature routes

## Key Files

- `layout.tsx` - Root layout
- `globals.css` - Global CSS styles

## Detailed Structure

See below for a more detailed breakdown of each subdirectory.

### (auth)

Contains authentication-related pages.

- `layout.tsx` - Layout for auth pages
- `login/` - Login page
  - `[[...login]]/page.tsx` - Login page (Clerk integration)
- `signup/` - Signup page
  - `[[...signup]]/page.tsx` - Signup page (Clerk integration)

### (marketing)

Contains marketing pages.

- `layout.tsx` - Layout for marketing pages
- `page.tsx` - Home page
- `about/` - About page
  - `page.tsx` - About page content
- `contact/` - Contact page
  - `page.tsx` - Contact page content
- `pricing/` - Pricing page
  - `page.tsx` - Pricing page content

### api

Contains API routes.

- `stripe/` - Stripe-related API routes
  - `webhooks/` - Stripe webhook handlers
    - `route.ts` - Webhook endpoint for handling subscription events (checkout.session.completed, customer.subscription.updated, customer.subscription.deleted)

### todo

Contains todo feature routes.

- `_components/` - Components specific to the todo feature
  - `todo-list.tsx` - Todo list component
- `layout.tsx` - Layout for todo pages
- `page.tsx` - Todo page (likely shows todo list and form)
