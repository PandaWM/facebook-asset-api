---
name: facebook-asset-api
description: Build, review, document, and troubleshoot Meta/Facebook asset management API systems for Business Manager, ad accounts, pixels, apps, system users, OAuth, App Review, Graph API, Marketing API, audit logging, rate limiting, and compliance-first risk analysis. Use when working on Facebook App development, Facebook API integrations, BM/ad account/pixel/user asset workflows, App Review permission narratives, or diagnosing restrictions caused by automation-like asset operations.
---

# Facebook Asset API

Use this skill to design or audit a Facebook/Meta asset management system without encouraging evasion of Meta enforcement. Treat Meta Business assets as high-risk operational objects: every API action must have a user/business purpose, clear authorization, traceable logs, and conservative execution controls.

## Operating Rules

- Do not help bypass Meta restrictions, evade enforcement, fabricate business identity, hide automation, rotate accounts to avoid detection, or misuse fingerprints/cookies.
- Prefer official Meta/Facebook documentation as the source of truth. If the user asks about current API versions, permissions, review rules, or policy details, verify against official Meta documentation before giving exact claims.
- Separate read-only diagnosis from state-changing actions. Ask for explicit confirmation before recommending or performing changes that affect BM users, ad accounts, pixels, apps, payment methods, permissions, or review submissions.
- Redact secrets in all examples: access tokens, app secrets, cookies, passwords, OAuth codes, client secrets, and system user tokens.
- Treat bulk operations as risk-sensitive even when technically allowed by API permissions.

## Workflow

1. Identify the user goal:
   - App Review or permissions: read `references/app-review.md`.
   - Permission-to-feature mapping: read `references/permission-matrix.md`.
   - API architecture or endpoint design: read `references/api-design.md`.
   - Audit logs, throttling, and operational controls: read `references/audit-and-controls.md`.
   - BM restrictions or asset risk analysis: read `references/restriction-analysis.md`.
   - Privacy, data retention, or deletion flows: read `references/privacy-and-data.md`.
   - Graph API or Marketing API version upgrades: read `references/version-upgrades.md`.
   - Implementation planning: read `references/implementation-checklists.md`.
   - Deliverables or report formatting: read `references/output-templates.md`.
2. Map the involved assets:
   - Business portfolio / BM ID
   - App ID
   - System User ID
   - Facebook User ID
   - Ad Account IDs
   - Pixel IDs
   - Page IDs
   - Domains, payment methods, and customer/team IDs when relevant
3. Classify each API action:
   - Read-only sync
   - User-initiated change
   - Admin/back-office change
   - Scheduled job
   - Bulk job
   - Retry/recovery job
4. Check for risk patterns:
   - High-volume actions in short windows
   - Repeated failures or retries
   - Many assets sharing one app/system user/admin account
   - Newly created BMs receiving many linked assets quickly
   - Template-like naming across many assets
   - Pixel, user, app, or ad account reuse across restricted BMs
5. Recommend compliant fixes:
   - Reduce or pause risky actions
   - Add explicit user confirmation for sensitive actions
   - Add rate limits and cooldowns
   - Add audit logging and secret redaction
   - Isolate restricted assets from new workflows
   - Prepare truthful App Review materials

## Required Output Shape

For reviews or incident analysis, return:

- **Findings**: specific evidence and why it matters.
- **Likely causes**: ranked, with confidence level.
- **Immediate actions**: what to pause or change today.
- **Engineering changes**: API, audit, rate limit, or UI changes.
- **Policy/App Review notes**: what must be documented truthfully.
- **Data needed next**: exact IDs, logs, timestamps, or screenshots required.

## Asset Action Risk Levels

- **Low**: read-only insights sync, listing owned assets, reading account status, reading spend.
- **Medium**: assigning one known asset after user confirmation, updating internal notes, refreshing token status.
- **High**: binding pixels to ad accounts, inviting users, assigning ad accounts to customers, changing account type, changing payment or admin roles.
- **Critical**: bulk creation, bulk binding, bulk invitation, bulk reassignment, repeated retries after API failures, actions on recently restricted or newly created BMs.

For high or critical actions, require a business reason, actor identity, asset IDs, confirmation path, idempotency key, rate limit, and rollback/stop plan.

## References

- `references/app-review.md`: permission narratives, review materials, and truthful product positioning.
- `references/permission-matrix.md`: map common Meta permissions to features, review evidence, and risk controls.
- `references/api-design.md`: architecture patterns for OAuth, token storage, API boundaries, and data model.
- `references/audit-and-controls.md`: logging schema, redaction, throttling, cooldowns, retries, and risk scoring.
- `references/restriction-analysis.md`: how to analyze BM/ad account restrictions from asset timelines.
- `references/privacy-and-data.md`: privacy policy, retention, deletion, token handling, and data minimization.
- `references/version-upgrades.md`: version upgrade workflow, including Graph API/Marketing API v25.0 checks.
- `references/implementation-checklists.md`: pre-launch, production, incident, and App Review checklists.
- `references/output-templates.md`: reusable output formats for API reviews, App Review narratives, and restriction reports.
