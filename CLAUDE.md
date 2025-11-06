# CLAUDE.md - AI Assistant Guide

This document provides comprehensive guidance for AI assistants (like Claude) working on the Yoga Tung personal website project.

## 📋 Project Overview

This is a personal website for Yoga Tung, built to replace a static page website with a modern, content-managed solution.

### Core Technologies
- **Astro 5.x** - Static site generator (includes Vite 5.x)
- **React 18** - For interactive UI components
- **TypeScript** - Type-safe development
- **Tailwind CSS 3.x** - Utility-first styling
- **shadcn/ui** - Component library
- **Magic UI** - Animated components
- **Decap CMS** - Git-based content management
- **Netlify** - Hosting and deployment platform

### Project Goals
1. Replace a static website with dynamic content management
2. Provide blog functionality
3. Enable non-technical content updates via CMS
4. Maintain fast performance and SEO
5. Modern, responsive design

## ✅ Project Status (2025-11-05)

**Build Status**: ✅ All systems operational
- Production builds: Working (3 pages generated)
- TypeScript checks: 0 errors, 0 warnings, 0 hints
- Development server: Running on port 4321
- Sitemap generation: Working

**Recent Critical Fixes**:
1. **Tailwind CSS Configuration**: Fixed missing color definitions that caused build errors
2. **Homepage Optimization**: Removed unnecessary React hydration for better performance
3. **SEO Improvements**: Added sitemap integration, favicon, and robots.txt
4. **Type Checking**: Added @astrojs/check for comprehensive type validation

**Known Issues**:
- 3 moderate vulnerabilities in esbuild (development dependencies only, production unaffected)
- Empty `pages` content collection (warning during build, not an error)

## 🏗️ Architecture Decisions

### Why Astro?
- **Best-in-class performance**: Ships zero JavaScript by default
- **Island architecture**: Hydrates only interactive components
- **Content Collections**: Type-safe content management
- **Framework agnostic**: Can use React, Vue, Svelte, etc.

### Why Not Full SSR/SSG Framework?
- Project doesn't need server-side rendering
- Static generation is sufficient and faster
- Netlify hosting is optimized for static sites

### Component Strategy
- **Astro components** (.astro): For static, content-heavy pages
- **React components** (.tsx): For interactive UI elements (buttons, forms, etc.)
- **Client directives**: Use `client:load` for React components that need interactivity

### Content Management
- **Decap CMS**: Git-based, no database needed
- **Content Collections**: Type-safe with Zod schemas
- **Markdown**: For blog posts and pages

## 📁 Project Structure

```
yoga-tung/
├── public/                     # Static assets
│   ├── admin/                  # Decap CMS interface
│   │   ├── config.yml          # CMS configuration
│   │   └── index.html          # CMS entry point
│   ├── images/uploads/         # Media uploads from CMS
│   ├── favicon.svg             # Website icon (purple "Y")
│   └── robots.txt              # Search engine crawling rules
│
├── src/
│   ├── components/
│   │   └── ui/                 # Reusable UI components
│   │       ├── button.tsx      # shadcn/ui Button
│   │       └── bento-grid.tsx  # Magic UI Bento Grid
│   │
│   ├── content/                # Content collections
│   │   ├── blog/               # Blog posts (Markdown)
│   │   │   └── 2025-01-01-welcome.md
│   │   ├── pages/              # Static pages (Markdown)
│   │   └── config.ts           # Zod schemas for content
│   │
│   ├── layouts/
│   │   └── Layout.astro        # Main layout wrapper
│   │
│   ├── lib/
│   │   └── utils.ts            # Utility functions (cn helper)
│   │
│   ├── pages/                  # File-based routing
│   │   ├── index.astro         # Homepage (no React hydration)
│   │   ├── blog.astro          # Blog listing
│   │   └── blog/
│   │       └── [...slug].astro # Dynamic blog post pages
│   │
│   └── styles/
│       └── globals.css         # Global styles + Tailwind
│
├── .env.example                # Environment variables template
├── .gitignore                  # Git ignore rules
├── .node-version               # Node.js version specification (20)
├── astro.config.mjs            # Astro configuration (with sitemap)
├── CLAUDE.md                   # This file
├── netlify.toml                # Netlify deployment config
├── package.json                # Dependencies and scripts
├── README.md                   # User-facing documentation
├── tailwind.config.mjs         # Tailwind config (complete color palette)
└── tsconfig.json               # TypeScript configuration
```

## 🎨 Styling Conventions

### Tailwind CSS
- Use Tailwind utility classes for styling
- Follow mobile-first approach
- Use semantic color names from theme

### Dark Mode
- Dark mode is configured via `class` strategy
- CSS variables defined in `src/styles/globals.css`
- Use `dark:` prefix for dark mode styles

