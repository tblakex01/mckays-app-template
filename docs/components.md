# Components Directory

This directory contains reusable UI components used throughout the application.

## Subdirectories

- `header/` - Header component
- `landing/` - Components specific to landing/marketing pages
- `magicui/` - Magic UI components (animated UI elements)
- `sidebar/` - Sidebar components
- `ui/` - Shadcn UI components (buttons, forms, etc.)
- `utilities/` - Utility components and providers

## Key Files

- `components.json` - Configuration for Shadcn UI
- `header.tsx` - Main header component

## Detailed Structure

### header/

Contains the header component.

- `header.tsx` - Main header navigation

### landing/

Components used on landing/marketing pages.

- `features.tsx` - Features section component
- `hero.tsx` - Hero section component

### magicui/

Animated UI components from Magic UI.

- `animated-gradient-text.tsx` - Animated gradient text
- `hero-video-dialog.tsx` - Hero video dialog component

### sidebar/

Components for the sidebar navigation.

- `app-sidebar.tsx` - Main sidebar container
- `nav-main.tsx` - Main navigation items
- `nav-projects.tsx` - Projects navigation
- `nav-user.tsx` - User-related navigation
- `team-switcher.tsx` - Team switcher component

### ui/

Shadcn UI components (buttons, forms, dialogs, etc.). These are reusable primitives.

### utilities/

Utility components and providers.

- `providers.tsx` - React providers (e.g., for theme, authentication)
- `tailwind-indicator.tsx` - Component to show Tailwind CSS breakpoint
- `theme-switcher.tsx` - Component to switch between light/dark theme
- `posthog/` - PostHog analytics integration
  - `posthog-pageview.tsx` - Pageview tracking
  - `posthog-provider.tsx` - PostHog provider
  - `posthog-user-identity.tsx` - User identity tracking
