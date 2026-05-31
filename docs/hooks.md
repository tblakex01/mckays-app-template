# Hooks Directory

This directory contains custom React hooks used throughout the application.

## Key Files

- `use-mobile.tsx` - Hook to detect mobile screen size and orientation
- `use-toast.ts` - Hook for toast notification state management (custom implementation)

## Description

Custom hooks encapsulate reusable logic that can be shared across components. These hooks provide state and effects for common functionalities like detecting device characteristics or displaying notifications.

### use-mobile.tsx

Returns a boolean indicating whether the user is on a mobile device by using a media query for screen width (768px breakpoint). Uses window.matchMedia and resize event listeners to track viewport changes.

### use-toast.ts

Custom hook for managing toast notifications. Provides:

- `toast()` - Function to create and display toast notifications with title, description, and optional action
- `useToast()` - React hook that returns current toast state and methods to dismiss toasts
- Supports toast types: success, error, warning, info
- Uses a reducer pattern for state management with limited concurrent toasts (TOAST_LIMIT = 1)
