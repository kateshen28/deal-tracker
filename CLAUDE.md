# DealTracker

Personalized daily deal & cashback aggregator dashboard for tracking Capital One Shopping rewards, Rakuten cashback, and store promotions across brands you actually shop at.

## Stack

- Language: HTML5, CSS3, Vanilla JavaScript
- Framework: None (single-page static dashboard)
- Data source: Gmail (via Claude MCP tools) — Capital One Shopping emails, Rakuten emails, order confirmations
- Deployed on: Local file (open in browser)

## Structure

- `index.html` — the entire dashboard (single file, self-contained)
- Data is embedded as JS objects at the top of the `<script>` block
- No build step, no dependencies, no server required

## Key Concepts

- **Deal Stacking**: Combining Capital One Shopping rewards + Rakuten cashback on the same purchase for maximum savings
- **Buy/Wait Signals**: Compares current reward rate to historical range. If rate is in top 25% of range → "Buy Now". If bottom 30% → "Wait"
- **Rate History**: Capital One Shopping reward rates fluctuate significantly (e.g., Dyson: 3.5%–24%). Tracking history reveals patterns
- **Brands Tracked**: Only brands the user has purchased from at least once (extracted from Gmail order confirmations)

## Data Update Process

To refresh deal data:
1. Use Gmail MCP tools to search for recent Capital One Shopping emails (`from:capitaloneshopping`)
2. Search for Rakuten emails (`from:rakuten`)
3. Extract current rates, expiration dates, and category breakdowns
4. Update the `capitalOneData` and `rakutenDeals` objects in index.html

## Conventions

- Keep everything in a single HTML file for portability
- Use CSS custom properties (variables) for theming
- Mobile-first responsive design
- No external CDN dependencies — everything inline
- Brand logos use favicon service for reliability
- All links open in new tabs (`target="_blank" rel="noopener"`)

## Don't

- Don't add a backend server — this is a static dashboard
- Don't add npm/node dependencies
- Don't split into multiple files unless the single file exceeds 2000 lines
- Don't hardcode colors — use CSS variables
- Don't remove existing deal data without confirmation

## Working with Me

- Ask before changing the data/deal information
- Keep the file openable by double-clicking (no build step)
- Test in browser after changes
- Prefer clean, modern UI with white background and subtle shadows
