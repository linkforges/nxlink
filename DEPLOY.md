# Deploying `geotracker/apps/web` to Vercel (using Railway DB)

1. Push your repo to GitHub (branch of your choice).

2. In Vercel Dashboard, import the GitHub repository:
   - Select the repo and for **Root Directory** choose `geotracker/apps/web` (or leave blank since `vercel.json` at repo root sets `rootDirectory`).
   - Framework: Next.js (should be detected).
   - Build Command: `pnpm build` (or leave default).
   - Install Command: `corepack enable && pnpm install --frozen-lockfile` (recommended for pnpm monorepo).
   - Output Directory: `.next`

3. Add required environment variables in Vercel (Project → Settings → Environment Variables):
   - `DATABASE_URL` = the Railway Postgres connection string (copy from Railway dashboard).
   - If your web needs an API URL, add `NEXT_PUBLIC_API_URL` pointing to your API host.

4. Deploy: Trigger a deployment from Vercel (via UI or push to the connected branch).

5. Local testing (from repo root):
```powershell
corepack enable
pnpm install --frozen-lockfile
cd geotracker\apps\web
pnpm build
pnpm start
```

Notes:
- `vercel.json` at repo root already sets `rootDirectory` to `geotracker/apps/web` and adds an `installCommand` for pnpm.
- Do NOT put actual secrets into the repo; use Vercel environment variables for production values.
