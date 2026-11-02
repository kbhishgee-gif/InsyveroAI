# InsightAI — Business Analytics Portfolio Demo

Interactive dashboard for exploring fictional business sales data. Built as an MBA project and adapted for a public portfolio demonstration.

## Features
- CSV upload and built-in sample data
- Revenue, recorded cost, gross profit and margin calculations
- Interactive charts and filters, what-if scenario explorer, rule-based decision guidance
- Data-quality checks and exportable summary

## Public demo limitations
- This version intentionally disables connected AI. The assistant is **rule-based**, not a live generative model.
- Pricing and checkout previews are simulations; no payments or accounts exist.
- Demo data is fictional. Do not upload confidential business data.
- Gross profit is not net profit or available cash.

## Deploy
Upload `index.html` and the two CSV files to a static web host such as Cloudflare Pages or GitHub Pages. No Python backend, API key or paid hosting is required for this version.

## Development
The original local version used a Python server and OpenAI API for optional connected AI. That server is **not included** in this public deployment because a publicly exposed AI endpoint requires authentication, rate limiting, input validation, spending controls, secure secrets and monitoring.
