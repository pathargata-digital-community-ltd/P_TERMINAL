# P_TERMINAL Phase 1 TODO

- [ ] Terminal access requires a signed-in Firebase user with both `admin: true` and `superAdmin: true` claims.
- [ ] Non-authenticated visitors see a working sign-in path; authenticated non-Super Admin users see a clear denial state.
- [ ] Maintenance, AI Assistant, and Marketplace checkout changes require confirmation and a written reason.
- [ ] Sensitive changes write configuration and `super_admin_audit` event data atomically.
- [ ] Audit events include request ID, actor UID, action, target, before/after values, reason, timestamp, and result.
- [ ] Audit events are bounded and cannot be edited or deleted from the Terminal.
- [ ] Terminal shows a bounded recent audit history.
- [ ] Safe command terminal supports status, health, approved feature controls, help, and clear only.
- [ ] No fake activity, bot deployment, browser secret storage, unrestricted delete, or routine Admin App workflow is present.
- [ ] Validate HTML/JavaScript and rules JSON without writing production data.

## Phase 2 — Emergency Controls and Feature Flags

- [x] Add Super Admin-only Emergency Controls UI for global maintenance and read-only emergency mode.
- [x] Add audited Feature Flags UI for post creation, media upload, messaging, registration, public profiles, and push notifications.
- [x] Add bounded Firebase validation contracts for `feature_flags` and `emergency_controls`.
- [ ] Connect Native App write paths and screens to consume these flags safely.
- [ ] Add rollback preview and two-person approval for global emergency switches.

## Phase 3 — Rollback Preview and Approval Foundation

- [x] Show the latest audited change's before/after state in a bounded rollback preview.
- [x] Store a dedicated immutable rollback snapshot for every sensitive change with snapshot ID, target path, before state, requested after state, requester UID, created time, reason, request ID, and status.
- [x] Link each immutable snapshot ID into its corresponding audit event and rollback preview.
- [ ] Require a second Super Admin approval for global maintenance and read-only changes.
- [ ] Add approve, reject, expire, and cancel states with actor and timestamp.
- [ ] Add an explicit rollback action only after snapshot and approval rules are validated.
