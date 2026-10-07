---
name: pwa-integration
description: >
  Step-by-step instructions for building a new Progressive Web App (PWA) or
  integrating PWA compliance into a web application (Vite or Next.js) with
  offline capabilities, service workers, Web App Manifests, icon assets, and
  in-app install prompts. Use when building a new PWA or adding PWA support,
  offline capabilities, or installability to a web app.
---

# Progressive Web App (PWA) Integration Guidelines

This skill guides you through building a new Progressive Web App (PWA) or
integrating PWA capabilities into an existing web application in AI Studio.

## 1. Web App Manifest Standards

1.  `id`: Unique application identifier (`'/'`).
2.  `start_url`: Entry page (`'/'`).
3.  `scope`: Navigation scope (`'/'`).
4.  `name`: Full human-readable application title.
5.  `short_name`: Condensed title (≤ 12 characters).
6.  `display`: Set to `'standalone'`.
7.  `theme_color` & `background_color`.
8.  `icons`: Minimum 192x192 and 512x512 resolutions.

## 2. Next.js App Router Setup

Create `app/manifest.ts`:

```typescript
import type { MetadataRoute } from 'next';

export default function manifest(): MetadataRoute.Manifest {
  return {
    id: '/',
    name: 'My Application',
    short_name: 'App',
    description: 'Progressive web application.',
    start_url: '/',
    scope: '/',
    display: 'standalone',
    background_color: '#ffffff',
    theme_color: '#ffffff',
    icons: [
      { src: '/pwa-192x192.png', sizes: '192x192', type: 'image/png' },
      { src: '/pwa-512x512.png', sizes: '512x512', type: 'image/png' },
    ],
  };
}
```
