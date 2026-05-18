# Privacy Policy — Claude Code Monitor (Stream Deck Plugin)

_Last updated: May 2026_

---

## Summary

This plugin does **not collect, store, or transmit any personal data** to the developer or any third party. All communication happens directly between your computer and Anthropic's official API.

---

## What data is accessed

### OAuth token
The plugin reads the file `%USERPROFILE%\.claude\.credentials.json` on your local machine. This file is created and maintained automatically by Claude Code (Anthropic's official CLI). It contains an OAuth access token used to authenticate requests to the Anthropic API.

**The token is used solely to make API calls to `api.anthropic.com` on your behalf.** It is never sent to any other server, logged, stored externally, or shared with the developer.

### API response headers
The plugin reads the following HTTP response headers returned by `api.anthropic.com`:

- `anthropic-ratelimit-unified-5h-utilization` — your current 5-hour session usage (a number between 0 and 1)
- `anthropic-ratelimit-unified-5h-reset` — the timestamp of your next session reset
- `anthropic-ratelimit-unified-7d-utilization` — your current weekly usage
- `anthropic-ratelimit-unified-5h-status` — your session status (`allowed`, `soft_limited`, or `hard_limited`)

These values are displayed on the Stream Deck key and are never transmitted anywhere else.

---

## What data is NOT collected

- No personal information (name, email, account details)
- No usage history or logs
- No analytics or telemetry
- No crash reports sent to the developer
- No data stored on any remote server

---

## Third-party services

The only external service the plugin communicates with is **Anthropic's API** (`api.anthropic.com`), which is the service you are already using through Claude Code. Anthropic's own privacy policy applies to those requests: [anthropic.com/privacy](https://www.anthropic.com/privacy)

---

## Contact

For questions about this privacy policy, open an issue on the support repository:  
[github.com/Simmonsstummer/SD_CC_Usage_Monitor/issues](https://github.com/Simmonsstummer/SD_CC_Usage_Monitor/issues)
