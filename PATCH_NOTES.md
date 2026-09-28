# Patch notes — EURUSD plan v2.1

## Startup crash fix

Fixed a startup-time JavaScript initialization-order bug in `bot.js`.

`currentDayStartTs` was being initialized from `currentDayKey` before `currentDayKey` had been declared, causing Node.js to abort with:

`ReferenceError: Cannot access 'currentDayKey' before initialization`

`currentDayKey` is now initialized before `currentDayStartTs`.

## Validation

- `node --check bot.js` passes.
- Bot startup was smoke-tested with dependency stubs; it reaches the dashboard/server startup and connection/retry path without the previous `ReferenceError`.
- No trading credentials were included in the ZIP.
