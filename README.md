# Log Sentinel

A free, private log analyzer that spots suspicious activity in authentication and web server logs: brute-force attempts, failed logins, credential stuffing patterns, and basic web attack signatures (SQL injection and path traversal attempts). Everything runs in your browser. No log data is uploaded anywhere.

**[Live demo](https://jishnu-arc.github.io/log-sentinel/)**

## What it detects

**In SSH / Linux auth logs:**
- Brute-force patterns: many failed logins from one IP
- A successful login right after repeated failures
- One account logging in from many different IP addresses
- Logins attempted against invalid/unknown usernames

**In Apache / Nginx access logs:**
- IPs generating many 4xx errors (scanning behavior)
- Unusually high request volume from one IP
- Request paths containing SQL-injection-style syntax
- Request paths containing path-traversal sequences (`../`)

This is a learning and triage tool, not a replacement for a real SIEM. It only sees what's in the log you give it.

## How to use it

1. Paste log lines into the text box, or drag in a `.log`/`.txt` file.
2. Click **Analyze**, or click **Load sample log** to see it work on example data first.
3. Review the findings, sorted by severity, and the table of top IP addresses.

## Features

- Works offline and installs as an app (PWA)
- Parses standard SSH/auth log lines and Apache/Nginx combined log format
- Auto-detects the log type, or you can pick it manually
- Nothing leaves your browser: no server, no upload, no tracking
- No dependencies and no build step

## Run locally

```bash
git clone https://github.com/jishnu-arc/log-sentinel.git
cd log-sentinel
python3 -m http.server 8000
```

## Deploy on GitHub Pages

Settings → Pages → Deploy from a branch → `main` and `/ (root)`.

## Scope and disclaimer

This tool analyzes log text you provide. It does not scan, probe, or connect to any network or system. Detection rules are simple heuristics for learning and demonstration purposes and will miss sophisticated attacks and produce false positives. Always verify findings manually before acting on them.

## Contributing

Ideas welcome: Windows Event Log (EVTX-exported text) support, firewall log parsing, a timeline view, CSV export of findings.

## License

[MIT](LICENSE)
