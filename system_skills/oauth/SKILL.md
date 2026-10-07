---
name: "oauth-integration"
description: >
  Guidelines for implementing Third-Party (3P) OAuth flows with external non-Google services (e.g., GitHub, Discord, Strava, Spotify, Slack, etc.) in the AI Studio preview environment. Use when the user requests third-party OAuth, login with external services, or popup-based authentication. Covers iframe constraints, cookie configuration, and redirect URI setup.
---

# OAuth Integration Guidelines

When implementing third-party OAuth flows (e.g., Discord, Strava, GitHub,
Spotify, Slack) in the AI Studio preview environment, follow these guidelines
carefully. The preview runs in an **iframe** with cross-origin restrictions
requiring specific handling.

## Critical: AI Studio Preview Environment Constraints

> [!CAUTION]
> The AI Studio preview runs inside an **iframe** and will NOT work if opened
> directly in a popup window. OAuth popups **must** open the OAuth provider's
> authorization URL directly—never the container's own routes.

## 1. Use Popup-Based OAuth Flow (Provider URL Directly)

**Do NOT use redirect-based OAuth** (`signInWithRedirect` patterns). Use a popup
that opens the **OAuth provider's URL directly**.

```tsx
const handleConnect = async () => {
  try {
    const response = await fetch('/api/auth/url');
    const { url } = await response.json();
    const authWindow = window.open(url, 'oauth_popup', 'width=600,height=700');
  } catch (error) {
    console.error('OAuth error:', error);
  }
};
```

## 2. Cookie Configuration for Iframe Context

```ts
cookie: {
  secure: true,      // Required for SameSite=None
  sameSite: 'none',  // Required for cross-origin iframe
  httpOnly: true,    // Security best practice
}
```
