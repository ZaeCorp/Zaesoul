# ZAE SOUL

Static GitHub Pages site for the ZAE SOUL SPF pre-launch waitlist.

## Waitlist Webhook

The Google Apps Script endpoint is configured in `index.html`:

```js
const WAITLIST_ENDPOINT = "https://script.google.com/macros/s/.../exec";
```

The submitted Stitch URL was a redirected `script.googleusercontent.com/macros/echo` URL. The live form uses the corresponding Apps Script `/exec` URL because Google Apps Script POST handlers execute from `/exec`; the `googleusercontent` echo URL only accepts `GET`/`HEAD`.

To rotate the endpoint, replace that constant and redeploy by pushing to `main`.

## Google Sheet Columns

The waitlist form submits JSON with these fields:

- `createdAt`
- `name`
- `email`
- `skinType`
- `spfProblem`
- `country`
- `instagram`
- `source`
- `consent`

The hidden anti-spam honeypot field is named `website`. If it is filled, the site silently shows the success message and does not submit a row.

## Testing The Form

Open the site locally, fill out the required fields, accept consent, and submit. A successful submission shows:

> You’re on the ZAE SOUL early list. We’ll send sample testing updates soon.

Check the connected Google Sheet for the new row and confirm each submitted field maps to the columns above.

## GitHub Pages

This repo is a static site deployed from the `main` branch. The custom domain is set in `CNAME` as:

```text
zaesoul.com
```

Pushing changes to `main` updates the GitHub Pages site.
