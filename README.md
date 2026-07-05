# Skin Care Hospital Management System

Production-oriented Django architecture scaffold for a single-hospital, one-doctor skin care hospital management system.

This repository currently contains architecture only. It intentionally avoids business logic, Django models, HTML pages, SQL, and dummy CRUD code.

## Architecture Principles

- Keep each business domain in its own Django app under `apps/`.
- Keep reusable system-wide utilities in `apps/common/`.
- Keep algorithmic and workflow engines in `apps/core/`.
- Keep external integrations behind dedicated app boundaries such as `apps/payments/` and `apps/notifications/`.
- Keep database documentation in `docs/database/`; Django migrations remain inside each app's `migrations/` folder.
- Keep templates, static files, uploaded media, and frontend source assets separated.
- Keep future modules visible but isolated under `future/` until they become production apps.

## Django Apps

- `accounts`: authentication, role-based access, user profile ownership.
- `patients`: patient domain and patient-facing workflows.
- `staff`: staff domain, walk-in support, leave workflow ownership.
- `doctors`: doctor domain, doctor dashboard and availability ownership.
- `appointments`: central appointment domain; this should remain the main scheduling boundary.
- `sessions`: doctor clinic session lifecycle such as start, pause, resume, and end.
- `queues`: token and patient queue domain.
- `payments`: online payment, cash/UPI recording, wallet payment coordination, gateway boundaries.
- `wallets`: wallet balance, ledger, refunds, and adjustments.
- `referrals`: referral and discount policy coordination.
- `notifications`: SMS, email, reminder, and event notification boundaries.
- `reports`: reporting and future analytics entry point.
- `audit`: activity logs, security events, and traceability.
- `admin_portal`: admin-facing orchestration screens and workflows.

## Placement Guide

- Linked List: `apps/core/algorithms/linked_list.py`
- Priority Queue: `apps/core/algorithms/priority_queue.py`
- Queue Engine: `apps/core/queue_engine/`
- Payment Integration: `apps/payments/gateways.py`, `apps/payments/webhooks.py`, and `apps/payments/services.py`
- Business Logic: each app's `services.py`
- Read/query helpers: each app's `selectors.py` when the app needs a dedicated query layer
- Helper Functions: `apps/common/helpers/`
- Constants: `apps/common/constants/`
- Enumerations: `apps/common/enums/`
- Database Migrations: inside each Django app's `migrations/` directory
- Documentation: `docs/`

## Naming Conventions

- Python packages and modules: `snake_case`
- Django apps: plural domain names where natural, such as `patients`, `appointments`, `payments`
- Classes: `PascalCase`
- Functions and variables: `snake_case`
- Constants: `UPPER_SNAKE_CASE`
- Templates: grouped by app or role, named with `snake_case.html` when implemented later
- Static assets: lowercase kebab-case or snake_case, grouped by type
- API versions: `api/v1/`, `api/v2/`
- Settings modules: `base.py`, `development.py`, `production.py`, `testing.py`

## Folder Tree

```text
HMS/
  api/
  apps/
  config/
  docs/
  frontend/
  future/
  media/
  requirements/
  scripts/
  static/
  templates/
  tests/
  .env.example
  .gitignore
  manage.py
  pyproject.toml
```

The detailed tree can be regenerated with:

```powershell
Get-ChildItem -Recurse
```
