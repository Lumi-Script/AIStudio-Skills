# Agent Environments Reference (JavaScript/TypeScript)

Environments are managed Linux sandboxes that give agents an isolated place to execute code and persist files.

## Environment parameter usage patterns
1. "remote": Fresh sandbox.
2. environment_id: Reuse existing sandbox preserving files and packages.
3. Declarative custom setup: Mount repositories, GCS buckets, or inline files.

```javascript
const interaction = await ai.interactions.create({
    agent: "antigravity-preview-09-2026",
    input: "List all files under /workspace.",
    environment: {
        type: "remote",
        sources: [
            {
                type: "repository",
                source: "https://github.com/octocat/Spoon-Knife",
                target: "/workspace/spoon-knife",
            },
        ],
    },
});
```
