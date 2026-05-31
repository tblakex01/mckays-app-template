# Lib Directory

This directory contains utility functions, helper methods, and external library configurations.

## Key Files

- `stripe.ts` - Stripe library configuration and client instance
- `utils.ts` - General utility functions (cn for className merging)

## Subdirectories

- `hooks/` - Custom React hooks that are used as utilities (may overlap with hooks/ directory at root)

## Description

The lib directory houses code that is shared across various parts of the application, such as API clients, formatters, and helper functions that are not specific to React components or hooks.

### stripe.ts

Configures and exports the Stripe client for interacting with the Stripe API. The client is initialized with your secret key and configured for the 2024-06-20 API version. Used by `stripe-actions.ts` for subscription management.

### utils.ts

Contains the `cn` function that combines `clsx` and `tailwind-merge` for conditional className merging with proper Tailwind CSS class deduplication.

### hooks/

Custom hooks that are used as utilities across the application:

- `use-copy-to-clipboard.tsx` - Hook for copying text to clipboard with success state tracking
- `use-mobile.tsx` - Hook to detect mobile screen size (duplicate of root hooks)
- `use-toast.ts` - Hook for toast notification state management (duplicate of root hooks)