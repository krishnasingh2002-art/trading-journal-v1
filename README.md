# Trading Process Journal V2

V2 keeps the original local-first workflow and adds only two long-term durability upgrades:

1. **Screenshots move out of localStorage into IndexedDB** so image-heavy journals do not consume the browser's small key/value quota.
2. **Optional private Supabase backup** for cross-device recovery. Journal records live in a private Postgres row and screenshots live in a private Storage bucket. GitHub Pages still hosts only the app code.

The app is intentionally **not** real-time collaborative and does not automatically overwrite the cloud on every keystroke. Use **Backup / Sync now** after a session or review. This keeps the data model simple and avoids silent cross-device conflicts.

## One-time Supabase setup

1. Create a Supabase project.
2. In **SQL Editor**, run `supabase.sql` from this folder.
3. In Supabase **Authentication**, keep Email enabled. If email confirmation is enabled, confirm the account email after creating it.
4. In the journal's Settings page, enter the project URL and the publishable/anon browser key.
5. Create/sign in to your journal account.
6. Tap **Backup / Sync now**.

The SQL enables Row Level Security and restricts both the database snapshot and screenshot objects to the authenticated user's own `auth.uid()`. Supabase's security model requires RLS plus appropriate grants/policies for exposed tables.

## Cross-device workflow

- Device A: work normally → Settings → **Backup / Sync now**.
- Device B: open the same GitHub Pages app → enter the same Supabase URL/key → sign in → **Restore from cloud**.
- Screenshots are downloaded back into that device's IndexedDB.

## Existing V1 data

On first launch, V2 automatically migrates any old base64 screenshots found in the V1 journal into IndexedDB. Trade records remain in the same local journal structure.

## Important

- Do **not** put the Supabase `service_role` key in the website. Use only the browser-safe publishable/anon key.
- Do **not** make the screenshot bucket public.
- The GitHub repository remains safe to make public because journal records and screenshots are not committed there.
- Supabase Free currently includes 500 MB database, 1 GB file storage, and 5 GB egress. Free projects can pause after a period of inactivity, so this is a backup layer, not a guarantee of zero-maintenance production infrastructure.
