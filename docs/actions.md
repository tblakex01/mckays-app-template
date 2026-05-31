# Actions Directory

This directory contains server actions for database operations and external API interactions.

## Key Files

### Database Actions (actions/db/)

- `profiles-actions.ts` - Server actions for user profile CRUD operations
- `todos-actions.ts` - Server actions for todo CRUD operations

### Stripe Actions

- `stripe-actions.ts` - Server actions for Stripe subscription and customer management

## Database Actions

### profiles-actions.ts

Server actions for managing user profiles in the database:

- `createProfileAction(data)` - Creates a new user profile
- `getProfileByUserIdAction(userId)` - Retrieves a profile by user ID
- `updateProfileAction(userId, data)` - Updates a profile by user ID
- `updateProfileByStripeCustomerIdAction(stripeCustomerId, data)` - Updates a profile by Stripe customer ID
- `deleteProfileAction(userId)` - Deletes a profile by user ID

All actions return `ActionState<T>` for type-safe responses.

### todos-actions.ts

Server actions for managing todos in the database:

- `createTodoAction(todo)` - Creates a new todo item
- `getTodosAction(userId)` - Retrieves all todos for a user
- `updateTodoAction(id, data)` - Updates a todo by ID
- `deleteTodoAction(id)` - Deletes a todo by ID

All actions return `ActionState<T>` for type-safe responses.

## Stripe Actions

### stripe-actions.ts

Server functions for Stripe integration:

- `updateStripeCustomer(userId, subscriptionId, customerId)` - Updates customer profile with Stripe IDs
- `manageSubscriptionStatusChange(subscriptionId, customerId, productId)` - Handles subscription status changes from webhooks

These functions handle syncing user profiles with Stripe subscription data and managing membership status.