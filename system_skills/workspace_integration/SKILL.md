---
name: workspace-integration
description: >-
  Integrate 1P Google Workspace APIs (Google Drive, Docs, Sheets, Slides, Calendar, Gmail, Chat, Meet, Forms, Classroom, Tasks, Keep, People, Picker) into the application. Use when the user wants to authenticate with Google Workspace to read, write, or search Google Workspace data. Requires OAuth configuration via the set_up_oauth and remove_oauth tools.
---

# Google Workspace Integration

This skill guides you through integrating Google Workspace APIs into the application.

## Step 1: Configure OAuth
- Determine desired scopes with scope minimization (e.g. documents.readonly, spreadsheets.readonly).
- Use set_up_oauth tool for credentials.

## Authentication & UI
- Client-side token authentication using Firebase Auth GoogleAuthProvider.
- Cache access token in memory (never localStorage).
- Explicit user confirmation dialog before any mutating or destructive API operation.
