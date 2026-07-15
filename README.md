# who-am-we-web

Static asset origin for the WHO AM WE installation. Served via Cloudflare
Pages at **https://assets.who-am-we.com/**.

## What's here

```
mark.png                                # WHO AM WE mark (386×524, #FBF9D9 on transparent)
fonts/pp-fraktion-mono/                 # PP Fraktion Mono OTFs referenced by email templates
  PPFraktionMono-Regular.otf
  PPFraktionMono-Bold.otf
```

## Consumers

- **Email templates** (`server/services/email_templates/beginning.html`,
  `circulation.html`) — the mark is inlined via
  `<img src="https://assets.who-am-we.com/mark.png">`. Fonts are pulled via
  `@font-face` from `https://assets.who-am-we.com/fonts/pp-fraktion-mono/*.otf`.
  Server-side base URL is the `EMAIL_FONT_BASE_URL` env var
  (default in `server/config.py`).

## Deploy

Cloudflare Pages watches this repo's default branch. Any push updates the
edge-cached asset origin. No build step.
