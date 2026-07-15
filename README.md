# who-am-we-web

Static asset origin for the WHO AM WE installation. Served via Cloudflare
Pages at **https://assets.who-am-we.com/**.

## What's here

```
mark.png                                # WHO AM WE mark, cream (#FBF9D9 on transparent) — dark-mode
mark-inverse.png                        # WHO AM WE mark, dark  (#0a0a0a on transparent) — light-mode
fonts/pp-fraktion-mono/                 # PP Fraktion Mono OTFs referenced by email templates
  PPFraktionMono-Regular.otf
  PPFraktionMono-Bold.otf
```

## Consumers

- **Email templates** (`server/services/email_templates/beginning.html`,
  `circulation.html`) — both mark variants ship in every email as two
  `<img>` tags with `.light-mode-image` / `.dark-mode-image` classes; a
  `@media (prefers-color-scheme: dark)` block in the template CSS toggles
  `display` so the correct-contrast mark renders on the recipient's chosen
  mode. Fonts are pulled via `@font-face` from
  `https://assets.who-am-we.com/fonts/pp-fraktion-mono/*.otf`.
  Server-side base URL is the `EMAIL_FONT_BASE_URL` env var
  (default in `server/config.py`).

## Deploy

Cloudflare Pages watches this repo's default branch. Any push updates the
edge-cached asset origin. No build step.
