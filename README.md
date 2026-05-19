# Telegram Desktop clipboard test

Test page provided to **Telegram Security** for vendor-side verification of
Telegram Desktop on Windows (WebView2 backend).

## How to run the test

1. Open Telegram Desktop on **Windows** (WebView2 runtime installed by default).
2. Copy any text to the OS clipboard, e.g.
   `CLIPBOARD-TEST-12345`.
3. Open the test bot in Telegram Desktop and press the **Run test** menu button.

### Expected behavior
WebView2 should display a permission prompt before exposing the clipboard
(`COREWEBVIEW2_PERMISSION_STATE_DEFAULT` is the documented default).

### Current behavior
The test page calls `navigator.clipboard.readText()` on load and renders the
returned value on screen. When opened as a Telegram mini app, it also displays
the same result through `Telegram.WebApp.showAlert()`.

## Scope

Provided strictly for vendor verification. Not intended for public use.
