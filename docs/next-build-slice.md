# P3PO Next Build Slice

## Objective

Turn the foundation into a working product surface without coupling it to any customer or legacy backend.

## Build order

1. server-side P3PO data access layer for the private `p3po` schema
2. feature registry loader and deployment config validation
3. Inventory Intelligence provider interface
4. Supabase development adapter implementing the read-only inventory interface
5. work-order state service
6. defect/lesson recording service
7. minimal Command Center UI:
   - Overview
   - Work Orders
   - QA / Defects
   - Learning
   - Releases
   - Features
8. show Inventory navigation only when `inventory_intelligence` is enabled
9. integration health checks
10. CI validation for schemas/configuration

## Non-goals

- customer branding
- customer-specific workflows in core
- production deployment automation before release gates are tested
- broad inventory writes
- direct browser access to private control tables
