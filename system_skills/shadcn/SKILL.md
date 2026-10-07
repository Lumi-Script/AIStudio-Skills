---
name: shadcn-ui
description: >
  Guidelines for using shadcn/ui components and CLI. Use ONLY when the user
  requests shadcn or shadcn/ui. Covers initialization, adding components,
  community registries, and theming.
---

# shadcn CLI Usage (If Using shadcn)

Initialize shadcn (if not already done). **Always use `--defaults` (or `-d`) to
skip interactive prompts**:

```bash
npx shadcn@latest init --defaults
```

Add components as needed:

```bash
npx shadcn add button card dialog sheet
```

## Theming
shadcn uses CSS variables for theming:
- Semantic classes: `bg-primary`, `text-foreground`, `bg-destructive`
- Dark mode via `.dark` class on `<html>`
