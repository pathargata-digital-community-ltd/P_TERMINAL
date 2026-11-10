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
