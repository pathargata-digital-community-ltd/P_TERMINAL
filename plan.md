# P_TERMINAL Phase 1: Super Admin Security Foundation

## Design movement

**Calm operations cockpit**: a restrained, high-trust control room rather than a flashy bot terminal.

## Core principles

1. **Separation of duties**: routine moderation and support remain in the Admin App; high-risk configuration and infrastructure controls remain in this Terminal.
2. **Explicit authorization**: the Terminal requires both Firebase `admin: true` and `superAdmin: true` custom claims.
3. **Audited writes**: sensitive changes are confirmed, require a reason, and write the configuration change and audit event atomically.
4. **Safe by default**: no fake engagement, no browser secrets, no unrestricted deletion, and no production mutation during validation.

## Phase 1 outcomes

- Super Admin-only terminal gate with clear sign-in and permission states.
- Confirmation plus reason workflow for sensitive feature and maintenance changes.
- Immutable `super_admin_audit` event stream with actor, action, target, before/after state, reason, request ID, and timestamp.
- Audit viewer in the Terminal with bounded reads.
- Safe command terminal limited to read-only status/health and approved feature controls.
- Foundation for later dry-run migrations and two-person approval workflows.

## Data and security contract

The Native App Firebase rules own authorization. `admin_settings` and `marketplace_controls` remain protected by `auth.token.admin === true`; `super_admin_audit` is readable and writable only by `auth.token.superAdmin === true` and validates the actor and bounded event fields. The browser never receives service-account keys or provider secrets.

## Out of scope for this phase

Routine Admin App operations, fake users, fake likes/comments/shares, mass notification injection, password access, unrestricted delete, direct browser deployment, and production data cleanup.
