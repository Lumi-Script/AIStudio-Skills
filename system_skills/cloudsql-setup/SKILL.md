---
name: "cloudsql-setup"
description: |
  Provisions a relational Cloud SQL (PostgreSQL) database and configures Firebase Authentication together.
---

# Cloud SQL Setup

These instructions outline the steps for initializing Cloud SQL for AIS applications.

## 1. Consent Gate & Eligibility
- Check feature eligibility with rpc_action service_name: "cloudsql", method_name: "CheckFeatureEligibility".
- Show UI card with show_aistudio_ui ui_type: "cloudsql_setup".

## 2. Drizzle ORM Setup
- Drizzle ORM (drizzle-orm) for queries.
- Drizzle Kit (drizzle-kit) for schema migrations using admin user.
- Connection pooling with pg.Pool object method.

```typescript
import { drizzle } from 'drizzle-orm/node-postgres';
import { Pool } from 'pg';
import * as schema from './schema.ts';

export const pool = new Pool({
  host: process.env.SQL_HOST,
  user: process.env.SQL_USER,
  password: process.env.SQL_PASSWORD,
  database: process.env.SQL_DB_NAME,
  max: 10,
});

export const db = drizzle(pool, { schema });
```
