# ASWF IG Live reminder page and calendar file

This repo is served by GitHub Pages. It holds two things:

| Path | Public URL | Role |
|---|---|---|
| `live/index.html` | https://ivyleaguelawyer.github.io/aswf-ig-live-calendar/live/ | **QR target.** The reminder page with "Set Instagram reminder" and "Add to Calendar". The poster sticker QR encodes this URL. |
| `aswf-ig-live.ics` | https://ivyleaguelawyer.github.io/aswf-ig-live-calendar/aswf-ig-live.ics | The event file. GitHub serves it as `Content-Type: text/calendar`, so iPhone shows the native "add event" sheet. |

## Why the page lives here

The page used to be a Muse artifact at `https://muse.ai/s/aswf-ig-live-reminder-wxh6wz8clxjxr8`,
and the first printed posters encode that URL directly. In October 2026, Meta retired every Muse
share link created before its sharing fix, so that URL now shows "This page is no longer shared."
Nobody but Meta controls a muse.ai URL. The page now lives on a URL we control, so the printed
sticker QR can be repointed without reprinting.

## Rules

- **Never rename or delete the `live/` folder, and never make this repo private.** Every printed
  sticker breaks if `.../live/` stops resolving.
- Keep the repo name `aswf-ig-live-calendar`. GitHub does not redirect Pages URLs after a rename.

## Change the event (reschedule or new Instagram link)

1. Edit `aswf-ig-live.ics` on `main`: DTSTART/DTEND in Pacific local time, bump DTSTAMP to now
   in UTC, keep CRLF line endings and lines under 75 characters.
2. Edit `live/index.html`: the `date-block` text and `aria-label`, the Instagram button `href`,
   and the `dates=` / `startdt=` / `enddt=` values in the Google and Outlook links
   (UTC = Pacific + 8 h in November, + 7 h in summer).
3. Commit. Pages redeploys in 1–3 minutes. Scan the sticker to confirm.

## Repurpose the QR after the live

Replace the whole contents of `live/index.html` with this, and change both URLs to the new
destination:

```html
<!doctype html>
<meta charset="utf-8">
<meta http-equiv="refresh" content="0; url=https://NEW-DESTINATION.example/">
<link rel="canonical" href="https://NEW-DESTINATION.example/">
<title>Redirecting…</title>
<a href="https://NEW-DESTINATION.example/">Continue</a>
```

## Optional: restore the ASWF logo

The page currently shows a text wordmark. To use the logo, upload `aswf-logo.png` (from
`flowb-fix/assets/` in the SEMA 2026 QR Code Plotter Giveaway Drive folder) to `live/assets/`,
then swap the two `<span>` lines inside `.brand-lockup` in `live/index.html` for
`<img src="assets/aswf-logo.png" alt="ASWF — American Standard Window Film" width="600" height="172" />`.

Full background: `flowb-fix/MAINTENANCE.md` and `REMEDIATION.md` in the same Drive folder.
