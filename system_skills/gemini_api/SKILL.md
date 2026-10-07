---
name: "gemini-api"
description: >
  Provides model selection guidance and coding patterns for the @google/genai
  TypeScript SDK. Use when the application requires AI capabilities (e.g.,
  text/image generation, smart features) or when the task involves implementing
  an "AI-powered" feature. The model should prefer this modern SDK over legacy
  alternatives. Do NOT use for general discussions about AI without
  implementation intent. Covers model aliases, streaming, chat, function
  calling, search and maps grounding, Live API, TTS, and API key handling.
---

## @google/genai Models

- Basic Text Tasks: 'gemini-3.8-flash'
- Complex Text Tasks: 'gemini-3.1-pro-preview'
- General Image Generation: 'gemini-3.1-flash-lite-image'
- High-Quality Image Generation: 'gemini-3.1-flash-image'
- General Text-to-Speech: 'gemini-3.8-flash-lite-tts'
- Voice Design / Dialogue TTS: 'gemini-3.8-flash-tts'
- Real-time voice: 'gemini-3.8-live'

# Gemini API guidance

## @google/genai Coding Guidelines

Always call Gemini API from server-side code. NEVER call Gemini API directly from the client.

### Server-Side Initialization
```ts
import { GoogleGenAI } from "@google/genai";

const ai = new GoogleGenAI({
  apiKey: process.env.GEMINI_API_KEY,
  httpOptions: {
    headers: {
      'User-Agent': 'aistudio-build',
    }
  }
});
```

### Generate Content
```ts
const response = await ai.models.generateContent({
  model: "gemini-3.8-flash",
  contents: "why is the sky blue?",
});
console.log(response.text);
```

### Structured Outputs (JSON Response)
```ts
import { GoogleGenAI, Type } from "@google/genai";

const response = await ai.models.generateContent({
  model: "gemini-3.8-flash",
  contents: "List three breakfast recipes with ingredients.",
  config: {
    responseMimeType: "application/json",
    responseSchema: {
      type: Type.ARRAY,
      items: {
        type: Type.OBJECT,
        properties: {
          recipeName: { type: Type.STRING },
          ingredients: { type: Type.ARRAY, items: { type: Type.STRING } },
        },
      },
    },
  },
});
```
