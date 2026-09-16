# RBN FIX HUB — Quotations & Invoices

A self-contained, offline-first quotation and invoice generator built for **RBN FIX HUB** (Sales & Service). No server, no build step, no login required — everything runs in the browser and saves to `localStorage` on the device you use it on.

## Features
- Create, edit, list, search, filter, sort and paginate Quotations & Invoices
- Live-updating A4 quote-paper preview matching a printed invoice layout
- Per-item Discount / GST / Adjustment / Round-off / Advance-payment handling
- Download as PDF (via jsPDF + html2canvas) or Print directly
- Send via Gmail (opens a pre-filled Gmail compose window — attach the downloaded PDF manually, since a browser page can't attach files to an email automatically)
- Company profile, logo/seal/hero image, and document numbering settings
- One-click JSON backup export, plus **Merge** (combine an old backup into current data) and **Full Restore** (overwrite everything)
- Light/dark theme toggle, mobile-responsive layout

## Hosting on GitHub Pages
1. Create a new GitHub repository and push these files (`index.html`, `README.md`) to the `main` branch.
2. In the repo, go to **Settings → Pages**.
3. Under "Build and deployment", set **Source** to `Deploy from a branch`, branch `main`, folder `/ (root)`.
4. Save — GitHub will give you a URL like `https://<username>.github.io/<repo-name>/` within a minute or two.

No other configuration is needed — this is a single static HTML file.

## Important limitations (by design, not a bug)
- **Data is per-browser, per-device.** Everything is stored in `localStorage`. Clearing browser data, using a different browser, or a different device will not show the same records. Use **Settings → Backup, Restore & Merge → Download Master Backup** regularly, and use **Merge** to combine records from another device/browser.
- **Gmail sending is manual-attach.** Browsers can't attach files to an email via a link — the app downloads the PDF and opens a pre-filled Gmail window; you attach the file yourself.
- **No user accounts.** This is a single-operator tool with no login system, matching the original page as supplied.

## Fixes made while preparing this build for hosting
- Fixed a JavaScript error (`scale is not defined`) in the window-resize handler that broke the live quote-paper resizing.
- Fixed a print CSS conflict that caused the **Print** button on the New Quotation/Invoice form to print a blank page (an `!important` rule was hiding the quote paper along with the rest of the form).
- Replaced a broken relative favicon link (`../icons/icon-192.png`, which pointed to a folder that isn't part of this page) with a self-contained emoji favicon.
- Removed a non-functional "Log out" button left over from a larger multi-page version of the app that included a login system — this standalone page has no login, so the button did nothing.
- Hardened `localStorage` writes with a try/catch so a full/blocked storage quota shows a console warning instead of a silent crash.
