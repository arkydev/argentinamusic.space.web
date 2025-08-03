# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

### Package Manager
- This project uses **bun** as the package manager (bun.lock present)
- Install dependencies: `bun install`

### Development
- Start dev server: `bun run dev`
- Start with browser: `bun run dev -- --open`
- Type checking: `bun run check` or `bun run check:watch`

### Testing
- Run all tests: `bun run test`
- Unit tests only: `bun run test:unit`
- E2E tests only: `bun run test:e2e`
- Unit tests in watch mode: `bun run test:unit`

### Code Quality
- Format code: `bun run format`
- Lint and format check: `bun run lint`

### Build
- Production build: `bun run build`
- Preview build: `bun run preview`

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