# Backend implementation

> This file defines server responsibilities, write boundaries, and runtime constraints so API behavior remains stable.

## Responsibilities

- Validate business days, slot capacity, and phone format.
- Prevent overbooking when a booking is created.
- Preserve a timestamp for every state transition.

## Risks

- Repeated submissions require an idempotency key.
- Cancellation must not delete the original booking record.
