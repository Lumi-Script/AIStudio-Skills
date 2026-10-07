# Antigravity Agent Reference (JavaScript/TypeScript)

The Antigravity agent (`antigravity-preview-09-2026`) is a general-purpose managed agent that reasons, executes code, manages files, and browses the web inside a secure Linux sandbox.

```javascript
import { GoogleGenAI } from "@google/genai";

const ai = new GoogleGenAI({});

const interaction = await ai.interactions.create({
    agent: "antigravity-preview-09-2026",
    input: "Search for the latest AI research papers on reasoning and summarize them.",
    environment: "remote",
    tools: [
        { type: "google_search" },
        { type: "url_context" },
    ],
}, { timeout: 300000 });

console.log(interaction.output_text);
```
