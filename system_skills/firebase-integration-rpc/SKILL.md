---
name: "firebase-integration-rpc"
description: |
  Integrates Firebase (Firestore and Auth) into applications, generate secure rules, and handle errors.
---

# Firebase Integration Skill

Seamlessly incorporates Firebase Firestore and Auth into applications with hardened attribute-based access control (ABAC).

## 1. Intermediate Representation (IR)
- Describes database schema in `firebase-blueprint.json` separating entities (what) from firestore paths (where).

## 2. Hardened Security Rules (8 Pillars)
1. Master Gate (Relational Sync)
2. Validation Blueprints (Anti-Update-Gap)
3. Path Variable Hardening (isValidId)
4. Tiered Identity Logic
5. Total Array Guarding
6. PII Isolation & Schema Constraints
7. The Atomicity Guarantee (existsAfter)
8. Secure List Queries (Query Enforcer)

## 3. Structured Error Handling
```ts
function handleFirestoreError(error: unknown, operationType: OperationType, path: string | null) {
  const errInfo = {
    error: error instanceof Error ? error.message : String(error),
    operationType,
    path
  };
  console.error('Firestore Error:', JSON.stringify(errInfo));
  throw new Error(JSON.stringify(errInfo));
}
```
