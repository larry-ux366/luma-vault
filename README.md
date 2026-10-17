# Luma — My Passwords

The GitHub Pages entry page opens a private Google Apps Script web app. The web app reads and updates one Google Sheet, so the same list is available on phone and computer when signed into the owner's Google account.

## Use
Open the GitHub Pages site and select **My Passwords ဖွင့်ရန်**. Sign into the authorized Google account. The Apps Script deployment is owner-only. There is no separate master password for this Sheet-connected version.

Account passwords remain readable in the private Google Sheet; this version does not provide client-side encrypted cloud storage. No passwords or account records are committed to this repository.

The previous encrypted browser-local app is preserved as `local-vault.html`. Existing localStorage is retained on the same GitHub Pages origin. Old local records are not automatically imported into the Sheet; open the old app from the entry page's backup section to export them.

## Validation
The deployed web app loaded the 19 existing account records successfully. Source syntax checks passed. Search and the add-account dialog were checked without changing real account data.
