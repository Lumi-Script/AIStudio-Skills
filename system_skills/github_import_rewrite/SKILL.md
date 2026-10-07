---
name: "github-import-rewrite"
description: >-
  Cross-framework rewrite for GitHub repositories imported into AI Studio.
  Rewrites the imported project from its source framework to a different
  target framework while preserving core features and business logic.
---

You are asked to rewrite an imported GitHub project to a **target runtime** and
**target framework** specified in the user's message. The container has already
been provisioned with the correct target runtime — you do not need to detect or
configure it. Focus on building a new app in the target framework.

## CRITICAL RULES

1.  **DO NOT delete original source files until the new app compiles.** Build
    the entire new app first, verify with `compile_applet`, THEN clean up.
2.  Port 3000 on host `0.0.0.0` is the ONLY accessible port (web targets).
3.  npm only. No yarn, pnpm, bun.
4.  Preserve the app's existing features — do NOT add features that didn't
    exist.
5.  Do NOT restyle the application.

--------------------------------------------------------------------------------

## Step 1: Analyze Source Project

Read the full project structure. Understand before writing:

1.  Data models and schemas
2.  UI screens and components — the 3–5 most important features
3.  API routes and endpoints
4.  State management patterns
5.  External services (databases, APIs, auth)

--------------------------------------------------------------------------------

## Step 2: Build New App

The user's message tells you the target framework. Create the new project in the
root directory alongside the original files.

### Web Targets (React / Next.js / Angular)

**Runtime constraints:**

-   Node.js 22, npm only
-   Dev server MUST listen on port 3000, host `0.0.0.0`
-   `npm run dev` must start the app
-   Filesystem is ephemeral — no persistent local storage
-   HTTP(S) outbound only, no direct TCP to databases

**Project setup:**

-   Create `package.json` with correct deps and `"dev"` script
-   Set up TypeScript configuration
-   Standard directory structure (`src/`, `public/`, etc.)

**Framework-specific dev scripts:**

-   React (Vite): `"dev": "vite --host 0.0.0.0 --port 3000"`
-   Next.js: `"dev": "next dev -p 3000 -H 0.0.0.0"`
-   Angular: `"dev": "ng serve --host 0.0.0.0 --port 3000"`

--------------------------------------------------------------------------------

## Step 3: Verify

Run `compile_applet`. If it fails:

1.  Read the error carefully
2.  Fix the specific issue
3.  Re-run `compile_applet`
4.  Repeat up to 3 times

If it fails 3 times: STOP and explain the error to the user.

--------------------------------------------------------------------------------

## Step 4: Clean Up Original Files (AFTER successful compile)

**Only after `compile_applet` succeeds**, delete ALL original source files that
belong to the source framework. Keep only reusable static assets (images, fonts,
data files, LICENSE, README.md).
