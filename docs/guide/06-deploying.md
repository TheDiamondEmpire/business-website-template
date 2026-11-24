# 6. Deploying

Business Website Template by The Diamond Empire, https://thedempire.shop/

The built site is a folder of plain files. Any place that can serve files over HTTPS can host it. No server software, database or special runtime is needed, and no particular provider is required.

## Build

1. Set your site address (guide 5), either in `site.config.ts` or with `SITE_URL` when you build.
2. Run:

```text
npm run build
```

3. The finished site is in the `out/` folder. Check it first with `npm run serve`.

## What to upload

Upload the **contents** of the `out/` folder to the root of the place that serves your site, so that `out/index.html` is served at `https://your-address/`. Upload everything, including the `_next/` folder, `404.html`, `sitemap.xml`, `robots.txt` and `rss.xml`.

The template does not support serving from a sub-folder of a domain (for example `https://example.org/site/`). Use a domain or a sub-domain.

## What your host needs to do

| Need | Why |
|---|---|
| Serve `folder/index.html` for the address `/folder/` | Every page is exported as a folder with an `index.html`, and every link ends with a slash. Almost every host does this by default. |
| Serve `404.html` for addresses that do not exist, with status 404 | The template includes a styled "page not found" page. |
| Serve files with their normal types: `.html`, `.css`, `.js`, `.svg`, `.xml`, `.txt` | The feed and sitemap must be served as XML. |
| Use HTTPS | Required for a trustworthy site and for the share links to work. |

### Caching

Files in `_next/static/` have names that change when their content changes, so they can be cached for a long time. HTML pages should be cached for a short time (or revalidated) so that updates appear quickly.

### The contact form

The form needs no server of its own. You connect it to a service in `src/lib/contact/adapter.ts` (guide 4).

### Redirects

If you are replacing an old site, set up permanent (301) redirects from the old addresses to the new ones in your host's settings. The static export does not create redirects.

## Update the site

Edit, run `npm run check` and `npm run build`, and upload the new `out/` folder. Upload the whole folder each time so that the page files and the `_next/` files stay in step.

## Launch checklist

- [ ] All sample names, prices, quotes, addresses, phone numbers and emails are replaced.
- [ ] `siteUrl` (or `SITE_URL`) is your real address, and `/sitemap.xml` and `/robots.txt` show it.
- [ ] The contact form is connected and a test message arrived without the "Demo" mark.
- [ ] `public/og-default.png` is your image and `public/favicon.svg` is your icon.
- [ ] You looked at every page at phone width, at desktop width, in the light theme and in the dark theme.
- [ ] You tried the site with the keyboard only: tab through a page, use the skip link, open a question on the pricing page.
- [ ] Contrast of your new colours is checked (guide 2).
- [ ] `npm run check` passes and `npm run build` finishes without errors.
- [ ] Your privacy notice names the contact-form provider, and any analytics you add.
- [ ] A staging copy, if you have one, is kept out of search results.

Next: [Accessibility and privacy](07-accessibility-and-privacy.md).
