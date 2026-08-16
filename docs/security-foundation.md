# P3PO Security Foundation

## Current posture

P3PO control-plane data lives in a private Supabase schema and is not exposed to browser roles.

- `anon`: no schema/table grants
- `authenticated`: no schema/table grants
- `service_role`: server-side control-plane access only
- RLS: enabled on all P3PO tables as defense in depth

No service-role or secret credential may be committed or shipped to client code.

## Why there are no user RLS policies yet

The Command Center authentication and tenant-membership model is not implemented. Adding permissive placeholder policies now would weaken the design.

When interactive users are introduced, P3PO must add:

1. tenant membership/role model
2. server-verified authorization source
3. project-level membership where required
4. SELECT/INSERT/UPDATE/DELETE policies with ownership/tenant predicates
5. both USING and WITH CHECK on UPDATE policies
6. authorization tests

Do not authorize from user-editable metadata.

## Advisor status

Security Advisor currently reports informational `rls_enabled_no_policy` notices for P3PO tables; this matches the intentional server-only access model.

A warning for the legacy `vector` extension in `public` predates P3PO and should be evaluated separately before a production migration.

## Production provisioning

Customer production deployments must not reuse the shared development backend by default. Provision a dedicated project/database or an explicitly reviewed multi-tenant environment with tested isolation.
