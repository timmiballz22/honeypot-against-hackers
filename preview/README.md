# Public Cloudflare observatory

Source: `cloudflare-worker.js`. The Worker binds **only PUBLIC_DB**, never private D1. Read-only HTTP API, simulated telemetry, 403 on `/admin`.

Deploy with Wrangler using the accompanying `wrangler.jsonc` and your authenticated Cloudflare account. Existing hosted deployment: https://honeypot-observability-preview.furryfragz-work.workers.dev/

No sensitive values, private code, or real network-derived geographic attribution are included.
