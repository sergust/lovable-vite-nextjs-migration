# Migration Script: Lovable (Vite) → Next.js

🚀 **Automated migration script to seamlessly convert your Vite-based projects to Next.js with minimal manual intervention.**

This script follows the official [Next.js migration guide](https://nextjs.org/docs/app/guides/migrating/from-vite) and automates all the tedious setup steps, allowing you to focus on what matters most - building your application.

## ✨ Features

- 📦 **Automatic Next.js installation** and configuration
- 🏗️ **Creates Next.js App Router structure** (root layout, pages)
- 📝 **Updates TypeScript configuration** (preserves your existing settings)
- 🖼️ **Handles image import migration** with helper utilities
- 🔐 **Migrates environment variables** (VITE_ → NEXT_PUBLIC_)
- 📋 **Updates package.json scripts** for Next.js commands
- 🧹 **Provides cleanup utilities** to remove Vite artifacts
- 📚 **Generates comprehensive migration guides** for manual steps

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
- Node.js (v16 or higher)
- A Vite-based React project
- npm or yarn package manager

### Installation & Usage

1. **Download the migration script** to your project root:
   ```bash
   curl -O https://raw.githubusercontent.com/yourusername/lovable-vite-nextjs-migration/main/migrate-to-nextjs.js
   ```

2. **Run the migration**:
   ```bash
   node migrate-to-nextjs.js
   ```

3. **Start your Next.js application**:
   ```bash
   npm run dev
   ```

4. **Open your browser** to [http://localhost:3000](http://localhost:3000)

## 📋 What the Script Does

### Automated Steps ✅

1. **Installs Next.js dependency** (`next@latest`)
2. **Creates `next.config.mjs`** with SPA configuration
3. **Updates `tsconfig.json`** with Next.js-compatible settings
4. **Creates root layout** (`src/app/layout.tsx`) from your `index.html`
5. **Sets up entrypoint page** (`src/app/[[...slug]]/page.tsx`) with client-side rendering
6. **Creates image import helper** (`src/utils/imageHelper.ts`)
7. **Migrates environment variables** (renames VITE_ prefix to NEXT_PUBLIC_)
8. **Updates package.json scripts** (dev, build, start commands)
9. **Updates .gitignore** with Next.js-specific entries

### Generated Files 📄

After migration, you'll find these helpful files:
- `MIGRATION_SUMMARY.md` - Complete overview of changes and next steps
- `ENV_MIGRATION_GUIDE.md` - Guide for updating environment variable usage
- `cleanup-vite.js` - Script to remove Vite artifacts (optional)

## 🛠️ Manual Steps Required

While the script automates most of the migration, some manual updates are needed:

### 1. Update Image Imports
```javascript
// Before (Vite)
import logo from './logo.png'
<img src={logo} />

// After (Next.js)
import logo from './logo.png'
<img src={logo.src} />

// Or use the helper
import { getImageSrc } from './utils/imageHelper'
<img src={getImageSrc(logo)} />
```

### 2. Update Environment Variables in Code
```javascript
// Replace these in your code:
import.meta.env.MODE → process.env.NODE_ENV
import.meta.env.PROD → process.env.NODE_ENV === 'production'
import.meta.env.DEV → process.env.NODE_ENV !== 'production'
import.meta.env.SSR → typeof window !== 'undefined'
```

## 🧹 Cleanup (Optional)

After verifying everything works, clean up Vite artifacts:
```bash
node cleanup-vite.js
```

This removes:
- `main.tsx`, `index.html`, `vite-env.d.ts`
- `tsconfig.node.json`, `vite.config.ts`
- Vite dependencies from package.json

## 🔄 Migration Strategy

The script initially sets up Next.js as a **Single Page Application (SPA)** to minimize breaking changes. This approach:

- ✅ Keeps your existing routing logic intact
- ✅ Maintains client-side behavior you're used to
- ✅ Reduces migration complexity and conflicts
- ✅ Allows incremental adoption of Next.js features

### Future Optimizations

Once migrated, you can gradually adopt Next.js features:
- 🔄 **Migrate to Next.js App Router** for automatic code splitting
- 🖼️ **Use Next.js Image component** for automatic optimization
- ⚡ **Implement Server-Side Rendering** where beneficial
- 🎨 **Add Next.js font optimization** with `next/font`

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

**Made with ❤️ to simplify your migration journey from Vite to Next.js**
