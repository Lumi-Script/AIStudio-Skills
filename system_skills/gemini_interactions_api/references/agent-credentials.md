# Agent Credentials Reference (JavaScript/TypeScript)

Credentials are server-managed secrets that allow managed agents to access third-party services without the secret ever entering the agent's sandboxed environment.

## Credential Types
- bearer_token: Personal access tokens, bot tokens, static API keys.
- oauth2: Live token exchange against token_url on creation; proxy refreshes access tokens automatically.
- environment_variable: Sandbox container receives placeholder __GEMINI_CRED_<id>__ swapped on egress.

```typescript
import { GoogleGenAI } from "@google/genai";

const ai = new GoogleGenAI({});

const githubCred = await ai.credentials.create({
  id: "github-production",
  type: "bearer_token",
  token: process.env.GITHUB_PAT || "ghp_xxxxxxxxxxxx",
});
```
