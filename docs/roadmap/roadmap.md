# Express Crash Future Ideas Roadmap

This document outlines potential features, refactorings, and improvements for the Express Crash-course project. Ideas listed here are not prioritized unless explicitly stated.

## Current Ideas:

- [ ] Proper Tailwind usage
  - [ ] cdn.tailwindcss.com should not be used in production. To use Tailwind CSS in production, install it as a PostCSS plugin or use the Tailwind CLI: https://tailwindcss.com/docs/installation
- [ ] **Cookie Consent Banner:** see notes on Cookies, below
- [ ] Privacy Policy
- [ ] Other courses? An overall banner? Some kind of branding?
  - [ ] This could hold "cheatsheets", simple guides, etc.



## notes on Cookies

Do You Need to Notify Users About Cookies?
Yes, almost certainly.

The legal landscape around cookies is complex, but the general consensus and legal requirement in many parts of the world (like the EU/UK under GDPR and the ePrivacy Directive) is that you must:

Inform users that your site uses cookies.
Explain what the cookies are for.
Get consent before storing any non-essential cookies on their device.
Your progress-tracking cookie, while functional, would be considered non-essential. Essential cookies are those strictly necessary for the site to function, such as a session cookie for a login or a cookie to remember items in a shopping cart.

What you should do:

You should implement a simple cookie consent banner that appears for new visitors. This banner should briefly explain that the site uses a cookie to save their course progress and ask for their permission. It's also best practice to include a link to a Privacy Policy page, even a simple one, that details this.

By implementing a consent mechanism, you respect user privacy and comply with major international data privacy laws.