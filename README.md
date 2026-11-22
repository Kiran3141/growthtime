# Daily 90m Growth Trainer — GitHub Pages Deploy Guide

## 1. Host on GitHub Pages (2 minutes)
1. Create a new GitHub repository (e.g. `daily-growth-trainer`).
2. Upload `index.html`, `manifest.json`, and `sw.js` to the root of the `main` branch.
3. Go to **Settings -> Pages -> Build and deployment -> Source: Deploy from a branch (`main` / `/root`)**.
4. Your live app will be at `https://<your-username>.github.io/daily-growth-trainer/` (and installable as a PWA on iPhone/Android!).

## 2. Optional: Collect Daily Logs in a Free Google Sheet
If you want to see what you or other folks are doing daily on your GitHub Pages site:
1. Create a Google Sheet -> **Extensions -> Apps Script**.
2. Paste this script and deploy as a **Web App** (Execute as: *Me*, Who has access: *Anyone*):
```javascript
function doPost(e) {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var data = JSON.parse(e.postData.contents);
  sheet.appendRow([data.ts, data.role, data.type, data.detail]);
  return ContentService.createTextOutput("OK");
}
```
3. Copy the `/exec` URL and paste it into **Profile & Setup -> Optional Cloud Analytics Webhook** inside the app.
