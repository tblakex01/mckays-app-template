# Types Directory

This directory contains TypeScript type definitions used throughout the application.

## Key Files

- `index.ts` - Re-exports all type definitions for easy importing
- `server-action-types.ts` - Defines generic types for server actions

## Type Definitions

### ActionState<T>

A generic discriminated union type for server action responses. Used to provide type-safe responses for all server actions.

```typescript
export type ActionState<T> =
  | { isSuccess: true; message: string; data: T }
  | { isSuccess: false; message: string; data?: never }
```

This allows server actions to return either a success state with data or a failure state with an error message.

## Usage

Types are imported using the `@/types` alias. For example:

```typescript
import { ActionState } from "@/types"
```

Database-generated types are exported from the schema files in `db/schema/` and include:

- `InsertProfile` - Type for inserting a new profile
- `SelectProfile` - Type for selecting a profile from the database
- `InsertTodo` - Type for inserting a new todo
- `SelectTodo` - Type for selecting a todo from the database