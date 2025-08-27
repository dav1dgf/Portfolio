# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a personal portfolio website built with Astro, Tailwind CSS, and TypeScript. The project follows a component-based architecture with Astro components and uses TypeScript in strict mode.

## Development Commands

```bash
# Start development server
npm run dev
# or
npm start

# Build for production (runs type checking first)
npm run build

# Preview production build
npm run preview

# Type checking (automatically runs before build)
astro check
```

## Architecture and Structure

### Technology Stack
- **Framework**: Astro 4.16 with TypeScript support
- **Styling**: Tailwind CSS 3.4
- **Type Safety**: TypeScript with strict mode enabled
- **Font**: League Spartan Variable font

### Component Architecture

The project uses Astro's `.astro` component format with a clear separation:

1. **Layout Layer** (`src/layouts/`)
   - `Layout.astro`: Main HTML structure with global styles, dark mode support, and header/footer inclusion

2. **Component Layer** (`src/components/`)
   - Reusable UI components like `Badge`, `Card`, `SectionContainer`, `TitleSection`
   - Social interaction components: `SocialPill`, `LinkButton`
   - Icon components in `icons/` subdirectory for technology and social icons
   - Main content sections: `Projects.astro` containing project data and rendering logic

3. **Page Layer** (`src/pages/`)
   - `index.astro`: Main landing page that composes components together

### Key Implementation Patterns

**Component Props**: Components use TypeScript interfaces for prop validation:
```astro
---
interface Props {
  title: string;
  description: string;
}
const { title, description } = Astro.props;
---
```

**Project Data Structure**: Projects are defined as static data with tags system in `Projects.astro`:
- Tags are defined as objects with name and CSS classes
- Projects array contains metadata, links, and tag references

**Styling Approach**:
- Tailwind CSS for utility-first styling
- Global styles defined in `Layout.astro` for animations and dark mode
- Scroll-based header animation using CSS animation-timeline

## Important Conventions

- All components use `.astro` extension
- TypeScript strict mode is enforced
- Dark mode is handled via CSS `prefers-color-scheme`
- Images are stored in `/public` directory
- Component imports use relative paths from `src/`