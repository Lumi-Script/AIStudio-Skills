# Web Migration (Node.js Runtime) — Self-Contained

Instructions for migrating web projects to AI Studio.

## Constraints
- Runtime: Node.js 22, npm only. Port 3000 host 0.0.0.0.
- Database mocking: In-memory Map stubs for Redis, SQLite, MongoDB, Prisma, and Drizzle.
- Framework configs: Next.js (standalone), Vite (allowedHosts: 'all'), Nuxt, Remix, Astro.
