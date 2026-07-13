# US Market Review Dashboard

Prepared for Alireza Talebi.

## Files
- `us_market_dashboard.html` — main dashboard. Rename to `index.html` for GitHub Pages.
- `client_portfolio.json` — default portfolio source loaded by the dashboard when hosted in the same folder.
- `client_portfolio_sample.json` — sample client portfolio template.

## Portfolio source format
JSON:
```json
{
  "client_name": "Client Name",
  "as_of_note": "Optional note",
  "holdings": [
    {"symbol": "MSFT", "name": "Microsoft", "quantity": 40, "bought_at": 390.00}
  ]
}
```

CSV columns accepted:
`symbol,name,quantity,bought_at`

Aliases also accepted: `ticker`, `company`, `shares`, `cost_basis`, `cost`, `purchase_price`.

## Data behavior
- Prices refresh every 15 minutes from Yahoo Finance chart endpoints.
- QQQ and SPY overnight/extended-hours change is calculated from latest available quote versus prior close.
- 10Y yield uses `^TNX` and WTI crude uses `CL=F` from Yahoo.
- Portfolio news uses Google News RSS for the last 18 hours through a public CORS proxy.
- Headlines are flagged if they contain: guidance, downgrade, SEC, earnings, CEO.
- Earnings data is best-effort from Yahoo quoteSummary. For a production client dashboard, connect a licensed estimates/earnings calendar provider for consensus EPS and prior 4Q beat/miss.

## Hosting note
When opening the HTML directly from your computer, the browser may block reading `client_portfolio.json`. Use the Upload File button, or host the HTML and JSON together through GitHub Pages or another static web host.
