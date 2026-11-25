# ogerek-products

Product pages served under **ogerek.com/&lt;product&gt;** — a Cloudflare Worker with static assets.
Only the routes listed in `wrangler.jsonc` are handled here; every other path on ogerek.com
still goes to the main Ogerek app.

| Path | Product |
| --- | --- |
| [ogerek.com/snaptable](https://ogerek.com/snaptable/) | SnapTable AI — Chrome extension that scrapes tables & lists ([source](https://github.com/sertelemre/snaptable)) |

```
public/
  snaptable/
    index.html            landing + pricing + FAQ
    thanks/               Creem return URL after checkout (how to activate the license)
    privacy/ terms/ refund/
    404.html
    assets/               css, icons, screenshot
```

## Develop & deploy

```bash
npm install
npm run dev       # http://localhost:8787/snaptable/
npm run deploy    # publishes and (re)attaches the ogerek.com/snaptable* routes
```

## Adding another product

1. Put its pages in `public/<product>/`.
2. Add `{ "pattern": "ogerek.com/<product>*", "zone_name": "ogerek.com" }` (and the `www.` variant) to `routes`.
3. `npm run deploy`.

## SnapTable go-live checklist

- `public/snaptable/index.html`: the "Get SnapTable Pro" button still points to the Creem **test** payment link — replace it with the live link.
- Confirm the contact address (`hello@ogerek.com`) receives mail, and review the refund policy (14-day money-back on the first payment).
