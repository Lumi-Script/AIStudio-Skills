# Google Calendar API

## Scopes
- https://www.googleapis.com/auth/calendar — Full calendar access.
- https://www.googleapis.com/auth/calendar.events — View and edit events.
- https://www.googleapis.com/auth/calendar.events.readonly — View events.

## Key Concepts
- Calendars: Collections of events (primary or secondary).
- Events: Appointments with title, time, and location.

## Client-Side Pattern
```typescript
const res = await fetch('https://www.googleapis.com/calendar/v3/calendars/primary/events', {
  headers: { Authorization: `Bearer ${accessToken}` },
});
```
