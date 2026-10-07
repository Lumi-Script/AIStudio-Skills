# Deep Research Agent Reference (JavaScript/TypeScript)

The Gemini Deep Research Agent autonomously plans, executes, and synthesizes multi-step research tasks. Research tasks must be run in the background (`background: true`) and polled or streamed.

```javascript
import { GoogleGenAI } from '@google/genai';

const ai = new GoogleGenAI({});

const interaction = await ai.interactions.create({
    input: 'Research the history of Google TPUs.',
    agent: 'deep-research-preview-04-2026',
    background: true
});

while (true) {
    const result = await ai.interactions.get(interaction.id);
    if (result.status === 'completed') {
        break;
    }
    await new Promise(resolve => setTimeout(resolve, 10000));
}
```
