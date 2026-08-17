# System architecture

> This file records system boundaries and major dependencies so AI tools can identify the correct layer for a change.

```text
Customer page ──┐
                ├─ Booking API ─ Database
Operations UI ──┘       └─ Notification service
```

- The frontend displays only slots returned by the server.
- The backend owns capacity checks, idempotency, and state transitions.
- Notification failure does not roll back a successfully created booking.
