# Student Project Tracker — live variant

This is the cloud-backed variant of the hands-on web app development project. It uses an Express server, Vercel for hosting, and Supabase PostgreSQL for shared project records. Unlike the SQLite version, this variant requires a PostgreSQL connection string and does not migrate local SQLite data.

## Hosted app

The hosted URL will be added after deployment. It has not been deployed yet.

## Run locally

Use Node.js 22, as specified in `package.json`.

1. Install the locked dependencies:

   ```powershell
   npm.cmd ci
   ```

2. Copy `.env.example` to `.env`. In `.env`, replace only the placeholder after `DATABASE_URL=` with your own Supabase transaction-pooler connection string. Keep `.env` private; do not put a real connection string in `.env.example` or publish it.

3. In your Supabase project, run [`schema.sql`](./schema.sql) to create the `projects` table.

4. Start the local server:

   ```powershell
   npm.cmd start
   ```

   Open <http://localhost:3000>.

`DATABASE_URL` is server-only. For a Vercel deployment, configure it in the Vercel project’s environment-variable settings; do not expose it to browser code.

## Data and access

There is no sign-in. All visitors use the same shared demo records and can make changes to them. Do not use this demo for private or sensitive project data.

The original deployer's Supabase and Vercel credentials are not included. To deploy a hosted copy, a reader must create and configure their own Supabase database and Vercel project, and supply their own `DATABASE_URL`. Local setup needs a Supabase database but does not require Vercel.

## Checks completed

- `npm.cmd ci` completed successfully. It reported an engine warning because this environment has Node.js 24.11.1; the project specifies Node.js 22.
- Confirmed `.env` is ignored by the repository rules and `.env.example` is allowed.
- The server and database connection have not been started or verified here; the local `.env` still contains its placeholder.
