# wugweb-x backups (private)

Weekly schema + data dumps of the shared Supabase project `wugweb-x`, and a keep-alive so the free
plan never pauses. Must stay **private**: the data dumps contain personal data.

## Setup
1. Create this as a **private** GitHub repo and push these files.
2. Settings → Secrets and variables → Actions → New repository secret:
   - `SUPABASE_DB_URL` = the **Session pooler** connection string from Supabase → wugweb-x → Connect,
     with the database password filled in. Nothing else is needed.
3. Actions → run `keepalive` and `backup` once by hand to check them.

## Schedules
- `keepalive`: every 3 days, one small query.
- `backup`: Sundays, `dumps/YYYY-MM-DD/{schema,data}.sql.gz` plus a list of Storage objects.
  Uploaded files themselves live in Supabase Storage (not in tables, not in these dumps).
