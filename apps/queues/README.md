# Queues

Owns token and queue-related domain state.

Algorithmic queue mechanics should remain in `apps/core/queue_engine/`; this app should own Django-facing queue records and workflows.
