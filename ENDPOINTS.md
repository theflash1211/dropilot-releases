# Network Allowlist & Outbound Endpoints

All outbound HTTP and WebSocket traffic in Dropilot passes through a single allowlist validator (including redirect targets). Non-allowlisted hosts, direct IP literals, embedded URL credentials, and insecure schemes (`http://`, `ws://`) are rejected before any connection is opened.

## Allowlisted Hosts

| Feature | Allowlisted Hosts / Paths | Purpose |
| --- | --- | --- |
| **Twitch** | `twitch.tv`, `www.twitch.tv`, `gql.twitch.tv`, `id.twitch.tv`, `passport.twitch.tv`, `spade.twitch.tv`, `beacon.twitch.tv`, `assets.twitch.tv`, `static.twitchcdn.net`, `usher.ttvnw.net`, `*.ttvnw.net`, `static-cdn.jtvnw.net`, `*.jtvnw.net` | Official login window, OAuth validation, drops GQL queries, stream-less HLS `HEAD` watch heartbeat (0 Mbps video), Spade watch telemetry, box art & reward images |
| **Epic Games Free Weekly** | `store-site-backend-static-ipv4.ak.epicgames.com/freeGamesPromotions` + official `*.epicgames.com` / `*.unrealengine.com` checkout hosts | Public weekly free-game feed and optional 1-click assisted checkout inside Dropilot's isolated WebView2 window |
| **Login IdPs (Login Window Only)** | `accounts.google.com`, `appleid.apple.com`, `challenges.cloudflare.com`, `*.google.com`, `*.apple.com`, `*.amazon.com`, `*.gstatic.com`, `*.googleapis.com` | Permitted only inside the embedded login window when using OAuth social sign-in or platform verification |
| **Signed Updates** | `api.github.com/repos/theflash1211/dropilot-releases/releases/latest` & `github.com/theflash1211/dropilot-releases/releases/latest/download/latest.json` | Checks for and installs Minisign-verified Dropilot updates |
| **Remote Config** | `raw.githubusercontent.com/theflash1211/dropilot-releases/main/remote-config.json` | Optional live Twitch GQL persisted query hash manifest (1-hour local cache; can be disabled in Settings) |
| **Browser External Links** | `twitch.tv`, `*.twitch.tv`, `github.com`, `epicgames.com`, `store.epicgames.com`, `developer.microsoft.com`, `com.epicgames.launcher://store/...` | Safe links opened in your default browser or Epic Games Launcher when clicked |
