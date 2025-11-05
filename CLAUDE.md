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
│   └── images/uploads/         # Media uploads from CMS
│
├── src/
│   ├── components/
│   │   └── ui/                 # Reusable UI components
│   │       ├── button.tsx      # shadcn/ui Button
│   │       └── bento-grid.tsx  # Magic UI Bento Grid
│   │
│   ├── content/                # Content collections
│   │   ├── blog/               # Blog posts (Markdown)
│   │   ├── pages/              # Static pages (Markdown)
│   │   └── config.ts           # Zod schemas for content
│   │
│   ├── layouts/
│   │   └── Layout.astro        # Main layout wrapper
│   │
│   ├── lib/
│   │   └── utils.ts            # Utility functions (cn, etc.)
│   │
│   ├── pages/                  # File-based routing
│   │   ├── index.astro         # Homepage
│   │   ├── blog.astro          # Blog listing
│   │   └── blog/
│   │       └── [...slug].astro # Dynamic blog post pages
│   │
│   └── styles/
│       └── globals.css         # Global styles + Tailwind
│
├── astro.config.mjs            # Astro configuration
├── tailwind.config.mjs         # Tailwind configuration
├── tsconfig.json               # TypeScript configuration
├── netlify.toml                # Netlify deployment config
└── package.json                # Dependencies and scripts
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

### Issue: React component not interactive
**Cause**: Missing `client:*` directive
**Solution**: Add `client:load` or appropriate directive

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
  "@astrojs/tailwind": "^6.0.2",
  "react": "^18.3.1",
  "react-dom": "^18.3.1"
}
```

### UI Dependencies
```json
{
  "tailwindcss": "^3.4.0",
  "class-variance-authority": "latest",
  "clsx": "latest",
  "tailwind-merge": "latest",
  "lucide-react": "latest",
  "framer-motion": "latest"
}
```

### Dev Dependencies
```json
{
  "@types/react": "^18.3.12",
  "@types/react-dom": "^18.3.1",
  "typescript": "^5.6.3"
}
```

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

---

**Last Updated**: 2025-11-05
**Project Version**: 0.0.1
**Maintained By**: Yoga Tung
