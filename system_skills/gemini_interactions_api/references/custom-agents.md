# Building Custom Agents Reference (JavaScript/TypeScript)

Managed agents on the Gemini API let you bundle instructions, skills, and an environment into a reusable agent that you can invoke by ID.

```javascript
import { GoogleGenAI } from "@google/genai";

const ai = new GoogleGenAI({});

const agent = await ai.agents.create({
    id: "code-reviewer",
    base_agent: "antigravity-preview-09-2026",
    system_instruction: "You are a senior code reviewer. Check every file for bugs and security issues.",
    base_environment: {
        type: "remote",
        sources: [
            {
                type: "repository",
                source: "https://github.com/my-org/backend",
                target: "/workspace/repo",
            }
        ],
    },
});
```
