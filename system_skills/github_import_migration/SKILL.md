---
name: "github-import-migration"
description: >-
  Execute-First migration for GitHub repositories imported into AI Studio.
  Triages projects and routes to the appropriate self-contained migration
  reference. Supports Web (Node.js) and Android (Kotlin/Compose) runtimes.
---

## Core Philosophy
Attempt the simplest possible refactoring to make the app boot in AI Studio.
Strip non-essential blockers → Mock with in-memory stubs if boot-critical → Rewrite as last resort.

## Project Triage
- Category A: Native Android (build.gradle, .kt/.java) → references/android.md
- Category B: Cross-Platform Mobile (Flutter, React Native) → Create web app
- Category C: Web / Node.js (package.json, Python, Go, Ruby) → references/web.md
- Category D: Unsupported (C++, Unity, Electron) → Create web app replicating core logic