### Component Styling
```astro
<!-- Good: Semantic, responsive classes -->
<div class="container mx-auto px-4 py-8 md:py-16">
  <h1 class="text-2xl md:text-4xl font-bold mb-4">Title</h1>
</div>

<!-- Avoid: Inline styles -->
<div style="padding: 20px;">Bad</div>
```

## 🧩 Adding Components

### Adding shadcn/ui Components

1. Visit https://ui.shadcn.com/docs/components
2. Copy the component code
3. Create file in `src/components/ui/[component-name].tsx`
4. Adjust imports:
   ```tsx
   // Change this:
   import { cn } from "@/lib/utils"

   // To this:
   import { cn } from "../../lib/utils"
   ```
5. Use in Astro files with `client:load`:
   ```astro
   ---
   import { Button } from '../components/ui/button';
   ---
   <Button client:load>Click me</Button>
   ```

### Adding Magic UI Components

1. Visit https://magicui.design/
2. Copy component code
3. Create file in `src/components/ui/`
4. Install any required dependencies (usually `framer-motion`)
5. Use with `client:load` directive

## 📝 Content Management

### Blog Posts

Location: `src/content/blog/`

Schema (defined in `src/content/config.ts`):
```typescript
{
  title: string
  description: string
  date: Date
  image?: string
  tags?: string[]
}
```

Example blog post:
```markdown
---
title: "My Blog Post"
description: "A short description"
date: 2025-01-15
tags: ["tech", "web"]
---

# Content here
```

### Content Collections API

```typescript
// Get all blog posts
import { getCollection } from 'astro:content';
const posts = await getCollection('blog');

// Sort by date
const sorted = posts.sort((a, b) =>
  b.data.date.valueOf() - a.data.date.valueOf()
);

// Render content
const { Content } = await post.render();
```

## 🔧 Common Tasks

### Adding a New Page

1. Create `src/pages/[name].astro`
2. Use Layout component:
```astro
---
import Layout from '../layouts/Layout.astro';
---

<Layout title="Page Title">
  <main>
    <!-- Content here -->
  </main>
</Layout>
```

### Adding a New Blog Post

**Via CMS** (Recommended):
1. Navigate to `/admin`
2. Login (requires Netlify Identity)
3. Click "Blog" → "New Blog"
4. Fill in fields and publish

**Manually**:
1. Create `src/content/blog/YYYY-MM-DD-slug.md`
2. Add frontmatter with required fields
3. Write content in Markdown

### Modifying Styles

**Global styles**: Edit `src/styles/globals.css`
**Component styles**: Use Tailwind classes
**Theme colors**: Modify CSS variables in `globals.css`

### Adding React Interactivity

```astro
---
import InteractiveComponent from '../components/InteractiveComponent.tsx';
---

<!-- client:load - Load on page load -->
<InteractiveComponent client:load />

<!-- client:idle - Load when browser is idle -->
<InteractiveComponent client:idle />

<!-- client:visible - Load when component is visible -->
<InteractiveComponent client:visible />
```

## 🚀 Development Workflow

### Starting Development
```bash
npm install          # Install dependencies
npm run dev          # Start dev server (localhost:4321)
```

### Building for Production
```bash
npm run build        # Build static site to dist/
npm run preview      # Preview production build locally
```

### Type Checking
```bash
npm run astro check  # Check TypeScript and Astro errors
```

## 🐛 Common Issues & Solutions

### Issue: `border-border` class does not exist (FIXED)
**Cause**: Empty `colors: {}` object in `tailwind.config.mjs`
**Solution**: This was fixed in commit `ee7362b`. The complete shadcn/ui color palette is now defined:
```js
colors: {
  border: 'hsl(var(--border))',
  input: 'hsl(var(--input))',
  ring: 'hsl(var(--ring))',
  background: 'hsl(var(--background))',
  foreground: 'hsl(var(--foreground))',
  // ... plus primary, secondary, destructive, muted, accent, popover, card
}
```
All CSS variables from `globals.css` must be mapped to Tailwind colors.

### Issue: React component not interactive
**Cause**: Missing `client:*` directive
**Solution**: Add `client:load` or appropriate directive

### Issue: Invalid HTML - Button wrapping anchor tag
**Cause**: Using `<Button><a href="...">Link</a></Button>`
**Solution**: Use styled anchor tags directly or `<a>` inside button-styled div. See `src/pages/index.astro` for example of properly styled anchor elements.

### Issue: Tailwind classes not applying
**Cause**: Missing content path in `tailwind.config.mjs`
**Solution**: Verify content array includes all file types:
```js
content: ['./src/**/*.{astro,html,js,jsx,md,mdx,ts,tsx}']
```

### Issue: Type errors with content collections
**Cause**: Schema mismatch in frontmatter
**Solution**: Check `src/content/config.ts` schema matches markdown frontmatter

### Issue: Build fails on Netlify
**Cause**: Missing environment variables or build settings
**Solution**: Check `netlify.toml` and Netlify dashboard settings

## 📦 Dependencies

