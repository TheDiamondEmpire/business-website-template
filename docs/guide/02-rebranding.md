# 2. Rebranding

Business Website Template by The Diamond Empire, https://thedempire.shop/

A rebrand is a few lines in two files: `site.config.ts` (names and details) and `src/styles/tokens.css` (colours, type and spacing). No component needs to change.

## Names and details: `site.config.ts`

| Setting | What it changes |
|---|---|
| `name` | The brand name in the header, footer, page titles, structured data and form text. |
| `shortName`, `legalName` | The short name and the legal name (shown in the footer copyright line). |
| `tagline`, `description` | The line in the footer and the default description for search results. |
| `siteUrl` | The public address of the finished site (see guide 5). |
| `locale`, `language` | Language settings such as `en_GB` and `en-GB`. |
| `contact` | Email, phone, address and opening hours shown in the footer and on the contact page. |
| `contactTopics` | The choices in the contact form's topic list. |
| `nav`, `footerNav`, `cta` | The navigation links and the main button. |
| `authors` | The people who can be named as the author of a blog post. |
| `ogImage`, `themeColor` | The image shown when pages are shared and the browser colour on phones. |

## Colours, type and spacing: `src/styles/tokens.css`

Every colour on the site is a token at the top of this file, for example `--accent` (buttons), `--text`, `--bg` and `--hero-bg` (the dark bands). Change the value and the whole site follows.

Two rules keep the site readable:

1. **Write colours as plain hex values** such as `#1e40a6`. They are easy to check and to copy to other tools.
2. **Write the dark theme values twice.** The file has three blocks: the light values, then the dark values inside a `prefers-color-scheme: dark` rule (for visitors whose device is set to dark), and then the same dark values for the theme toggle button (`data-theme='dark'`). CSS cannot share one block between the two, so when you change a dark value change both copies.

### Check contrast after you change colours

Text must be readable against its background. As a guide, ordinary text needs a contrast ratio of at least 4.5 to 1 and large text, borders of form fields and focus rings need at least 3 to 1. Check your new pairs with any contrast checker for these combinations, in both themes:

- `--text` and `--text-muted` on `--bg`, `--surface` and `--surface-2`
- `--accent-text` on `--bg` and `--surface` (links)
- `--accent-ink` on `--accent` (button labels)
- `--hero-text`, `--hero-muted` and `--hero-accent` on `--hero-bg`
- `--footer-text` and `--footer-muted` on `--footer-bg`
- `--danger` on `--bg` and `--surface` (error text)
- `--input-border` and `--focus` on the surfaces they sit on

Keep the browser theme colours in `site.config.ts` (`themeColor`) equal to your `--bg` values.

### Type

The site uses system font stacks (`--font-sans`, `--font-serif`, `--font-mono`), so there are no font files to download and no request to a font service. You can change the stacks. If you add your own font files, host them yourself in `public/` and note that every font file adds to the weight of each page.

The sizes (`--step-0` and up) scale smoothly with the width of the screen. Spacing tokens (`--space-1` to `--space-9`) set the gaps.

## Logo, favicon and artwork

- **Logo:** the gem in the header and footer is a small SVG component in `src/components/art/Logo.tsx`. Replace its shapes with your own logo, or replace the component.
- **Favicon:** replace `public/favicon.svg`.
- **Hero and 404 artwork:** `src/components/art/HeroArt.tsx` and `NotFoundArt.tsx` are generated placeholders drawn with SVG shapes and your colour tokens. Replace them with your own artwork when you have it.
- **Share image:** export your own 1200 by 630 pixel image to `public/og-default.png` with any design tool, and delete `public/og-default.svg` (it is only the source of the sample image). Most social networks do not accept SVG, so the PNG is the file that counts. If you use a different file name or size, update `ogImage` in `site.config.ts`.
- **Team photos:** the About page shows generated initials. To use photos, replace the `Avatar` component with an image that has a short, meaningful `alt` text.

## When you are done

- Search the project for the sample names ("Diamond Empire", "example.com") and replace what you find.
- Run `npm run check`.
- Run `npm run build` and look at the result with `npm run serve`.

Next: [Pages, services and blog posts](03-content.md).
