---
name: "image-generation"
description: >
  Use when the application needs to generate or update images — hero banners, illustrations, icons, backgrounds,
  avatars, product photos, or any visual asset. Covers image selection strategy
  (using tools vs assets vs placeholders) and runtime generation using Gemini
  models.
---

# Images

## Selection Strategy

Choose images that reinforce the app's purpose and visual identity.

-   **Important Assets (Hero images, etc.):** Use the `generate_image` tool to
    create these, especially if the request is specific. Aim for ~5 generated
    images per app or less. Use standard aspect ratios (16:9, 1:1, etc.) as
    detailed below in the prompt guidelines.
-   **Parallel Batching (Mandatory):** When an app requires visual assets,
    **audit all visual slots across the entire layout upfront** (hero, Bento
    cards, avatars, showcases) and **emit all `generate_image` tool calls in
    parallel within a single turn**.
-   **Prefer known assets:** Attempt to use official, high-quality, publicly
    accessible CDN URLs or well-known asset repositories for the rest of the
    images.
-   **Fallback:** If `generate_image` is unavailable or fails, use styled CSS
    fallback containers (e.g. subtle gradient mesh with domain SVG icon and
    title) or inline SVG.

## Implementation

Always use `<img>` elements with the following requirements:

-   **`referrerPolicy="no-referrer"`**: Required on every `<img>` tag to prevent
    broken images from referrer-restricted hosts.
-   **Generated Image Paths & `server.ts`**: `generate_image` saves files to
    `/src/assets/images/<name>_<timestamp>.jpg`. Reference this path as a URL
    string (`src="/src/assets/images/..."`) or import it only in client-side
    components.

```tsx
<img
  src="/src/assets/images/hero_banner_1742081234567.jpg"
  alt="Hero banner description"
  referrerPolicy="no-referrer"
/>
```

## Image Configuration

-   `aspectRatio`: Supported values are "1:1", "3:4", "4:3", "9:16", "16:9", "1:4", "1:8", "4:1", "8:1".
