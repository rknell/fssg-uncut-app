`app` Lifecycle Controller
==========================

The global `app` object initializes the application and wires Cordova lifecycle events to DOM updates.

Source: `www/js/index.js`

`initialize()`
--------------
- Purpose: Entry point. Binds required startup events.
- Parameters: none
- Returns: void
- Example:
```html
<script>
  app.initialize();
</script>
```

`bindEvents()`
--------------
- Purpose: Registers event listeners (currently `deviceready`).
- Parameters: none
- Returns: void
- Side effects: Adds a `deviceready` listener on `document`.

`onDeviceReady()`
-----------------
- Purpose: Handler invoked when Cordova fires the `deviceready` event.
- Parameters: none
- Returns: void
- Calls: `app.receivedEvent('deviceready')`

`receivedEvent(id)`
-------------------
- Purpose: Updates the DOM to reflect that an event was received.
- Parameters:
  - `id` (string): The element id to target (e.g., `"deviceready"`).
- Returns: void
- Side effects:
  - Hides `.listening` element inside `#<id>`
  - Shows `.received` element inside `#<id>`
  - Logs to console: `Received Event: <id>`
- Example:
```html
<div id="deviceready">
  <p class="event listening">Listening</p>
  <p class="event received" style="display:none">Received</p>
  <script>
    app.receivedEvent('deviceready');
  </script>
</div>
```

Event Flow
----------
1. `app.initialize()`
2. `bindEvents()` adds `document.addEventListener('deviceready', ...)`
3. When fired, `onDeviceReady()` calls `receivedEvent('deviceready')`
