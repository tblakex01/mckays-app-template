# DB Directory

This directory contains the database schema, migrations, and Drizzle ORM configuration.

## Key Files

- `db.ts` - Drizzle ORM database connection and instance
- `drizzle.config.ts` - Drizzle ORM configuration file (located in project root, but related)

## Subdirectories

- `migrations/` - SQL migration files
- `schema/` - Database schema definitions

## Detailed Structure

### db.ts

Sets up the connection to the PostgreSQL database (via Supabase) and initializes the Drizzle ORM client.

### migrations/

Contains SQL migration files that define the evolution of the database schema.

- `0000_nostalgic_mauler.sql` - Initial migration creating tables for profiles and todos
- `meta/` - Metadata about migrations (used by Drizzle)

### schema/

Contains TypeScript files defining the database schema using Drizzle ORM.

- `index.ts` - Exports all schema definitions
- `profiles-schema.ts` - Schema for user profiles table
- `todos-schema.ts` - Schema for todos table

## Database Schema

### profiles-schema.ts

Defines the `profiles` table for user profiles:

| Column | Type | Description |
|--------|------|-------------|
| `userId` | text | Primary key, linked to Clerk user ID |
| `membership` | enum | 'free' or 'pro', defaults to 'free' |
| `stripeCustomerId` | text | Stripe customer ID (optional) |
| `stripeSubscriptionId` | text | Stripe subscription ID (optional) |
| `createdAt` | timestamp | Auto-set on creation |
| `updatedAt` | timestamp | Auto-updated on changes |

### todos-schema.ts

Defines the `todos` table:

| Column | Type | Description |
|--------|------|-------------|
| `id` | uuid | Primary key, auto-generated |
| `userId` | text | Foreign key to user |
| `content` | text | Todo content |
| `completed` | boolean | Completion status, defaults to false |
| `createdAt` | timestamp | Auto-set on creation |
| `updatedAt` | timestamp | Auto-updated on changes |

## Description

The db directory is where all database-related code lives. The application uses Drizzle ORM for type-safe SQL queries and migrations. The schema defines the tables, and the migrations are used to update the database schema over time.
