# CC Usage Monitor — Stream Deck Plugin

Monitor your **Claude Code session usage** in real time, directly on an Elgato Stream Deck key.

---

## What you see on the key

The key displays a large session percentage number, colored by usage level — exactly as it appears in use:

- **Green** — usage below 70%, session healthy
- **Yellow** — usage between 70% and 89%, approaching limit
- **Red** — usage at or above 90%, session critical
- **Flashing** — usage above 90% (animated alert)

Below the number, the key title shows the **countdown to session reset** (e.g. `3h12m`).

When Claude Code enters extra usage or rate-limited mode, the key shows `EXTRA` or `STOP` above the countdown.

**Press the key** at any time to force an immediate refresh.

---

## Requirements

- Elgato Stream Deck hardware (any model with keys)
- Stream Deck software **6.0 or later**
- [Claude Code](https://claude.ai/code) installed and signed in on Windows

> Claude Code manages its own OAuth token automatically — no manual API key setup required.

---

## Install

Find **CC Usage Monitor** in the [Elgato Marketplace](https://marketplace.elgato.com) and click Install, or search for it directly inside the Stream Deck software.

---

## How it works

Every 5 minutes the plugin makes a minimal API call (1 output token, Haiku model) to the official Anthropic API and reads the rate-limit response headers:

| Header | Meaning |
|---|---|
| `anthropic-ratelimit-unified-5h-utilization` | Session usage 0.0–1.0 |
| `anthropic-ratelimit-unified-5h-reset` | Timestamp of next session reset |
| `anthropic-ratelimit-unified-7d-utilization` | Weekly usage 0.0–1.0 |
| `anthropic-ratelimit-unified-5h-status` | `allowed` / `soft_limited` / `hard_limited` |

The countdown timer updates every second between API calls using the cached reset timestamp — no extra calls are made.

> **Why 5 minutes?** Each API call counts slightly toward the session usage being monitored. Polling more frequently would accelerate the very limit you're watching.

---

## Support

Open an issue on this repository: [github.com/Simmonsstummer/SD_CC_Usage_Monitor/issues](https://github.com/Simmonsstummer/SD_CC_Usage_Monitor/issues)

---

## Privacy

See [PRIVACY.md](PRIVACY.md)
