# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

### Package Manager
- This project uses **npm** as the package manager (standard Node.js project)
- Install dependencies: `npm install`

### Development
- Start dev server: `npm run dev`
- Start with browser: `npm run dev -- --open`
- Type checking: `npm run check` or `npm run check:watch`

### Testing
- Run all tests: `npm run test`
- Unit tests only: `npm run test:unit`
- E2E tests only: `npm run test:e2e`
- Unit tests in watch mode: `npm run test:unit`

### Code Quality
- Format code: `npm run format`
- Lint and format check: `npm run lint`

### Build
- Production build: `npm run build`
- Preview build: `npm run preview`

## Project Architecture

### Tech Stack
- **SvelteKit 2.x** with **Svelte 5** (using new `$state` runes)
- **TypeScript** for type safety
- **TailwindCSS 4.x** for styling with typography plugin
- **Static adapter** for deployment (builds to static files)

### Key Features
- **Responsive design** with mobile-first approach
- **Spanish language** content for Argentine market
- **Minimal, sophisticated aesthetic** using stone color palette
- **Dynamic content rotation** with animated text changes
- **Single-page layout** designed to fit viewport without scrolling on desktop

### Content Focus
- **Information aggregation platform** for Argentina's music scene
- Aggregates: concerts, festivals, artists, pricing info (does NOT sell tickets)
- Coverage: Major Argentine cities (Buenos Aires, Córdoba, Rosario, etc.)
- Genres: Rock, Jazz, Electronic, Folklore, Tango, Pop, Cumbia, etc.

### Code Structure
- **Main page**: `src/routes/+page.svelte` - Complete landing page with rotating content
- **Styling**: TailwindCSS classes with custom noise texture background
- **Responsiveness**: Uses sm/md/lg breakpoints with careful mobile optimization
- **State management**: Svelte 5 `$state` runes for reactive content rotation
- **Analytics**: Integrated analytics tracking script in `src/app.html`

### Design Principles
- **Clean, minimal aesthetic** inspired by SF startup design
- **Stone color palette** (stone-50 to stone-900) for sophistication
- **Typography scaling** across all device sizes
- **Mobile-responsive grids** that adapt layouts appropriately
- **Subtle animations** for content rotation and hover states

### Important Notes
- Uses **static adapter** - builds to static files for deployment
- **Spanish content** with "Argentina Music" as brand name (kept in English)
- **Mobile-first responsive design** with careful attention to small screens
- **Single viewport page** - no scrolling required on desktop
- **Inter font** loaded from Google Fonts for typography consistency
- **SEO optimized** with structured data for search engines

## Testing Configuration
- **Unit tests**: Vitest with Svelte 5 support
- **E2E tests**: Playwright for browser testing
- **Type checking**: svelte-check with TypeScript
- **Linting**: ESLint with Svelte plugin

## Git Commit Guidelines

- Use conventional commits format: `type(scope): description`
- Use 50/72 rule
- Keep commit messages clean and focused on code changes only
- NEVER add co-authors, "Generated with" tags, or other metadata
- Use separate commits for different file types/purposes:
  - Scripts/automation: `feat:` or `fix:`
  - Documentation: `docs:`
  - Configuration: `fix:` or `refactor:`
- Focus on what changed and why, not who or how it was generated