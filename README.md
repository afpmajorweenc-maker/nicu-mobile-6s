# NICU Mobile 6S Audit PWA

This package contains an installable GitHub Pages front end and the matching
Google Apps Script backend for the NICU CQI Nurse and Midwife 6S audit.

## 1. Update Google Apps Script

1. Back up the existing Apps Script project.
2. Replace `Code.gs` with the supplied `Code.gs`.
3. Keep an `Index.html` file in Apps Script if you also want the original
   Apps Script-hosted page to continue working.
4. Run `setupSystem()` once from the Apps Script editor and authorize it.
5. Select **Deploy > Manage deployments**, edit the web-app deployment,
   choose **New version**, and deploy it as **Execute as me**.
6. For a technical demonstration, the GitHub front end requires an Apps Script
   deployment that accepts its cross-origin POST request. A deployment limited
   to signed-in Google users may redirect that request to a sign-in page and the
   static front end cannot verify the result. Do not make a clinical endpoint
   public merely to bypass this limitation; use an approved authenticated
   institutional backend or retain the Apps Script-hosted version instead.

If deployment produces a different `/exec` URL, replace `API_URL` near the top
of the script in `index.html` with that new URL.

## 2. Publish on GitHub Pages

1. Create a GitHub repository, for example `nicu-mobile-6s`.
2. Upload `index.html`, `manifest.webmanifest`, `service-worker.js`, and the
   complete `icons` folder to the repository root. Do not upload `Code.gs` to
   a public repository if it later contains confidential configuration.
3. Open **Settings > Pages** in the repository.
4. Under **Build and deployment**, select **Deploy from a branch**.
5. Select the `main` branch and `/ (root)`, then save.
6. Open the Pages URL after GitHub finishes publishing.

## 3. Add to an iPhone Home Screen

1. Open the GitHub Pages URL in Safari, not inside Messenger or another app.
2. Tap **Share**.
3. Tap **Add to Home Screen**.
4. Turn on **Open as Web App** if Safari displays that option.
5. Tap **Add**.

## Important safety and privacy note

GitHub Pages is public static hosting. Do not place patient information,
spreadsheet IDs, passwords, secret tokens, or private configuration in this
repository. The supplied cross-origin submission cannot read the Apps Script
response, so the page tells the user to confirm the new row in Google Sheets.
Pilot the system with fictitious data before operational use. For authenticated
clinical deployment and reliable confirmation, use an approved institutional
backend or keep the application entirely within Google Workspace.
