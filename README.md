# Honey / Fieldnotes — Simulated Telemetry Observatory

Public website source for an **entirely synthetic** honeypot-telemetry observatory. This repository is owned by the public GitHub account only; **private simulation data, secrets and backend source must never be committed here**.

## Live website

https://honeypot-observability-preview.furryfragz-work.workers.dev/

Powered by a public Cloudflare Worker and a **public-only** D1 database binding. Data includes 48 seeded synthetic events in a demonstration run. Location markers are deliberately assigned, not IP-derived; no listeners or real attacks are recorded.

### Public API

- `GET /api/public/stats` — simulated run statistics.
- `GET /api/public/events` — allowlisted, synthetic-only events and geographic coordinates.
- `GET /` — interactive Leaflet world map showing fabricated locations.
- `GET /activity`, `/services`, `/research` — read-only informational pages.
- `GET /admin` — HTTP 403. There is no public admin console.
- No public mutation API. POST requests return HTTP 405.

## Deploy

`preview/cloudflare-worker.js` is the currently deployed Cloudflare Worker source, including an interactive map. Configure a public D1 binding named `PUBLIC_DB` pointing only to your sanitized public D1 database, and use your own Cloudflare account. **Do not bind the private D1 database.**

The private implementation belongs in a **different PRIVATE GitHub repository** `specter-telemetry-api` under the James account. Cloudflare private Worker `specter-telemetry-core` is authenticated with a secret and has no public workers.dev subdomain.

## Research limitations

- All present data is simulated. The map does **not** represent observed attacks, detected source IPs, or inferred attacker geography.
- The basemap uses OpenStreetMap tiles and attribution.
- The original React/TypeScript/Vite/Firebase prototype is not the production deployment.
- Never check in secrets, token values, service-account credentials or fake-decoy credential fields.

See [Cloudflare D1 documentation](https://developers.cloudflare.com/d1/) and [OpenStreetMap tile policy](https://operations.osmfoundation.org/policies/tiles/).
