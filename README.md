# ogerek-products

**ogerek.com** — a home for Ogerek's business products: the home page lists the products and
each product lives under **ogerek.com/&lt;product&gt;**. Served by a Cloudflare Worker with static
assets (`ogerek.com/*`). More specific routes, such as the SnapTable license API at
`ogerek.com/snaptable/api/*`, are handled by their own Workers.

| Path | Content |
| --- | --- |
| [ogerek.com](https://ogerek.com/) | Products home page |
| [ogerek.com/snaptable](https://ogerek.com/snaptable/) | SnapTable AI — Chrome extension that scrapes tables & lists ([source](https://github.com/sertelemre/snaptable)) |

```
public/
  index.html              products home page (add a card per product)
  404.html
  assets/ogerek.css
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
npm run deploy    # publishes and (re)attaches the ogerek.com/* routes
```

## Adding another product

1. Put its pages in `public/<product>/`.
2. Add a product card to `public/index.html` (copy the SnapTable one).
3. `npm run deploy`.

## SnapTable go-live checklist

- `public/snaptable/index.html`: the "Get SnapTable Pro" button still points to the Creem **test** payment link — replace it with the live link.
- Confirm the contact address (`hello@ogerek.com`) receives mail, and review the refund policy (14-day money-back on the first payment).
