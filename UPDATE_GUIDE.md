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
- `s` is one of: business, technology, sports, entertainment, devotional. Exactly one story has `"lead": 1`.
- `ticker` `up: 1` colours a value green (rise); omit for falls. Use "−" (minus sign) for falls.
- `chart` is optional (null to hide). Shape: `{"title":{en,te},"sub":{en,te},"note":{en,te},"unit":"%","bars":[{"en":"Nifty","te":"నిఫ్టీ","w":{"en":"India, Mon","te":"భారత్, సోమ"},"v":-0.43,"hi":true}]}` — `v` negative = fall, positive = rise.

## Editorial rules
- 14–18 stories: at least 3 per section. Business leans India markets/economy; Entertainment leans Telugu cinema; Sports leans cricket/Indian sport; Technology covers AI, phones, apps, Indian tech.
- Devotional (ఆధ్యాత్మికం): 2–4 stories on Telugu festivals and temples — during Karthika Masam (10 Nov–8 Dec 2026) focus on it: today's/upcoming observances (Somavarams, Pournami, Ekadashi, Kalabhairava Jayanti), major temple events and crowds (Srisailam, Vemulawada, Srikalahasti, Pancharamas, Keesaragutta, Yadadri, Tirumala), Koti Deepotsavam. After Karthika, cover the next festival season (Dhanurmasam, Vaikunta Ekadashi, Sankranti) and TTD/temple news. Report observances and dates as reported by sources; describe beliefs respectfully as traditions ("devotees believe…"), never as claims of fact; no astrology predictions.
- Every fact comes from a source fetched during the update, linked in `src` (1–3 links). No invented numbers, quotes or events.
- Write in your own words. No copied sentences; no direct quotes longer than a few words.
- Telugu must be natural, simple Telugu (not word-for-word translation). Keep names, numbers and tickers identical in both languages.
- Neutral tone. Politics only as plain fact, both sides fairly. No insurance or product ads.
- Prefer news from the last 24–36 hours; drop stories older than ~4 days.

## "This day" box (`today`) — every edition
```json
"today": {"title": {"en": "...", "te": "..."},
  "significance": {"en": "3–4 sentences", "te": "..."},
  "history": [{"y": "1926", "en": "...", "te": "..."}],
  "src": [["Source", "https://..."]]}
```
- `significance`: why today matters for Telugu readers — the tithi/festival/observance (with its tradition and meaning), and any notable anniversary (jayanti, punyatithi, national/international day). Dates must come from fetched sources.
- `history`: 3–5 verified events that happened on this calendar date (India and Telugu states first), oldest first. Each must be verifiable from a fetched source listed in `src`.

## Spirituality column (`column`) — new each morning, kept in the evening
```json
"column": {"by": {"en": "Susthira News desk", "te": "సుస్థిర న్యూస్ డెస్క్"},
  "verse": {"en": "transliteration", "te": "తెలుగు లిపిలో శ్లోకం", "ref": {"en": "Bhagavad Gita 2.47", "te": "భగవద్గీత 2.47"}},
  "en": {"h": "Title", "body": ["para", "para", "para", "para"]},
  "te": {"h": "శీర్షిక", "body": ["...", "...", "...", "..."]}}
```
- 220–320 words per language, 3–5 short paragraphs, warm and simple. Telugu written naturally, not translated word for word.
- Draw on classical sources (Upanishads, Bhagavad Gita, Brahma Sutras, Yoga Sutras, saints like Annamayya, Vemana, Tyagaraja, Potana) and link to the season or day when possible. Quote only the short Sanskrit/Telugu verse (classical texts only), with its exact reference; never invent a verse or reference.
- Explain ideas as the tradition teaches them ("the Upanishads teach…"), end with one small practice for the reader. No predictions, astrology, miracle claims, health claims, or criticism of any faith.
- Byline stays "Susthira News desk". Change the column only in the morning edition; the evening edition keeps the morning column.
