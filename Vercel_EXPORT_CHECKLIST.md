# Vercel Export & Deploy Checklist

1. Prepare GitHub
   - Push your changes to the `main` branch (or update `.github/workflows/vercel_export.yml` branch filter).
   - Add GitHub Secret `VERCEL_TOKEN` (Vercel Personal Token).

2. Vercel Project Setup
   - Import the GitHub repo in Vercel.
   - Ensure `vercel.json` at repo root points `rootDirectory` to `geotracker/apps/web`.
   - Set `Install Command` to `corepack enable && pnpm install --frozen-lockfile` if Vercel doesn't pick it.
   - Set `Build Command` to `pnpm build` and `Output Directory` to `.next`.

3. Environment Variables
   - Add `DATABASE_URL` from Railway under Project Settings → Environment Variables.
   - Add any other required env vars (e.g., `NEXT_PUBLIC_API_URL`) for preview/production.

4. Deploy
   - Trigger deployment in Vercel dashboard or push to the configured branch.
   - Monitor build logs for pnpm install and `next build` success.

5. Verify
   - Visit the deployed URL and check API calls and DB connectivity.
   - If DB connection fails, confirm `DATABASE_URL` is correct and accessible from Vercel.
