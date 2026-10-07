# SaaS & Dashboard Design Guidelines

This reference covers enterprise SaaS products, business analytics platforms,
data spreadsheets, workflow & task managers, and admin consoles.

## 1. Scope & Taxonomy Coverage
- Enterprise SaaS & Systems: B2B platforms, user management, billing panels.
- Data Spreadsheets & Normalization Tools: Habit logs, financial ledgers, test analyzers.
- Task & Mailbox Assistants: Scheduling agents, queue management.
- Developer & Monitoring Consoles: API usage monitors, telemetry dashboards.

## 2. Architectural & Visual Rules
### A. Layout Structure & Navigation
- Workspace Canvas: Sidebar navigation (240px–280px) + Header with breadcrumbs + Main viewport.
- Top Bar Contract: Breadcrumbs on left, actions on right.
- Single-Elevation Depth: Flat surfaces with subtle 1px border lines.
- High-Density Data Grids: Compact row heights (36px–44px), clean column alignments.

### B. Tabular Numerals & Metric Display
- Tabular Figures: Every numeric value, counter, timestamp, and currency must use tabular figures or monospace font.
- Hardware & Segmented Displays: Dedicated segmented styles with dark metallic bezels.

### C. State Completeness
1. Populated State: Rich domain-grounded table rows.
2. Empty State: Explanatory copy and primary creation action.
3. Loading State: Skeleton placeholders matching row geometry.
4. Filtering & Search: Live client-side search input and status filters.
