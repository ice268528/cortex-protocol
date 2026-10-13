# FB-01 — Gate B Packet

## Goal
Employee submits title + description; system stores Feedback with initial state `new`.

## Flow
Employee → frontend → backend validation → durable write → success/error response.

## Invariants
- authenticated employee only
- no false success if durable write fails
- initial status is `new`

## Human Decision
Accepted.
