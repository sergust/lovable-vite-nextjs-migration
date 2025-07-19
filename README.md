# Migration Script: Lovable (Vite) → Next.js

🚀 **Comprehensive automated migration script to seamlessly convert Lovable/Vite-based projects to Next.js with professional development setup.**

This enhanced script follows the official [Next.js migration guide](https://nextjs.org/docs/app/guides/migrating/from-vite) and goes beyond basic migration to set up a complete modern development environment with code quality tools.

## ✨ Enhanced Features

- 📦 **Complete dependency management** - Next.js + Prettier + ESLint
- 🧹 **Smart cleanup** - Removes conflicting lockfiles and Vite artifacts
- 🎨 **Code quality setup** - Prettier formatting with Angular-style rules
- 🔍 **Enhanced ESLint** - Next.js optimized rules with Prettier integration
- 🏗️ **Intelligent component detection** - Automatically finds and migrates your main components
- 📝 **Advanced TypeScript config** - Path aliases (@/*) and strict type checking
- 🖼️ **Robust image handling** - TypeScript-safe image import helpers
- ⚙️ **Tailwind compatibility** - Fixes ES module imports automatically
- 🔐 **Environment migration** - Complete VITE_ → NEXT_PUBLIC_ conversion
- 📋 **Professional scripts** - Development, build, lint, and format commands
- 🔧 **TypeScript fixes** - Resolves common interface and type issues

## 🎯 Why Use This Script?

### Benefits of Next.js over Vite
- **Faster initial page loads** with Server-Side Rendering (SSR)
- **Automatic code splitting** built into the router
- **Eliminates network waterfalls** with optimized data fetching
- **Built-in optimizations** for images, fonts, and scripts
- **Middleware support** for authentication and experimentation
- **Better SEO** with server-side rendering capabilities

## 🚀 Quick Start

### Prerequisites
- Node.js (v18 or higher)
- A Lovable/Vite-based React project
- npm package manager

### Installation & Usage

1. **Download the migration script** to your project root:
   ```bash
   curl -O https://raw.githubusercontent.com/sergust/lovable-vite-nextjs-migration/main/migrate-to-nextjs.js
   ```

2. **Run the migration**:
   ```bash
   node migrate-to-nextjs.js
   ```

3. **Start your Next.js application**:
   ```bash
   npm run dev
   ```

4. **Format your code** (optional):
   ```bash
   npm run format
   ```

5. **Open your browser** to [http://localhost:3000](http://localhost:3000)

## 📋 What the Script Does

### Automated Steps ✅

**Environment Setup:**
0. **Cleans conflicting lockfiles** from parent directories
1. **Installs dependencies** (Next.js + Prettier + ESLint configs)
2. **Creates Prettier configuration** with professional formatting rules

**Next.js Migration:**
3. **Creates `next.config.mjs`** with SPA export configuration
4. **Updates `tsconfig.json`** with path aliases (@/*) and Next.js settings
5. **Updates ESLint configuration** with Prettier integration and Next.js rules

**Project Structure:**
6. **Creates root layout** (`src/app/layout.tsx`) from your `index.html` metadata
7. **Creates entrypoint page** with intelligent component detection from Lovable structure
8. **Creates typed image helper** (`src/utils/imageHelper.ts`) with TypeScript support

**Code Quality & Cleanup:**
9. **Fixes Tailwind config** ES module imports (tailwindcss-animate)
10. **Removes Vite artifacts** (main.tsx, App.tsx, vite.config.ts, etc.)
11. **Migrates environment variables** (VITE_ → NEXT_PUBLIC_)
12. **Updates package.json scripts** with lint, format, and build commands
13. **Updates .gitignore** with Next.js-specific entries
14. **Fixes TypeScript interfaces** (converts empty interfaces to type aliases)

### Generated Files 📄

After migration, you'll find these helpful files:
- `MIGRATION_SUMMARY.md` - Complete overview with all steps and available scripts
- `ENV_MIGRATION_GUIDE.md` - Environment variable migration guide
- `.prettierrc` & `.prettierignore` - Code formatting configuration
- `cleanup-vite.js` - Legacy cleanup script (most cleanup done automatically)

### New Scripts Available 🛠️

```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run start        # Start production server
npm run lint         # Check for linting issues
npm run lint:fix     # Auto-fix linting issues
npm run format       # Format all files with Prettier
npm run format:check # Check if files are formatted
```

## 🛠️ Manual Steps (Minimal)

The enhanced script automates most migration tasks, but some manual updates may be needed:

### 1. Environment Variables in Code (If Used)
```javascript
// Replace these in your code if you use them:
import.meta.env.MODE → process.env.NODE_ENV
import.meta.env.PROD → process.env.NODE_ENV === 'production'
import.meta.env.DEV → process.env.NODE_ENV !== 'production'
import.meta.env.SSR → typeof window !== 'undefined'
```

### 2. Image Imports (Rare Cases)
Most image imports work automatically, but if you encounter issues:
```javascript
// Use the provided helper
import { getImageSrc } from '@/utils/imageHelper'
<img src={getImageSrc(logo)} />

// Or direct path for public assets
<img src="/logo.png" /> // if file is at public/logo.png
```

### 3. Component Path Updates (If Needed)
The script automatically detects common Lovable component structures, but you may need to update imports:
```javascript
// Update relative imports to use new alias
import Button from '@/components/ui/button'
```

## 🧹 Post-Migration Workflow

### 1. Test Your Application
```bash
npm run dev
```
Open: http://localhost:3000

### 2. Code Quality Check
```bash
npm run format      # Format all code with Prettier
npm run lint        # Check for any remaining issues
npm run build       # Test production build
```

### 3. Verify Migration Success
- ✅ Application loads at localhost:3000
- ✅ No console errors in browser
- ✅ All components render correctly
- ✅ Tailwind styles work properly
- ✅ Images load correctly

### 4. Optional: Review Changes
- Check `MIGRATION_SUMMARY.md` for detailed breakdown
- Review formatted code changes
- Verify TypeScript compilation

## 🔄 Migration Strategy

The enhanced script sets up Next.js as a **Single Page Application (SPA)** with professional development tools to minimize breaking changes. This approach:

- ✅ Preserves your existing Lovable component structure
- ✅ Maintains client-side behavior you're familiar with
- ✅ Reduces migration complexity and potential conflicts
- ✅ Provides immediate code quality improvements
- ✅ Sets up foundation for gradual Next.js feature adoption

### Intelligent Component Detection
The script automatically detects common Lovable project structures:
- `src/pages/Index.tsx` (primary detection)
- `src/pages/index.tsx` 
- `src/components/Index.tsx`
- `src/App.tsx` (fallback)

### Future Optimizations
Once migrated, gradually adopt Next.js features:
- 🔄 **Migrate to server components** for better performance
- 🖼️ **Use Next.js Image component** for automatic optimization  
- ⚡ **Implement Server-Side Rendering** where beneficial
- 🎨 **Add Next.js font optimization** with `next/font`
- 📊 **Add bundle analysis** with `@next/bundle-analyzer`

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

### Development
1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Troubleshooting

### Common Issues

**TypeScript Error: "The 'files' list in config file 'tsconfig.json' is empty"**
- The script automatically fixes this, but if you encounter it, remove the empty `"files": []` array from your tsconfig.json

**ES Module vs CommonJS Issues**
- If you see `require is not defined`, your project uses ES modules. The script handles this automatically.

**Import Errors After Migration**
- Check that all image imports use `.src` property: `<img src={image.src} />`
- Verify environment variables are updated in your code

### Getting Help

- 📖 Check the generated `MIGRATION_SUMMARY.md` file
- 📚 Read the [Next.js Migration Guide](https://nextjs.org/docs/app/guides/migrating/from-vite)
- 🐛 Open an issue on GitHub if you encounter problems

## 🙏 Acknowledgments

- Built following the official [Next.js migration documentation](https://nextjs.org/docs/app/guides/migrating/from-vite)
- Inspired by the needs of developers migrating from Vite to Next.js
- Thanks to the Next.js and Vite communities for their excellent documentation

---

**Made with ❤️ to simplify your migration journey from Lovable to Next.js**
