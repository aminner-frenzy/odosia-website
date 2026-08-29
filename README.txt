ODOSIA — website files
======================

WHAT'S HERE
  index.html    the coming-soon landing page
  privacy.html  privacy policy  (this is the URL you give App Store Connect)
  terms.html    terms of service
  social.jpg    the preview image used when the link is shared
  README.txt    this file

Images and styles are already inside the HTML, so nothing can break by
being in the wrong folder. Just keep the four files together.

PUTTING IT LIVE ON CLOUDFLARE PAGES
  This site is hosted directly on Cloudflare Pages, connected to this
  repo's GitHub source — no VM, no nginx, no cert management. (An earlier
  attempt served it from nginx on odosia-vm, the same GCE VM as the odosia
  API, but Cloudflare could never validate the origin's cert for these
  domains, so it moved here.)

  One-time setup (only needed once, may already be done):
  1. In the Cloudflare dashboard: Workers & Pages -> Create -> Pages ->
     Connect to Git -> select this repo (odosia-website).
  2. Build settings: no build command, output directory "/" (this is a
     plain static site — nothing to compile).
  3. In the Pages project's Custom domains tab, add odosia.app and
     www.odosia.app. Cloudflare wires up DNS and issues/renews SSL
     automatically. Remove any leftover A records for these two hostnames
     that point at odosia-vm's IP, if present, so they don't conflict.

  To update after that: just push to main. Cloudflare Pages builds and
  deploys automatically — no GitHub Actions workflow involved.

BEFORE YOU SUBMIT TO THE APP STORE
  - Fill in every [BRACKET] in privacy.html and terms.html. Most of them
    are claims about your infrastructure or your contracts that would be
    untrue until they're true.
  - Have a lawyer read both. They're thorough drafts, not legal advice.
  - Put https://odosia.app/privacy.html in App Store Connect, and link it
    from inside the app too — Apple requires both.

THE EMAIL SIGN-UP
  Open index.html and find ENDPOINT near the bottom. Leave it empty and
  the button opens the visitor's email app to hello@odosia.app, so it
  works on day one. Paste a form URL from Formspree / Buttondown / Kit /
  Mailchimp between the quotes and it posts there instead.
