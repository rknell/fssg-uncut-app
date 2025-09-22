Testing
=======

Specs are written with Jasmine and can be run in the browser.

Run Specs
---------
1. Open `www/spec.html` in a browser
2. The runner will load `www/js/index.js`, helpers, and specs
3. Results appear in the Jasmine HTML reporter

Key Specs
---------
- Verifies `app.initialize()` binds `deviceready`
- Verifies `onDeviceReady()` calls `receivedEvent('deviceready')`
- Verifies `receivedEvent()` toggles `.listening`/`.received` visibility
