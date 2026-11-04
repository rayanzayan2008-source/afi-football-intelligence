# AFI Football Intelligence — Cloudflare Worker deployment

This version includes both the static website and a server-side Worker API proxy.
The API key is read only from the Cloudflare Worker secret `API_FOOTBALL_KEY`.

## Important
A static-assets-only upload cannot run this backend. Deploy this project as a Worker
with Static Assets using Wrangler / Cloudflare Workers Builds.

## Files
- `public/index.html` — AFI website
- `src/index.js` — Worker API proxy
- `wrangler.json` — Worker + static assets configuration

## Secret
In Cloudflare Worker settings, add a Secret:
- Name: `API_FOOTBALL_KEY`
- Value: your private API-Football key

## API routes
- `/api/football?action=fixtures&date=YYYY-MM-DD`
- `/api/football?action=live`
- `/api/football?action=analysis&fixture=FIXTURE_ID`

## Deploy with Wrangler
From this project folder:
1. `npx wrangler login`
2. `npx wrangler secret put API_FOOTBALL_KEY`
3. `npx wrangler deploy`

The API provider may return no odds or predictions for some fixtures or competitions.
The dashboard displays those as unavailable rather than inventing data.
