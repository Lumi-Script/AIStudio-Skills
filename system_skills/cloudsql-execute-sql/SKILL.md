---
name: "cloudsql-execute-sql"
description: |
  Executes SQL statements on the Cloud SQL instance. This tool is designed for data query language (DQL) and data manipulation language (DML) operations, such as querying existing data, seeding databases, and debugging.

  Do NOT use this skill for:
    - Applications that do not use Cloud SQL as their database.

  Important Guidelines:
    - Do not use this tool for data definition language (DDL) operations (e.g., creating or altering tables); these should be handled by the ORM. Exception: You may use this tool to install PostgreSQL extensions, which the ORM does not support.
    - Do not use this tool for data control language (DCL) operations.
    - Do not use this tool to create, update, or delete databases or database users.
    - Avoid destructive actions like dropping tables or databases.
    - Use "sql_statement" as the argument name. Do not use "sql".
---

## Cloud SQL Query Execution

Use these instructions when you need to query or manipulate data in the Cloud
SQL instance for testing, seeding or debugging.

### Executing SQL

*   To execute a SQL statement (e.g., for data manipulation or querying), use
    the `rpc_action` tool with `service_name: "cloudsql"` and `method_name:
    "ExecuteSql"`.
*   **Arguments**: You MUST use `sql_statement` (and NEVER `sql`) as the key in
    the `arguments` map.
