---
name: gemini-interactions-api
description: >
  Provides coding patterns for the @google/genai TypeScript SDK. Covers using
  the Interactions API for the Antigravity agent, Deep Research agent, Omni
  models (Omni Flash), and general model capabilities (text, image, speech
  generation), as well as other specialized APIs for music (Lyria) and
  real-time audio (Live API) in a server-side context.
---

# Gemini Interactions API

## Prerequisites
`@google/genai` >= 2.4.0

## Calling Interactions API
- Always call Interactions API from server-side code.
- Managed agents (antigravity-preview-09-2026, deep-research-preview-04-2026) and Omni models (gemini-omni-1.1-flash) can ONLY be invoked using ai.interactions.create().
- response_modalities strictly requires lowercase literals: 'text', 'image', 'audio', 'video'.

```ts
import { GoogleGenAI } from "@google/genai";

const ai = new GoogleGenAI({ apiKey: process.env.GEMINI_API_KEY });

const interaction = await ai.interactions.create({
  agent: "antigravity-preview-09-2026",
  input: "Write a python script and execute it.",
  environment: "remote",
}, { timeout: 300000 });

console.log(interaction.output_text);
```
