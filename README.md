# 🧱 ALLBOOKPRIEST Monorepo  
> Modern Vue 2 + Vite + Turborepo Setup

![Vite](https://img.shields.io/badge/Vite-6.x-blue?logo=vite)
![Vue](https://img.shields.io/badge/Vue-2.7-green?logo=vue.js)
![Turbo](https://img.shields.io/badge/TurboRepo-2.x-black?logo=vercel)
![License](https://img.shields.io/badge/license-MIT-lightgrey)
![Status](https://img.shields.io/badge/Status-Active-success)

---

## 📖 Overview

**ALLBOOKPRIEST Monorepo** is a full-featured **multi-package monorepo** powered by  
[Turborepo](https://turbo.build/), [Vite](https://vitejs.dev/), and [Vue 2](https://v2.vuejs.org/).  

It includes:
- 📦 **artiqui** → A reusable Vue 2 component library.  
- 📘 **book_priest** → The main app consuming artiqui.  

This monorepo structure allows for efficient builds, dependency sharing, and parallel development.

---

## 🧩 Tech Stack

| Tool | Purpose |
|------|----------|
| ⚡ **Vite** | Lightning-fast bundler & dev server |
| 🧱 **Turborepo** | Monorepo orchestration & caching |
| 🧩 **Vue 2 + vite-plugin-vue2** | Legacy Vue app framework |
| 🎨 **Sass** | CSS preprocessor for styling |
| 🧹 **Prettier + ESLint** | Code formatting & linting |
| 🧠 **Husky + Lint-staged** | Git hooks for quality |
| 📅 **Flatpickr** | Beautiful date picker |

---

## 🗂️ Repository Structure

```
ALLBOOKPRIEST-MONOREPO/
│
├── packages/
│   ├── artiqui/          # Vue 2 component library
│   └── book_priest/      # Main app using artiqui
│
├── turbo.json            # Turborepo configuration
├── package.json          # Root package manager file
└── README.md             # This file
```

---

## ⚙️ Requirements

Before starting, make sure you have:
- 🟢 **Node.js 18+**
- 🔵 **npm 9+**
- 🧭 **GitHub CLI** (optional for pushing from Codespaces)

---

## 🚀 Getting Started

### 1️⃣ Clone the repo

```bash
git clone https://github.com/manishkenguva37/ALLBOOKPRIESTREPOOOFORLERNAMONOREPO.git
cd ALLBOOKPRIESTREPOOOFORLERNAMONOREPO
```

### 2️⃣ Clean install dependencies

```bash
rm -rf node_modules packages/*/node_modules package-lock.json
npm install
```

---

## 🧠 Development

To run **all apps simultaneously** (both `artiqui` & `book_priest`):

```bash
npm run dev:all
```

Turborepo runs each workspace in **parallel** with shared caching.

### Individual package development

#### Run only `artiqui`:
```bash
cd packages/artiqui
npm run dev
```

#### Run only `book_priest`:
```bash
cd packages/book_priest
npm run dev
```

Once running, open:
```
http://localhost:5173
```

---

## 🏗️ Build for Production

To build all packages at once:

```bash
npm run build
```

Or individually:
```bash
# For artiqui
cd packages/artiqui
npm run build

# For book_priest
cd packages/book_priest
npm run build
```

Built files are output to each package’s `/dist` folder.

---

## 🧹 Code Quality

Precommit checks & formatting run automatically:
```bash
npm run lint
npm run format
```

When committing:
- Husky triggers lint-staged
- Prettier formats code automatically

---

## 🌐 Git & GitHub Setup

If pushing from GitHub Codespaces, unset the default token first:

```bash
unset GITHUB_TOKEN
gh auth login
```

Then push your branch:
```bash
git push --set-upstream origin mono-repo-turbo
```

---

## 🖼️ Screenshot

> Add your preview under `/docs/screenshot.png`

![Preview](./docs/screenshot.png)

---

## 🧩 Turbo Configuration Example

```jsonc
{
  "$schema": "https://turbo.build/schema.json",
  "tasks": {
    "build": {
      "outputs": ["dist/**"]
    },
    "dev": {
      "cache": false,
      "persistent": true,
      "dependsOn": ["^build"]
    }
  }
}
```

---

## 🧪 Package Scripts Overview

| Command | Location | Description |
|----------|-----------|-------------|
| `npm run dev` | book_priest | Start dev server |
| `npm run build` | book_priest | Build production app |
| `npm run dev` | artiqui | Build library in watch mode |
| `npm run build` | artiqui | Compile production build |
| `npm run dev:all` | root | Run all dev tasks via Turbo |

---

## 🧱 Folder Notes

### 📦 `packages/artiqui`
Reusable Vue 2 component library built with Vite.  
Exports components to be used by `book_priest`.

### 📘 `packages/book_priest`
Main Vue 2 application that imports components from `artiqui`.

---

## 🧑‍💻 Author

**👤 Manish Kenguva**  
📍 GitHub → [@manishkenguva37](https://github.com/manishkenguva37)  
📧 Email → manishkenguva37@gmail.com  

---

## 🪪 License

**MIT License**

You are free to modify and distribute this code as long as attribution is provided.

---

## 💡 Tips

- If Turbo skips builds → ensure `"tasks"` field (not `"pipeline"`) in `turbo.json`
- If `vite-plugin-vue2` fails → downgrade Vite to `4.x`
- Use `--legacy-peer-deps` when npm conflicts appear

---

## 📷 Project Structure Visual

![Monorepo Diagram](https://raw.githubusercontent.com/vercel/turbo/main/examples/images/turborepo-diagram.png)
