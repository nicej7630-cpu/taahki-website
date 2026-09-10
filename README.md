# Taahki Health Center — Website Setup

This folder has everything you need to put the site live on your own domain, for free.

## Files
- `index.html` — the website itself
- `doctors.json` — the list shown in "Meet the team." Edit this file any time to add, remove, or rename doctors. No coding needed — just edit the text between the quotes.

## Step 1 — Put it on GitHub
1. Create a free account at github.com if you don't have one.
2. Create a new repository (e.g. `taahki-website`). Make it Public.
3. Upload `index.html` and `doctors.json` into it (drag and drop works on GitHub's website).

## Step 2 — Turn on GitHub Pages
1. In your repository, go to **Settings → Pages**.
2. Under "Source," choose the `main` branch and `/root` folder, then save.
3. GitHub gives you a link like `https://yourusername.github.io/taahki-website/` — that's your site, live, within a minute or two.

## Step 3 — Connect your own domain
1. Buy your domain (e.g. from Namecheap, GoDaddy, or a local Lebanese registrar) if you don't already have one.
2. In your repository, go to **Settings → Pages → Custom domain** and type your domain (e.g. `taahkihealth.org`).
3. At your domain registrar, add these DNS records (exact steps vary slightly by registrar):
   - For a domain like `taahkihealth.org`: four **A records** pointing to GitHub's IP addresses (GitHub's Pages docs list the current ones — search "GitHub Pages custom domain A records").
   - For `www.taahkihealth.org`: a **CNAME record** pointing to `yourusername.github.io`.
4. DNS changes can take a few hours to fully apply. Once they do, check "Enforce HTTPS" back in GitHub Pages settings so the site loads securely.

## Step 4 — Make the appointment form actually deliver emails
Right now the form points to a placeholder. To make it real:
1. Go to formspree.io and create a free account.
2. Create a new form and set the delivery email to whichever inbox should receive appointment requests.
3. Formspree gives you a form ID. Open `index.html`, find this line near the appointment form:
   ```
   <form id="apptForm" action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
   ```
4. Replace `YOUR_FORM_ID` with the ID Formspree gave you. Save and re-upload the file to GitHub.
5. Submit a test appointment on your live site to confirm the email arrives.

## Step 5 — Set up a support email address
GitHub Pages hosts the website only — it doesn't include email. Once your domain is active:
1. Sign up for a mail provider that supports custom domains — Zoho Mail has a solid free tier for one domain; Google Workspace is a paid option with more features.
2. Create an address like `support@taahkihealth.org`.
3. Add that address to the Contact section of `index.html` wherever you'd like it shown.

## Updating the doctor list later
Open `doctors.json` on GitHub, click the pencil (edit) icon, and add or edit entries in this format:
```json
{
  "name": "Dr. First Last",
  "role": "Their specialty or title",
  "note": "One short line about their focus"
}
```
Keep the commas between entries and the square brackets `[ ]` at the very top and bottom. Commit the change, and the live site updates automatically within a minute.
