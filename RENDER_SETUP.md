# Om Mavtar ERP — Render deployment

This package serves React and Express together, so `/api/auth/login` reaches the backend.

## Deploy
1. Upload these files to a **private GitHub repository**. Do not use a public repository because the original project includes `data/users.json` with plaintext credentials.
2. In Render, choose New > Blueprint, connect the repository, and select `render.yaml`.
3. Confirm a **paid Starter** web service and a persistent disk (free services do not support persistent disks).
4. Deploy and open the assigned `onrender.com` URL. Test login and inventory saves.
5. After testing, in Render Settings > Custom Domains add `mavtarexport.in` and follow Render's exact DNS instructions in GoDaddy. Remove conflicting old website records only after verifying the new deployment.
6. Migrate real records separately. The ZIP includes seed/sample records and user accounts; it is NOT an export of Cloud Run's live data.

## Data
`DATA_DIR=/var/data` points ERP JSON, users and history files at the Render persistent disk. Back up this disk regularly; a persistent disk is not a backup.

## SECURITY — MUST FIX BEFORE PRODUCTION
The supplied code has plaintext passwords, predictable demo credentials, unauthenticated user-management/data API endpoints, and no server-enforced access checks. **Do not publish this as a production ERP containing real data** until backend authentication/authorization and password hashing are implemented and tested. The staff-email endpoint prepares an email but does not send it.

Do not assume existing Google Cloud data transfers automatically.