### Core Dependencies
```json
{
  "astro": "^5.0.3",
  "@astrojs/react": "^3.6.2",
  "@astrojs/sitemap": "^3.6.0",
  "@astrojs/tailwind": "^6.0.2",
  "react": "^18.3.1",
  "react-dom": "^18.3.1"
}
```

### UI Dependencies
```json
{
  "tailwindcss": "^3.4.0",
  "class-variance-authority": "^0.7.1",
  "clsx": "^2.1.1",
  "tailwind-merge": "^3.3.1",
  "lucide-react": "^0.552.0",
  "framer-motion": "^12.23.24"
}
```

### Dev Dependencies
```json
{
  "@astrojs/check": "^0.9.5",
  "@types/react": "^18.3.12",
  "@types/react-dom": "^18.3.1",
  "autoprefixer": "^10.4.21",
  "typescript": "^5.6.3"
}
```

**Note**: `@astrojs/check` is required for the build script and TypeScript validation.

## 🔐 Security Considerations

- **Decap CMS**: Uses Netlify Identity for authentication
- **Git Gateway**: Provides secure CMS → Git integration
- **Environment Variables**: Use `.env` for sensitive data (not committed)
- **Content Validation**: Zod schemas validate content structure

## 🎯 Performance Best Practices

1. **Optimize Images**: Use Astro's Image component
2. **Minimize JavaScript**: Only hydrate necessary components
3. **Lazy Load**: Use `client:visible` for below-fold components
4. **Static Generation**: Pre-render all pages at build time
5. **CDN**: Netlify serves from global CDN

## 🧪 Testing Strategy

Currently no automated tests. Future considerations:
- **Unit Tests**: Vitest for utility functions
- **Component Tests**: React Testing Library
- **E2E Tests**: Playwright or Cypress
- **Type Safety**: TypeScript provides compile-time checking

## 📚 Additional Resources

- [Astro Docs](https://docs.astro.build)
- [Astro Content Collections](https://docs.astro.build/en/guides/content-collections/)
- [shadcn/ui](https://ui.shadcn.com)
- [Tailwind CSS](https://tailwindcss.com/docs)
- [Decap CMS](https://decapcms.org/docs)

## 🤝 Working with This Project (For AI Assistants)

### When Making Changes

1. **Read First**: Always read relevant files before editing
2. **Preserve Structure**: Maintain existing patterns and conventions
3. **Type Safety**: Ensure TypeScript types are correct
4. **Test Locally**: Verify changes work with `npm run dev`
5. **Build Check**: Run `npm run build` before committing

### Code Style

- Use TypeScript for `.ts` and `.tsx` files
- Use semicolons consistently
- Use 2 spaces for indentation
- Use single quotes for strings in JS/TS
- Follow existing naming conventions

### Git Workflow

- Write clear, descriptive commit messages
- Reference issue numbers when applicable
- Keep commits focused and atomic
- Test builds before pushing

### Documentation

- Update README.md for user-facing changes
- Update CLAUDE.md for architecture changes
- Add JSDoc comments for complex functions
- Keep code self-documenting when possible

## 🎓 Learning Path for New Contributors

1. **Understand Astro**: Read Astro documentation and tutorial
2. **Learn Content Collections**: Essential for blog functionality
3. **Explore shadcn/ui**: Understand component patterns
4. **Review Tailwind**: Familiarize with utility classes
5. **Try Decap CMS**: Access `/admin` to see CMS interface

## 🚨 Important Notes for AI Assistants

### Critical Configuration Files
1. **tailwind.config.mjs**: Must include complete color palette. Empty `colors: {}` causes build errors.
2. **astro.config.mjs**: Contains site URL, integrations, and output mode. Update site URL before deployment.
3. **src/styles/globals.css**: Defines CSS variables that must be mapped in Tailwind config.

### Performance Optimization
- Avoid unnecessary React hydration: Use plain HTML/CSS for static content
- Only use `client:*` directives when interactivity is required
- Example: Homepage uses styled `<a>` tags instead of React `<Button>` components

### SEO Best Practices
- Sitemap is auto-generated via `@astrojs/sitemap` integration
- Update `site` URL in `astro.config.mjs` before deployment
- Use semantic HTML (proper heading hierarchy, anchor tags for links)
- robots.txt included to guide search engines

### Build Verification Checklist
Before committing changes, verify:
```bash
npm run build        # Must complete without errors
npm run astro check  # Must show 0 errors, 0 warnings
```

Expected build output:
- 3 pages generated (index, blog, blog post)
- Sitemap files created in dist/
- No TypeScript errors

### Common Pitfalls
1. **Don't** use empty objects in Tailwind config (`colors: {}`)
2. **Don't** wrap anchor tags in buttons for navigation
3. **Don't** forget `client:load` when React components need interactivity
4. **Do** test builds locally before pushing
5. **Do** update documentation when making architectural changes

---

**Last Updated**: 2025-11-05
**Project Version**: 0.0.1
**Maintained By**: Yoga Tung
