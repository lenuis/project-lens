# Decision record

> This file records important choices, rationale, and rejected alternatives so future AI tools do not repeatedly overturn confirmed direction.

## Customers do not need accounts

The first release prioritizes a low booking barrier. Contact details are used only for the current booking. Membership and loyalty points are outside 0.1.0.

## Git stores commits; CHANGELOG speaks to users

Do not duplicate Git history in Markdown. `CHANGELOG.md` explains only the user-visible changes in formal releases.
