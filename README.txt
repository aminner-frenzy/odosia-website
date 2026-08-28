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

PUTTING IT LIVE ON CLOUDFLARE (about 10 minutes, free)
  1. Cloudflare dashboard -> Workers & Pages -> Create application
     -> Get started -> Drag and drop your files.
  2. Name the project "odosia", drag this whole folder in, Deploy site.
     You'll get a odosia.pages.dev link — check it looks right there first.
  3. In the project -> Custom domains -> Set up a domain -> odosia.app
     (repeat for www.odosia.app if you want it). Cloudflare makes the DNS
     record itself because the domain is already on your account.
  4. .app is an HTTPS-only domain, so the site won't load until the
     certificate is issued — usually a few minutes. That's normal.

  To update later: same project -> Create deployment -> drag the new folder.

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
