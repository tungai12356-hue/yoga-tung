# Yoga Tung - Personal Website

A modern personal website built with cutting-edge web technologies, designed to replace a static page website with a fully-featured, content-managed site.

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
│   └── images/uploads/     # Media uploads folder
├── src/
│   ├── components/
│   │   └── ui/             # shadcn/ui and Magic UI components
│   ├── content/
│   │   ├── blog/           # Blog posts (Markdown)
│   │   ├── pages/          # Content pages
│   │   └── config.ts       # Content collection schemas
│   ├── layouts/
│   │   └── Layout.astro    # Main layout template
│   ├── lib/
│   │   └── utils.ts        # Utility functions
│   ├── pages/
│   │   ├── blog/           # Blog routes
│   │   ├── blog.astro      # Blog listing page
│   │   └── index.astro     # Homepage
│   └── styles/
│       └── globals.css     # Global styles and Tailwind imports
├── astro.config.mjs        # Astro configuration
├── tailwind.config.mjs     # Tailwind CSS configuration
├── tsconfig.json           # TypeScript configuration
└── netlify.toml            # Netlify deployment configuration
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
Main Astro configuration with React and Tailwind integrations.

### `tailwind.config.mjs`
Tailwind CSS configuration with shadcn/ui theme variables.

### `public/admin/config.yml`
Decap CMS configuration for content collections.

### `netlify.toml`
Netlify deployment settings and build configuration.

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
- ✅ Tailwind CSS with dark mode support
- ✅ TypeScript for type safety
- ✅ SEO-friendly structure
- ✅ Fast static site generation with Astro
- ✅ Netlify deployment ready

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