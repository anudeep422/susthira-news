# Susthira News — update guide

The site is `public/index.html` (layout, never changes) + `public/stories.json` (content, replaced at every update).
Pushing to `main` deploys to Firebase automatically (see `.github/workflows/deploy.yml`).

## stories.json format
```json
{
 "updated": {"en": "Updated 24 Nov 2026, 7:00 AM IST", "te": "నవీకరణ: 24 నవం 2026, ఉ. 7:00"},
 "date":    {"en": "Tuesday, 24 November 2026", "te": "మంగళవారం, 24 నవంబర్ 2026"},
 "ticker":  [{"en": "Sensex", "te": "సెన్సెక్స్", "v": "83,676 −244"}, {"en": "Brent", "te": "బ్రెంట్", "v": "$92.34", "up": 1}],
 "chart":   null,
 "stories": [
  {"s": "business", "lead": 1, "when": {"en": "Mon, 23 Nov", "te": "సోమ, 23 నవం"},
   "en": {"h": "Headline", "p": "2–4 sentence summary"},
   "te": {"h": "శీర్షిక", "p": "2–4 వాక్యాల సారాంశం"},
   "src": [["Source name", "https://..."]]}
 ]
}
```
- `s` is one of: business, technology, sports, entertainment. Exactly one story has `"lead": 1`.
- `ticker` `up: 1` colours a value green (rise); omit for falls. Use "−" (minus sign) for falls.
- `chart` is optional (null to hide). Shape: `{"title":{en,te},"sub":{en,te},"note":{en,te},"unit":"%","bars":[{"en":"Nifty","te":"నిఫ్టీ","w":{"en":"India, Mon","te":"భారత్, సోమ"},"v":-0.43,"hi":true}]}` — `v` negative = fall, positive = rise.

## Editorial rules
- 12–16 stories: at least 3 per section. Business leans India markets/economy; Entertainment leans Telugu cinema; Sports leans cricket/Indian sport; Technology covers AI, phones, apps, Indian tech.
- Every fact comes from a source fetched during the update, linked in `src` (1–3 links). No invented numbers, quotes or events.
- Write in your own words. No copied sentences; no direct quotes longer than a few words.
- Telugu must be natural, simple Telugu (not word-for-word translation). Keep names, numbers and tickers identical in both languages.
- Neutral tone. Politics only as plain fact, both sides fairly. No insurance or product ads.
- Prefer news from the last 24–36 hours; drop stories older than ~4 days.
