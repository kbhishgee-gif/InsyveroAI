# InsyveroAI Phase 1 — optional real AI explanations

This version retains the Premium v3.1 marketing site and dashboard. The existing **local rule-based answers are the default**. Real AI is **not enabled automatically** and no API key is included.

## Deploy safely

1. Keep `index.html` in the root of the existing GitHub Pages repository. Upload the `backend/` folder to that repository too, or to a separate private repository.
2. Create a Python web service on Render (or a similar host) using `backend` as its root directory, build command `pip install -r requirements.txt`, and start command `uvicorn app:app --host 0.0.0.0 --port $PORT`.
3. Set backend **environment variables** `OPENAI_API_KEY` (secret), `FRONTEND_ORIGIN=https://kbhishgee-gif.github.io`, `ENABLE_PUBLIC_DEMO_AI=false`, and `OPENAI_MODEL=gpt-4.1-mini`. Do not commit `.env` files or API keys.
4. Confirm `https://YOUR-SERVICE.onrender.com/health` returns `ok:true` and `ai_enabled:false`.
5. In the root `index.html`, replace `https://YOUR-RENDER-SERVICE.onrender.com` in `AI_API_BASE` with your actual backend URL, then commit it to GitHub Pages.
6. When you are ready to test real model calls, change `ENABLE_PUBLIC_DEMO_AI` to `true` on the backend. Refresh the site and select **Enable connected AI** in the Ask AI workspace. Local mode still works if AI is unavailable.

## Security / cost cautions

- The frontend sends **only aggregated filtered values and the question**, not raw CSV rows, names, customer IDs, or full uploaded files. However, **product, region, and category labels** are included in aggregates; do not upload sensitive or confidential data to this public demo.
- This is a **public, unauthenticated demo**. CORS/origin checking is **not** authentication. The backend includes a basic per-IP 10 requests/hour limit, but this is insufficient for a public paid product or for strong protection against automated abuse. Keep AI disabled until you've set provider spending limits, monitored usage, and preferably added proper user authentication and server-side quotas. Do not promise users their data is private or securely stored.
- Real AI can make mistakes. Totals and calculations remain browser-derived; explanations must be reviewed.
- If you use Render's blueprint, note that `rootDir` points to `backend` and the blueprint itself is in `backend/render.yaml`; manual deployment may be simpler.

## Local test

```bash
cd backend
python -m pip install -r requirements.txt
uvicorn app:app --reload --port 8000
```

The `/health` endpoint should work without an API key. Real AI requests are off by default.
