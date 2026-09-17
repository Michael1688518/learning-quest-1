# Learning Quest v3.1 — GitHub Pages upload version

CN / EN / DE trilingual responsive learning prototype for Kevin, Camilla, Daniel and Harry. Upload all six files in this folder to the repository root.

## Files
`index.html`, `harry_index.html`, `app.js`, `styles.css`, `content.js`, `README.md`

## Device behavior
Learning records are saved offline in browser `localStorage`, separated by learner. The UI is responsive for phones and computers.

## Cross-device cloud sync
v3.1 includes the sync UI and a safe cloud-sync architecture, but **does not embed credentials or silently create a backend**. To actually share records between phone and computer, create a Supabase project, use only its public anon key in the browser, enable authentication, create a `learning_records` table, and enforce Row Level Security so each signed-in parent can access only their own rows. Never put the service-role/admin key in GitHub Pages.

Suggested table columns: `id uuid primary key`, `user_id uuid`, `learner text`, `payload jsonb`, `updated_at timestamptz`. RLS should restrict rows with `auth.uid() = user_id`.

Until backend setup is completed, offline/local learning works normally but different devices do not synchronize.

## Validation
The release build is checked for JavaScript syntax, local HTML dependencies, required file presence, responsive viewport/media rules, and ZIP extraction integrity.
