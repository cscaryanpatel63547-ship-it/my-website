# UsefulTube Hub
React + Vite discovery site powered by the official YouTube Data API v3.

## Setup
1. `npm install`
2. Create a key: Google Cloud Console → enable **YouTube Data API v3** → Credentials → API key.
3. `cp .env.example .env` and set `VITE_YOUTUBE_API_KEY=your_key`
4. `npm run dev` (local) / `npm run build` (production)

## Keeping the key private (recommended)
`VITE_*` variables are bundled into browser code, so anyone can see them. On Vercel, set env vars
`YOUTUBE_API_KEY=your_key` and `VITE_USE_PROXY=true`; requests then go through `api/youtube.js` and the key stays server-side
(responses are cached 10 min). If you use the client key instead, restrict it by HTTP referrer in Google Cloud.

## Notes
- Quota: default 10,000 units/day; each search costs ~100 units, video lookups ~1.
- Trending = YouTube "most popular" in the Education category for `VITE_REGION` (default US).
- SPA routing is preconfigured for Vercel (`vercel.json`) and Netlify (`public/_redirects`).
