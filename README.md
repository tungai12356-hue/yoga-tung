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

## 📚 Learn More

- [Astro Documentation](https://docs.astro.build)
- [React Documentation](https://react.dev)
- [shadcn/ui Documentation](https://ui.shadcn.com)
- [Decap CMS Documentation](https://decapcms.org/docs)
- [Netlify Documentation](https://docs.netlify.com)

## 🎯 Future Plans

This website is designed to replace a static page website with:
- Dynamic content management
- Blog functionality
- Easy content updates through CMS
- Modern, responsive design
- Fast performance and SEO optimization

## 📄 License

This project is open source and available under the [MIT License](LICENSE).