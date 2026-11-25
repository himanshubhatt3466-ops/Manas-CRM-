# Manas CRM – College Admission Lead Management

GitHub Pages-ready static CRM for one college, one administrator and up to 50,000 lead records.

## Included
- Dashboard with total/new/due/converted metrics and status overview
- Add, edit, delete, search and filter admission leads
- Duplicate mobile-number check
- Lead source, course, qualification, priority, notes and follow-up date/time
- Follow-up centre and course-wise reports
- CSV import/export
- JSON local backup and restore
- IndexedDB local browser database
- Optional Google Drive backup via OAuth using Drive `appDataFolder`

## Deploy
1. Create a GitHub repository named `manas-crm`.
2. Upload `index.html`, `styles.css`, `app.js`, and this README to the repository root.
3. Go to Settings → Pages.
4. Select Deploy from a branch → `main` → `/(root)` → Save.
5. Open the GitHub Pages URL.

## Configure Google Drive backup
1. In Google Cloud Console create/select a project and enable Google Drive API.
2. Configure the OAuth consent screen and add your account as a test user if the app is in testing.
3. Create OAuth Client ID → Web application.
4. Add the exact GitHub Pages origin (example `https://YOURNAME.github.io`) to Authorized JavaScript origins.
5. In Manas CRM → Settings, paste the OAuth Client ID ending in `.apps.googleusercontent.com` and save.
6. Go to Backup & Restore → Connect Google → authorize → Backup to Drive.

Only the OAuth Client ID is placed in this static app. Never publish a client secret or service-account key. The app requests `drive.appdata` scope and stores backup snapshots in the hidden app-data folder. Reconnect after reloading the page; tokens are kept in memory.

## Important limitations
- GitHub Pages is static hosting; there is no server database or private backend.
- Records live in the browser's IndexedDB on that device/browser. They are not automatically shared across devices. Download backups regularly.
- Google Drive backup is a manual snapshot upload, not continuous sync or automatic restore.
- Admin-only means one local administrator interface, not secure server-side authentication. Anyone using the same unlocked browser profile may access its records.
- For multiple staff, centralized access, strong authentication, audit logs and live sync, add a secure backend/database.
- Capacity is configured to 50,000 records; actual browser storage quotas vary by device and browser.
- Use HTTPS (GitHub Pages) for Google OAuth. Avoid storing sensitive documents or unnecessary personal information.

## CSV format
Required columns: `name,phone,course`. Optional: `email,qualification,source,status,follow,followdate,notes`. CSV import is on the Admission Leads page.
