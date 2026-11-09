# Project notes

1. The root layout, `app/layout.tsx`, contains the `<html>` and `<body>` tags. Every page is rendered inside them.

2. `app/page.tsx` renders the page at `/`.

3. Put images and other static files in `public/`. Reference them from the site root: for example, `public/next.svg` is available at `/next.svg`. For images, the app can use Next.js's `Image` component with `src="/next.svg"`.

4. `tsconfig.json` configures TypeScript for the project, including type checking, module resolution, JSX, and which files TypeScript includes. It also sets up the `@/*` import alias.

5. `@/*` is an alias for paths from the project root (`./*`). For example, if a `components/Header.tsx` file exists, you can import it like this:

   ```tsx
   import Header from "@/components/Header";
   ```

6. `app/layout.tsx` imports `Geist` and `Geist_Mono` from `next/font/google`. Next.js fetches and optimizes these fonts during the build, then serves them as app assets so the browser does not need to request them from Google Fonts.

7. A `page.tsx` defines the UI for a route. A `layout.tsx` wraps the page and its nested routes, allowing shared UI and state to persist as you navigate. The root `app/layout.tsx` is required; nested layouts can be added for sections of the app.

8. Put a navbar that should appear on every page in the root `app/layout.tsx`, around `{children}`. A navbar shared only by a section can go in that section's nested layout.

9. `app/globals.css` contains global styles and imports Tailwind CSS. The root layout imports it with `import "./globals.css";`.

10. `AGENTS.md` provides instructions and project-specific guidance to AI coding agents. It is not needed to run the app; Next.js and the browser do not use it as application code.
