---
name: "real-time-and-multi-user"
description: >
  Guidelines for implementing real-time features, WebSockets, and collaborative
  canvases. Use when the app requires chat, live collaboration, multiplayer games,
  or notifications. Covers server-authoritative state, event-based communication,
  and canvas library selection (Konva, Fabric.js).
---

# Real-Time & Multi-User Guidelines

## Critical Rule: No Simulations

When building applications with multi-user or real-time features, **you MUST use
real infrastructure**:

Feature Type       | Required Implementation
------------------ | ------------------------------------------
Chat / Messaging   | WebSockets with server-side state
Live Collaboration | WebSockets with server-side state
Multiplayer Games  | WebSockets with server-authoritative state
Notifications      | Push notifications or WebSocket events

## Architecture Principles

### 1. Server as Source of Truth
The server maintains authoritative state. Clients are views of that state.

### 2. Event-Based Communication
`Client A sends action → Server processes → Server broadcasts to all clients`

### 3. Canvas Library Selection
- **Default choice**: Konva with `react-konva` (state-driven matches server-as-source-of-truth)
- **Advanced features**: Fabric.js v6+
