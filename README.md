# A Money — legal pages

Static site serving the Privacy Policy and Terms of Service that the iOS app links to.

## These URLs are load-bearing

`AMoney/Features/Settings/SettingsView.swift` hardcodes:

- `https://tiennx.github.io/amoney/privacy`
- `https://tiennx.github.io/amoney/terms`

The shipped app already links them. If these paths stop resolving, the Settings screen links to nothing —
which is also an App Store review problem, since a working privacy policy URL is required for submission.
Changing a path means shipping an app update.

That is why the layout uses `privacy/index.html` rather than `privacy.html`: only the directory form serves
at `/privacy` without an extension.

## Do not edit these HTML files by hand

They are generated. The sources are `docs/legal/*.md` in the app repository, and the generator is
`tools/build-pages.py` there. It exists because:

- the source markdown carries an internal editorial header (how the document was written, which placeholders
  are outstanding) that must not be published;
- placeholder values must be identical across both documents;
- it exits non-zero while any placeholder is unresolved, so an incomplete legal document cannot be published
  by accident.

Edit the markdown, re-run the generator, copy `pages/` here.

## Publishing

This repository must be **public** — GitHub Pages on a private repository needs a paid plan. It deliberately
contains only these pages, not the app source.

Settings → Pages → Source: `main` branch, `/ (root)`.
