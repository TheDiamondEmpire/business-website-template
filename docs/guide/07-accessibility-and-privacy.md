# 7. Accessibility and privacy

Business Website Template by The Diamond Empire, https://thedempire.shop/

## Accessibility: what is built in

- **Landmarks:** a banner (header), a main area, a footer, and labelled navigation areas ("Main", "Footer", "Breadcrumb").
- **Skip link:** the first thing a keyboard user reaches on every page is "Skip to main content".
- **Keyboard use and focus:** every control can be reached and used with the keyboard, and shows a thick focus outline. After a page change inside the site, focus moves to the main area.
- **Headings:** one first-level heading per page and no skipped levels.
- **Forms:** every field has a visible label. Errors appear in a summary at the top that receives focus, and next to each field, linked to it for screen readers.
- **Colour and contrast:** colours come from the tokens in `src/styles/tokens.css`, in a light and a dark theme. The theme follows the visitor's device and can be switched with a button.
- **Reduced motion:** if the visitor has asked their device to reduce motion, transitions and smooth scrolling are switched off.
- **Text size:** type sizes use relative units, so they follow the visitor's browser settings.
- **No content that only works with a mouse:** the FAQ uses native `<details>` elements.

## What you still need to check

Automated tools find only part of the problems that affect people. This template was scanned with an automated tool and a keyboard script, and that does not show conformance with any accessibility standard. After you add your own content, check these by hand:

- Every image you add has a short `alt` text that says what it shows, or an empty `alt=""` when it is only decoration.
- Link text makes sense out of context. Avoid "click here".
- Headings describe the content below them.
- Videos have captions and audio has a transcript.
- Your new colours meet the contrast guidance in guide 2.
- Try the pages with the keyboard only, at 200 percent zoom, and with a screen reader if you can.
- Ask someone who uses assistive technology to try your finished site.

## Privacy: what the template does

- **No tracking.** The template includes no analytics, advertising, tag manager, tracking pixel or session recording, and loads no third-party script, font, stylesheet or image. The finished pages request files only from your own address.
- **No cookies.** The template sets none. The theme toggle remembers its choice in the browser's local storage on the visitor's device. It is never sent anywhere.
- **The contact form** sends nothing until you connect a service (guide 4).
- **RSS feed:** a plain file. It does not track readers.

## If you add analytics or other services

Every service you add can send visitor data to another company. Before you add one:

1. Decide whether you need it.
2. Prefer a privacy-friendly service that does not use cookies, and read its terms.
3. Update your privacy notice, and add a cookie or consent notice if the law where your visitors are requires one.
4. Add the service's script deliberately, in `src/app/layout.tsx`, using the provider's current instructions. The template does not include a place-holder so that nothing is added by accident.

## Next.js usage statistics

The development tool (Next.js) can collect anonymous statistics about the commands you run on your own computer. This is not part of your finished site. To switch it off, run `npx next telemetry disable`.

## Security notes

- The finished site is static files. There is no server code, database or login to attack.
- Everything in the folder is public once it is published. Never put secrets, passwords or private keys in the project.
- Keep your tools up to date: run `npm outdated` now and then, and `npm audit` before you publish.
- Serve the site only over HTTPS.
