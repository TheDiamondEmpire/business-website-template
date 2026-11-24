# 5. SEO

Business Website Template by The Diamond Empire, https://thedempire.shop/

The template builds in the technical basics. It cannot give you good rankings: those depend on your content, your market and time. What it does is remove the common technical mistakes.

## What is built in

| Feature | Where it comes from |
|---|---|
| A unique title and description on every page | `pageMetadata()` in `src/lib/seo.ts`, called by every page |
| A canonical link on every page | The same function, built from your site address |
| Open Graph and Twitter card tags | The same function; the image is `public/og-default.png` |
| `sitemap.xml` | `src/app/sitemap.ts`, from the page list in `src/lib/routes.ts` |
| `robots.txt` | `src/app/robots.ts` |
| An RSS feed at `/rss.xml` | `src/app/rss.xml/route.ts`, from your blog posts |
| Structured data (JSON-LD) | `Organization` on every page, `BreadcrumbList` on every inner page and `BlogPosting` on every post, from `src/lib/jsonld.ts` |
| One `<h1>` per page, a sensible heading order and a language on `<html>` | The page components |
| Fast, small pages | Static files, no tracking scripts, system fonts and inline SVG artwork |

## Set your site address

Canonical links, the sitemap, robots.txt, the feed and the structured data all use one public address. Set it in one of two ways:

1. Edit `siteUrl` in `site.config.ts`, for example `https://www.yourbusiness.com` (no trailing slash).
2. Or set the `SITE_URL` environment variable when you build, which overrides the file: `SITE_URL=https://www.yourbusiness.com npm run build` (on Windows PowerShell: `$env:SITE_URL='https://www.yourbusiness.com'; npm run build`).

The sample address `https://www.example.com` is a reserved example that no one owns. Pages built with it point search engines to a site that does not exist, so never publish with it.

## Titles and descriptions

- A page title is the page's name plus your brand name, for example "Pricing | Your Business". If the combination is longer than 70 characters, the page name is used on its own.
- Write each description in your own words, about 50 to 160 characters, and make it different on every page. Descriptions for service pages come from `content/services.json`, for posts from the front matter, and for the other pages from their JSON files.
- Do not use the same title or description on two pages.

## Structured data

Search engines may use the structured data to show richer results. Check what is on a page by opening its source and searching for `application/ld+json`. In `site.config.ts` you can add your social profile addresses to `social` and they are added to the `Organization` entry. If you add more types (for example a local business address or a product), keep the data true and visible on the page.

## The share image

When someone shares a page, social networks show `public/og-default.png` (1200 by 630 pixels). Replace it with your own image. Pages that need a different image can pass one to `pageMetadata` in a later version of your code.

## After you publish

1. Open `https://your-address/sitemap.xml`, `/robots.txt` and `/rss.xml` and check that they load and use your address.
2. Add your site to the search engines' webmaster tools and submit `sitemap.xml`.
3. Open a few pages, view the source and check the canonical link.
4. Keep staging copies out of search results: serve them with a password, or change `allow: '/'` to `disallow: '/'` in `src/app/robots.ts` for that copy only. Never keep a disallow rule on the live site.

Next: [Deploying](06-deploying.md).
