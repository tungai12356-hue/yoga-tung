# Yoga Tung - Personal Website

A modern personal website built with cutting-edge web technologies, designed to replace a static page website with a fully-featured, content-managed site.

## 🎉 Project Status

✅ **Build Status**: All systems operational
✅ **Type Safety**: 0 errors, 0 warnings
✅ **Production Ready**: Successfully builds and deploys
✅ **SEO Optimized**: Sitemap, robots.txt, and semantic HTML

**Latest Updates** (2025-11-05):
- Fixed critical Tailwind CSS configuration
- Added sitemap generation for SEO
- Optimized homepage bundle size
- Added favicon and robots.txt
- Complete shadcn/ui color theme integration

## 🚀 Tech Stack

- **[Astro 5.x](https://astro.build/)** - Modern static site generator with best-in-class performance
- **[Vite 5.x](https://vitejs.dev/)** - Included with Astro for lightning-fast development
- **[React 18](https://react.dev/)** - Interactive UI components with the latest React features
- **[shadcn/ui](https://ui.shadcn.com/)** - Beautiful, accessible component library built with Radix UI and Tailwind CSS
- **[Magic UI](https://magicui.design/)** - Animated components for enhanced user experience
- **[Decap CMS](https://decapcms.org/)** - Git-based content management system (formerly Netlify CMS)
- **[Tailwind CSS](https://tailwindcss.com/)** - Utility-first CSS framework
- **[TypeScript](https://www.typescriptlang.org/)** - Type-safe development

## 📦 Project Structure

```
/
├── public/
│   ├── admin/              # Decap CMS admin interface
│   │   ├── config.yml      # CMS configuration
│   │   └── index.html      # CMS entry point
│   ├── images/uploads/     # Media uploads folder
│   ├── favicon.svg         # Website icon
│   └── robots.txt          # Search engine rules
│
├── src/
│   ├── components/
│   │   └── ui/             # shadcn/ui and Magic UI components
│   │       ├── button.tsx
│   │       └── bento-grid.tsx
│   ├── content/
│   │   ├── blog/           # Blog posts (Markdown)
│   │   ├── pages/          # Content pages
│   │   └── config.ts       # Content collection schemas
│   ├── layouts/
│   │   └── Layout.astro    # Main layout template
│   ├── lib/
│   │   └── utils.ts        # Utility functions (cn helper)
│   ├── pages/
│   │   ├── blog/           # Blog routes
│   │   │   └── [...slug].astro
│   │   ├── blog.astro      # Blog listing page
│   │   └── index.astro     # Homepage
│   └── styles/
│       └── globals.css     # Global styles and Tailwind imports
│
├── .env.example            # Environment variables template
├── .gitignore              # Git ignore rules
├── .node-version           # Node.js version (20)
├── astro.config.mjs        # Astro configuration
├── CLAUDE.md               # AI assistant documentation
├── netlify.toml            # Netlify deployment configuration
├── package.json            # Dependencies
├── README.md               # This file
├── tailwind.config.mjs     # Tailwind CSS configuration
└── tsconfig.json           # TypeScript configuration
```

## 🛠️ Getting Started

### Prerequisites

- Node.js 20 or higher
- npm or pnpm

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd yoga-tung
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

4. Open your browser and navigate to `http://localhost:4321`

## 📝 Available Commands

| Command                   | Action                                           |
| :------------------------ | :----------------------------------------------- |
| `npm install`             | Installs dependencies                            |
| `npm run dev`             | Starts local dev server at `localhost:4321`      |
| `npm run build`           | Build your production site to `./dist/`          |
| `npm run preview`         | Preview your build locally, before deploying     |
| `npm run astro ...`       | Run CLI commands like `astro add`, `astro check` |

## 🎨 Using Decap CMS

Decap CMS provides a user-friendly interface for managing your content:

1. After deploying to Netlify, enable Netlify Identity and Git Gateway in your Netlify dashboard
2. Access the CMS at `https://your-site.netlify.app/admin`
3. Create and edit blog posts and pages through the visual editor

### Local CMS Development

To use Decap CMS locally:

1. Uncomment `local_backend: true` in `public/admin/config.yml`
2. Run `npx decap-server` in a separate terminal
3. Access the CMS at `http://localhost:4321/admin`

## 🎨 Adding More shadcn/ui Components

This project is set up to easily add more shadcn/ui components:

```bash
# Example: Add a Card component
# 1. Create the component file in src/components/ui/
# 2. Copy the component code from https://ui.shadcn.com
# 3. Adjust imports to use "@/lib/utils" -> "../../lib/utils"
```

Available component examples:
- Button (already included)
- Card, Badge, Dialog, Dropdown Menu, etc.

Visit [shadcn/ui](https://ui.shadcn.com/docs/components) for more components.

## 🎭 Magic UI Components

Magic UI components are included for enhanced animations:

- **Bento Grid** - Already included in `src/components/ui/bento-grid.tsx`
- More components available at [Magic UI](https://magicui.design/)

## 🔧 Configuration Files

### `astro.config.mjs`
Main Astro configuration with integrations:
- **React**: For interactive UI components
- **Tailwind CSS**: Utility-first styling (base styles disabled for shadcn/ui)
- **Sitemap**: Automatic sitemap generation for SEO
- **Site URL**: Configure your production domain here

### `tailwind.config.mjs`
Tailwind CSS configuration with complete shadcn/ui theme:
- **Dark mode**: Class-based dark mode support
- **Color system**: Full HSL color palette with CSS variables
- **Border radius**: Customizable radius system
- **Content paths**: Configured for all file types (.astro, .tsx, .md, etc.)

### `public/admin/config.yml`
Decap CMS configuration:
- **Backend**: Git Gateway with Netlify Identity
- **Collections**: Blog posts and pages
- **Media**: Stored in `public/images/uploads/`
- **Workflows**: Editorial workflow support

### `netlify.toml`
Netlify deployment settings:
- **Build command**: `npm run build`
- **Publish directory**: `dist`
- **Node version**: 20
- **Redirects**: SPA-style routing support

### `.env.example`
Template for environment variables:
- Copy to `.env` for local development
- Add your site URL and API keys as needed

## 🚀 Deployment to Netlify

### One-Click Deploy

Deploy directly to Netlify:

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start)

### Manual Deployment

1. Push your code to GitHub
2. Import your repository in Netlify
3. Configure build settings (should auto-detect from `netlify.toml`)
4. Enable Netlify Identity for CMS authentication
5. Enable Git Gateway for CMS content management

## ✨ Features

### Current Features
- ✅ Modern, responsive homepage with hero section
- ✅ Full-featured blog system with content collections
- ✅ Markdown-based content management
- ✅ Decap CMS integration for easy content editing
- ✅ shadcn/ui components (Button, utilities)
- ✅ Magic UI components (Bento Grid)
- ✅ Tailwind CSS with complete dark mode support
- ✅ TypeScript for type safety (0 errors, 0 warnings)
- ✅ **SEO optimized**: Sitemap generation, robots.txt, semantic HTML
- ✅ **Performance optimized**: Minimal JavaScript, optimal bundle size
- ✅ Fast static site generation with Astro
- ✅ Netlify deployment ready
- ✅ **Custom favicon**: Purple gradient "Y" branding
- ✅ **Build verified**: Production builds tested and working

### Planned Features
- 🔄 Portfolio/Projects section
- 🔄 Contact form
- 🔄 Newsletter subscription
- 🔄 Search functionality
- 🔄 RSS feed
- 🔄 Social media integration
- 🔄 Analytics integration
- 🔄 Progressive Web App (PWA) features

## 🐛 Troubleshooting

### Build Errors

**Problem**: TypeScript errors during build
```bash
npm run build
```
**Solution**: Run `npm run astro check` to see detailed type errors.

**Problem**: `border-border` class does not exist error
**Solution**: This was fixed in the latest update. The `tailwind.config.mjs` now includes all shadcn/ui color definitions. If you still see this error, make sure you have the latest version with the complete colors configuration.

**Problem**: Tailwind CSS classes not working
**Solution**: Make sure `src/styles/globals.css` is imported in your layout and the content paths in `tailwind.config.mjs` are correct.

**Problem**: React components not rendering
**Solution**: Make sure to add `client:load` directive to React components in `.astro` files:
```astro
<Button client:load>Click me</Button>
```

### Development Server Issues

**Problem**: Port 4321 already in use
**Solution**: Kill the process or use a different port:
```bash
npm run dev -- --port 3000
```

## 📚 Learn More

### Official Documentation
- [Astro Documentation](https://docs.astro.build) - Learn about Astro features
- [React Documentation](https://react.dev) - Learn React fundamentals
- [shadcn/ui Documentation](https://ui.shadcn.com) - Browse available components
- [Decap CMS Documentation](https://decapcms.org/docs) - Configure your CMS
- [Netlify Documentation](https://docs.netlify.com) - Deployment guides

### Helpful Resources
- [Astro Blog Tutorial](https://docs.astro.build/en/tutorial/0-introduction/)
- [Tailwind CSS Cheat Sheet](https://nerdcave.com/tailwind-cheat-sheet)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html)
- [Git Workflow Guide](https://guides.github.com/introduction/flow/)

## 🎯 Project Goals

This website is designed to replace a static page website with:
- ✨ Dynamic content management through Decap CMS
- 📝 Blog functionality for sharing thoughts and updates
- 🎨 Modern, responsive design that works on all devices
- ⚡ Fast performance with static site generation
- 🔍 SEO optimization for better discoverability
- 🔄 Easy content updates without touching code
- 🚀 Automated deployments via Netlify
- 📱 Mobile-first approach

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 👤 Author

**Yoga Tung**

- Website: [Coming Soon]
- GitHub: [@tungai12356-hue](https://github.com/tungai12356-hue)

## 🙏 Acknowledgments

- [Astro](https://astro.build) - For the amazing framework
- [shadcn](https://twitter.com/shadcn) - For the beautiful UI components
- [Vercel](https://vercel.com) - For design inspiration
- [Netlify](https://netlify.com) - For excellent hosting and CMS tools