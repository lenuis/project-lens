# Local Shop Booking

> Help independent shop owners accept online bookings through a clear and verifiable workflow.

## Current status

- Phase: booking-flow usability validation
- Direction: confirm the booking form before connecting notifications and administration
- Latest conclusion: date, time slot, and contact details are required for the first release; promotions and membership come later

## Current round

- Starting point: a static page existed, but fields and failure feedback were inconsistent
- Completed this round: organized requirements, interface structure, API conventions, and test entry points
- Current position: confirming booking fields and error messages
- Next: implement the form and validate failure recovery

## Product features

### Online booking

Let customers select a date and time and submit contact details without creating an account. [[docs/requirements.md|Booking requirements]]

#### Requirements

- [x] Define the first-release scope and success criteria <!-- project-lens:step changed=2026-08-16T01:20:00.000Z completed=2026-08-16T01:20:00.000Z -->
- [x] Confirm form structure and mobile layout [[docs/design.md#Booking form|Interface design]] <!-- project-lens:step changed=2026-08-16T03:10:00.000Z completed=2026-08-16T03:10:00.000Z -->

#### Form implementation

- [~] Confirm booking fields and error messages [[docs/requirements.md#Booking form|Requirements]] <!-- project-lens:step changed=2026-08-17T03:40:00.000Z -->
  - [x] Confirm dates and available time slots <!-- project-lens:step changed=2026-08-17T02:10:00.000Z completed=2026-08-17T02:10:00.000Z -->
  - [ ] Define phone-number and note validation
  - [ ] Document submission failure and retry behavior
- [ ] Implement the customer booking form [[docs/frontend.md#Execution checklist|Frontend checklist]]
- [ ] Connect the create-booking API [[docs/api.md#Create a booking|API contract]]

### Operations dashboard

Let the shop owner view today's bookings and confirm, complete, or cancel them. [[docs/backend.md|Backend implementation]]

#### Booking management

- [x] Define booking states and data fields [[docs/api.md#Booking states|State contract]] <!-- project-lens:step changed=2026-08-16T06:30:00.000Z completed=2026-08-16T06:30:00.000Z -->
- [ ] Implement today's booking list
- [ ] Add confirm, complete, and cancel actions

### Release and reliability

Give every release test evidence, user-facing change notes, and a recovery path. [[docs/release.md|Release workflow]]

#### First release

- [x] Establish test scope and acceptance checklist [[docs/testing.md|Test record]] <!-- project-lens:step changed=2026-08-16T08:45:00.000Z completed=2026-08-16T08:45:00.000Z -->
- [ ] Validate on real mobile devices
- [ ] Record user-visible 0.1.0 changes [[CHANGELOG.md|Release record]]

## Recent updates

2026-08-17 11:40:00 - Added booking-field boundaries, error feedback, and linked test coverage.
2026-08-16 18:20:00 - Created frontend, backend, API, design, test, and release documents and linked them from overview tasks.
