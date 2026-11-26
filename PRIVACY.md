# Privacy Policy & Local Storage Map

Dropilot collects **zero telemetry**, **zero analytics**, and **zero crash reports**. Nothing leaves your PC except direct requests to official platform endpoints and GitHub release/config checks from `theflash1211/dropilot-releases`.

## Exact Storage Locations on Windows

Dropilot writes strictly inside per-user AppData folders and Windows Credential Manager:

| Data | Location | Notes |
| --- | --- | --- |
| **Session Tokens** | Windows Credential Manager (`Dropilot/*`) | Protected by Windows DPAPI; never written to `settings.json`, logs, or frontend state |
| **App Settings** | `%APPDATA%\Dropilot\settings.json` | Written atomically; stores theme, intervals, campaign toggles, priority queue, and window bounds |
| **Claim History & Cache** | `%APPDATA%\Dropilot\history.json`, `epic-cache.json`, `remote-config-cache.json` | Local-only lifetime claim log and offline caches |
| **Rolling Logs** | `%LOCALAPPDATA%\Dropilot\logs\dropilot.log*` | Daily rolling, capped size; all tokens, cookies, and auth headers are scrubbed |
| **Isolated WebView2 Profile** | `%LOCALAPPDATA%\Dropilot\WebView2\` | Used strictly by Dropilot's own embedded UI, login, and Epic claim windows |
| **Autostart (Optional, Off by Default)** | `HKCU\Software\Microsoft\Windows\CurrentVersion\Run` | Standard current-user autostart entry; never touches HKLM, Task Scheduler, or Windows Services |

## Browser Profile Isolation

Dropilot **never** accesses, reads, or modifies Chrome, Microsoft Edge, Firefox, Brave, Opera, or any external browser's profile directory, cookies, `Local State`, or `Login Data` files. Authentication happens only when you sign in directly on official pages inside Dropilot's isolated WebView2 window.

## Deleting All Data

You can remove all Dropilot sessions, WebView2 browsing data, and settings at any time via **Settings → Data & Updates → Clear app data**, or by deleting `%APPDATA%\Dropilot`, `%LOCALAPPDATA%\Dropilot`, and the `Dropilot/*` entries in Windows Credential Manager.
