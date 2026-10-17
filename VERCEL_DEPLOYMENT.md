# Deploy GoCart on Vercel

## Deploy
1. Extract this ZIP and push the contents of the `gocart-main` folder to a GitHub repository.
2. In Vercel, choose **Add New → Project** and import that repository.
3. Framework preset: **Next.js**. Root Directory: the repository root (the folder containing `package.json`).
4. Build command: `npm run build` (default). Install command: `npm install` (default).
5. Confirm the Node.js version is **24.x** in Vercel Project Settings → General → Node.js Version (if shown).
6. Deploy.

The old npm lockfile has been removed because it pinned Next.js 15.3.5. Run `npm install` locally before committing if you want to generate a fresh `package-lock.json`; do not reuse the old lockfile.

## Environment variables
The UI defaults to `$` if the currency variable is not set. To change it, add this in Vercel → Project → Settings → Environment Variables:

- `NEXT_PUBLIC_CURRENCY_SYMBOL` = `$` (or your preferred symbol, e.g. `₹`)

The Prisma schema references `DATABASE_URL` and `DIRECT_URL`, but the current project UI uses local demo data and does not require a database just to build/deploy. If you add database-backed functionality later, configure both variables with valid PostgreSQL connection strings and run the appropriate Prisma migrations.

## Notes
- Use Node.js 24.x (the project is configured for Node.js 24 and Next.js 16.4.2).
- Do not upload `.env`, `node_modules`, `.next`, or `.vercel` to GitHub.
- This project currently uses demo/local state for its store data; deployment does not automatically add real authentication, payment processing, or persistent orders.
