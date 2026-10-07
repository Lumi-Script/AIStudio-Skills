# Managed Agents Reference (JavaScript/TypeScript)

This reference guide provides JavaScript/TypeScript code patterns for creating and using Managed Agents with the `@google/genai` SDK.

## Multi-turn Conversations
```javascript
const interaction2 = await ai.interactions.create({
    agent: "antigravity-preview-09-2026",
    previous_interaction_id: interaction.id,
    environment: interaction.environment_id,
    input: "Now plot the Fibonacci sequence as a line chart.",
}, { timeout: 300_000 });
```
