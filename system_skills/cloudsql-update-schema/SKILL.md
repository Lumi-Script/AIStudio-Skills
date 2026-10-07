---
name: "cloudsql-update-schema"
description: >-
  Updates the Cloud SQL database schema for the app based on the schema defined in src/db/schema.ts and the configuration in src/db/drizzle.config.ts.

  Use this skill if any of the following happen:
    - The user requests to update their Cloud SQL database schema
    - Changes are made to the src/db/schema.ts file
    - Changes are made to the src/db/drizzle.config.ts file
---

## Cloud SQL Schema Update

Use these instructions when the application's relational database schema needs
to be updated or created based on `src/db/schema.ts`.

### Schema Update

*   Run the `rpc_action` tool with `service_name: "cloudsql"` and `method_name:
    "UpdateSchema"`.
*   **Verification (MANDATORY)**: After the schema update completes
    successfully, you **MUST** verify that the schema was applied correctly.
    1.  Run a query against `information_schema.columns` to confirm the new
        tables/columns exist in the database.
    2.  Ensure that the database state matches the schema defined in
        `src/db/schema.ts` before proceeding to test the application.
