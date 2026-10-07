---
name: applet-seo
description: >
  Configures advanced search engine optimization (SEO), OpenGraph
  social share cards, Twitter cards, and Schema.org structured data (JSON-LD)
  for web applications in AI Studio. Use when the user requests enhanced SEO,
  social sharing cards, or rich structured data.
---

# Applet SEO & Social Metadata Guidelines

This skill guides you through implementing search engine optimization (SEO),
tailored metadata, social sharing cards, and structured data in AI Studio web
applications.

## 1. Page Title & Meta Description

### Page Titles (`<title>` and `og:title`)

*   **Must be specific and branded**: Use a descriptive title matching the
    application's actual identity (e.g., `<title>MealPrep Pro – Weekly Meal
    Planner & Grocery List</title>`).
*   **Never use generic placeholders**: Avoid strings like `"AI App"`, `"React
    App"`, `"Vite App"`, `"Home"`, or `"My Application"`.
*   **Length guideline**: Keep titles between 30 and 60 characters for optimal
    search engine snippet rendering.

### Meta Descriptions (`<meta name="description">` and `og:description`)

*   **Accurate summary**: Summarize the core value proposition and key features
    in 1–2 compelling sentences.
*   **Length guideline**: Keep descriptions between 120 and 160 characters so
    they are not truncated in search result snippets.
*   **Call to action**: Include actionable phrasing (e.g., *"Plan your weekly
    recipes, generate grocery lists, and track nutrition with MealPrep Pro."*).

```html
<title>MealPrep Pro – Weekly Meal Planner & Grocery List</title>
<meta
  name="description"
  content="Plan your weekly recipes, generate smart grocery lists, and track daily nutrition with MealPrep Pro."
/>
```

--------------------------------------------------------------------------------

## 2. OpenGraph & Twitter Social Cards

Ensure links shared on social platforms (Slack, Discord, X/Twitter, LinkedIn,
Facebook, iMessage) generate rich visual cards:

### Standard OpenGraph Tags

```html
<meta property="og:type" content="website" />
<meta property="og:title" content="MealPrep Pro – Weekly Meal Planner & Grocery List" />
<meta
  property="og:description"
  content="Plan your weekly recipes, generate smart grocery lists, and track daily nutrition with MealPrep Pro."
/>
<meta property="og:site_name" content="MealPrep Pro" />
```

### Twitter / X Cards

```html
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:title" content="MealPrep Pro – Weekly Meal Planner & Grocery List" />
<meta
  name="twitter:description"
  content="Plan your weekly recipes, generate smart grocery lists, and track daily nutrition with MealPrep Pro."
/>
```

### Dynamic URL Resolution

When configuring canonical URLs (`og:url`, `<link rel="canonical">`):

*   In server-side / SSR contexts, utilize `process.env.APP_URL` if available.
*   In client-side React / SPA contexts, use `window.location.origin +
    window.location.pathname`.

--------------------------------------------------------------------------------

## 3. Schema.org Structured Data (JSON-LD)

For domain-specific applications, embed Schema.org structured data in a `<script
type="application/ld+json">` tag within the `<head>` or root component to enable
rich search snippets:

### Common Types:

*   **WebApplication / SoftwareApplication** (General utilities, calculators,
    productivity tools)
*   **Recipe** (Cooking and meal planning apps)
*   **Event** (Scheduling, ticketing, and calendar apps)
*   **Product** (E-commerce and shopping apps)
*   **HowTo / FAQPage** (Educational guides and tutorials)

### Example (WebApplication):

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "WebApplication",
  "name": "MealPrep Pro",
  "applicationCategory": "LifestyleApplication",
  "operatingSystem": "All",
  "description": "Plan your weekly recipes, generate smart grocery lists, and track daily nutrition.",
  "offers": {
    "@type": "Offer",
    "price": "0",
    "priceCurrency": "USD"
  }
}
</script>
```
