# Vue.js Portfolio Project - Copilot Instructions

## Project Overview

This is a Vue.js web application built with:
- **Vue 3** - Progressive JavaScript framework
- **Vite** - Lightning-fast build tool
- **Vue Router 5** - Official router for Vue.js
- **Yarn** - Package manager (yarn.lock is used)

## Project Setup Summary

✅ **Scaffolding**: Created with `npm create vite@latest . --template vue`
✅ **Package Manager**: Yarn (yarn.lock configured)
✅ **Router Setup**: Vue Router 5 installed and configured
✅ **Home View**: Created with "Hello World" greeting page
✅ **Build**: Successfully compiles without errors
✅ **Dependencies**: Installed with `yarn install --ignore-engines`

## Key Files

- `src/main.js` - Application entry point with router integration
- `src/App.vue` - Root component with RouterView
- `src/router/index.js` - Vue Router configuration
- `src/views/HomeView.vue` - Home page displaying "Hello World"
- `package.json` - Project dependencies and scripts
- `yarn.lock` - Yarn dependency lock file
- `vite.config.js` - Vite configuration

## Development Commands

```bash
# Install dependencies
yarn install

# Start development server (with hot reload)
yarn dev

# Build for production
yarn build

# Preview production build
yarn preview
```

## Development Server

The development server runs on `http://localhost:5173` and features hot module reloading (HMR) for instant updates.

## Notes

- Node.js 20.15.0 is currently installed (Vite prefers 20.19+ but works with compatibility flag)
- All dependencies installed with `--ignore-engines` flag due to Node version
- Project is ready for further development and component additions
