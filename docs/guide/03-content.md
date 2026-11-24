# 3. Pages, services and blog posts

Business Website Template by The Diamond Empire, https://thedempire.shop/

The words of the site live in plain files in `content/`. You do not need to touch the code to change them.

## Edit the words

| File | Page |
|---|---|
| `content/home.json` | Home page: headline, values, process steps, testimonials, closing call to action |
| `content/services.json` | The services page and one page per service |
| `content/pricing.json` | Pricing: packages, comparison table, questions |
| `content/about.json` | About: story, values and team |
| `content/posts/*.mdx` | Blog posts |

JSON files are strict: keep the quotation marks, commas and brackets as they are and change only the text. When the site is built, every file is checked, and a mistake stops the build with a message that names the file and the field.

## Add a service

1. Open `content/services.json`.
2. Copy one whole service block (from `{` to `}`) and paste it after the last one, with a comma between them.
3. Change the `slug` (lower-case letters, numbers and hyphens, for example `annual-review`), the `title` and the other fields.
4. Choose an `icon` from this list: compass, gears, diamond, path, tag, people, focus, scale, heart.

The new service gets its own page at `/services/your-slug/`, a card on the services page, an entry in the sitemap and a link in the "Other services" list. Nothing else needs to change.

## Add a blog post

1. Create a file in `content/posts/` named after the address you want, for example `how-we-plan-a-year.mdx` (it becomes `/blog/how-we-plan-a-year/`).
2. Start it with front matter, then write the post:

```text
---
title: How we plan a year in one afternoon
description: A short summary of the post, 50 to 180 characters, shown in search results.
date: 2026-11-03
tags: [strategy, planning]
author: amara-osei
---

## First heading

Your text. Use **bold**, *italic*, lists and [links](https://example.com/).
```

Rules:

- If the title or description contains a colon, put the whole text in double quotes, for example `title: "Pricing: a simple guide"`.
- `date` is written year-month-day.
- `author` must be one of the ids listed in `authors` in `site.config.ts`.
- `tags` creates the tag pages automatically. Use a few consistent tags rather than many one-off ones.
- Start at a second-level heading (`##`). The title is the page's first-level heading, so do not write `# ` in the body.
- To update a post later, add `updated: 2026-12-01` to the front matter. Search engines see the new date.

The post appears on the blog page, on its tag pages, in the sitemap and in the RSS feed. There is no pagination: if you publish many posts, ask a developer to add it.

### The Callout box

Inside a post you can write a highlighted note:

```text
<Callout title="Try this">
Text of the note.
</Callout>
```

To add your own component, add it to `mdxComponents` in `src/lib/mdx.tsx`.

## Add a new page

1. Copy a folder in `src/app/`, for example `src/app/about/`, to `src/app/your-page/`. Edit `page.tsx` and its `.module.css` file.
2. Give it metadata with `pageMetadata({ title, description, path: '/your-page/' })`, a `PageHero` (it holds the page's one `<h1>`) and a breadcrumb trail like the other pages.
3. Add its address to the `STATIC_PAGES` list in `src/lib/routes.ts` so it goes in the sitemap.
4. Add a link to `nav` (and `footerNav`) in `site.config.ts` if it belongs in the menus.
5. Use addresses that end with a slash, for example `/your-page/`.

## Remove what you do not need

- Delete a service from `content/services.json` and the page, card and sitemap entry go with it.
- Delete a post file to remove the post. Make sure nothing else links to it.
- To drop a whole page, delete its folder in `src/app/`, remove it from `STATIC_PAGES` in `src/lib/routes.ts` and remove it from the menus.

## Check your work

Run `npm run check`, then `npm run build` and look through the result with `npm run serve`. Every link on the site should lead somewhere.

Next: [Connect the contact form](04-connect-the-contact-form.md).
