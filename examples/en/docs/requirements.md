# Booking requirements

> This file describes user problems, scope, and acceptance criteria. It tells people and AI what to build without prescribing the implementation.

## Booking form

Customers should complete a booking in under one minute without creating an account.

- Date: a business day within the next 14 days.
- Time slot: an available 30-minute slot.
- Phone: used for confirmation and change notifications.
- Note: optional, limited to 100 characters.

### Acceptance criteria

- [x] Dates and slots come from one availability source.
- [ ] A missing phone number produces a clear field-level message.
- [ ] A network failure preserves entered values and allows retry.

## Booking management

The shop owner can view today's bookings and mark them confirmed, completed, or cancelled.
