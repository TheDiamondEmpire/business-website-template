# 4. Connect the contact form

Business Website Template by The Diamond Empire, https://thedempire.shop/

The contact form checks what a visitor types and then hands the message to a **submit adapter**. The adapter that comes with the template is a stand-in: it makes **no network request**, stores nothing and shows a confirmation that is clearly marked **Demo** and says the message was not sent. That is on purpose, so the form can never look as if it works when it does not.

Before you publish, connect a real service.

## How it works

1. The visitor fills in the form. The browser checks every field and, if something is wrong, shows an error summary and a message next to each field.
2. When everything is valid, the form calls `submitContact(payload)` from `src/lib/contact/adapter.ts`.
3. The adapter returns `{ ok: true }` when the message was accepted, or `{ ok: false }` when it was not. The form shows a thank-you message or an error message with a retry.

The payload holds: `name`, `email`, `topic`, `message` and `consent` (always `true`, because the form requires the tick box).

## Connect a service in one file

Open `src/lib/contact/adapter.ts`. The only line that matters is:

```text
export const submitContact: SubmitAdapter = demoAdapter;
```

### Option A: a form service or your own endpoint that accepts JSON

The template includes an optional ready-made adapter that posts the message as JSON. Replace the line with:

```text
import { createJsonPostAdapter } from './http-adapter';
export const submitContact: SubmitAdapter = createJsonPostAdapter('https://your-form-address.example/endpoint');
```

(Keep the import line at the top of the file with the others.) The address must start with `https://`. Check what your provider expects: some want form-encoded data or different field names. If so, use option B.

### Option B: write your own adapter

An adapter is one function that takes the payload and returns a promise:

```text
export const submitContact: SubmitAdapter = async (payload) => {
  // send payload to your service here
  return { ok: true };
};
```

Return `{ ok: false }` when the service answers with an error, and `{ ok: true, message: 'Custom thank-you text' }` if you want your own confirmation wording.

## Things to decide before you go live

- **Where the messages go and who can read them.** Name your provider in your privacy notice. The data leaves the visitor's browser only after you connect an adapter.
- **Spam.** Browser checks do not stop automated spam. Use the protection your provider offers (a hidden field, rate limiting or a challenge) and validate again on the receiving side. Never trust the browser-side checks alone.
- **Confirmation email.** If you send an automatic reply, send it from the receiving side, not from the page.
- **No secrets in the page.** Everything in the finished site is public. An endpoint used from the browser is public by nature, so choose one that limits abuse.
- **The consent wording.** The tick box says the visitor agrees that you may use their details to reply. Adjust the wording in `src/components/ContactForm.tsx` to match your privacy notice.

## Test it

1. Run `npm run dev` and send a message through the form. Check that it arrives and that the thank-you message shows without the **Demo** mark.
2. Send an empty form and one with a bad email address. You should see the error summary and the messages next to the fields.
3. Switch off your internet connection and send again. The form should show "Your message was not sent" and keep what you typed.
4. Run `npm test`. The form tests use a stand-in adapter, so they keep passing when you connect yours.

If you do not connect a form, replace the contact page with your email address and phone number, or the visitor will think they have contacted you when they have not.

Next: [SEO](05-seo.md).
