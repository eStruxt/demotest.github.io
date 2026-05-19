# Telegram Desktop clipboard — coordinated disclosure PoC

Test page provided to **Telegram Security** as part of a coordinated disclosure
for an issue affecting Telegram Desktop on Windows (WebView2 backend).

## How to run the test

1. Open Telegram Desktop on **Windows** (WebView2 runtime installed by default).
2. Copy any text to the OS clipboard, e.g.
   `CLIPBOARD-TEST-PoC-12345-SECRET-DO-NOT-LEAK`.
3. Open the disclosure test bot in Telegram Desktop and press the **Run test** menu button.

### Expected behavior
WebView2 should display a permission prompt before exposing the clipboard
(`COREWEBVIEW2_PERMISSION_STATE_DEFAULT` is the documented default).

### Observed behavior
The test page resolves `navigator.clipboard.readText()` immediately without
any prompt and renders the value on screen, demonstrating that any web content
rendered inside the Telegram Desktop WebView2 wrapper can read the user's
clipboard silently.

## Verifying the end-to-end flow

The page additionally POSTs the result to a public webhook.site inbox so the
Telegram Security team can observe the value reaching the network in real time:

- Inbox view (read-only): _see disclosure email_

The page performs no other network activity. The full page source is this
repository's `index.html`.

## Scope

Provided strictly for vendor reproduction. Not intended for public use.
