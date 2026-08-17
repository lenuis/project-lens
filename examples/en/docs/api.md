# API contract

> This file keeps request fields, responses, and error semantics in one place so frontend, backend, and AI tools do not guess.

## Create a booking

`POST /api/bookings`

```json
{
  "date": "2026-08-20",
  "slot": "14:30",
  "phone": "13800000000",
  "note": "Window seat"
}
```

## Booking states

- `pending`: waiting for shop confirmation.
- `confirmed`: confirmed by the shop.
- `completed`: customer arrived and the booking is complete.
- `cancelled`: cancelled but retained for history.
