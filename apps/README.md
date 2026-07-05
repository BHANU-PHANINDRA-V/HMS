# Apps

Contains Django apps grouped by business domain.

Each app owns its future models, admin registration, views, URLs, services, tests, and migrations. The current files are placeholders only so that the project architecture is ready before implementation begins.

Business logic should live in app-level `services.py` files, not directly inside future views or models.
