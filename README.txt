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

PUTTING IT LIVE ON GOOGLE CLOUD
  This site is served by nginx on odosia-vm — the same GCE VM that runs the
  odosia API (see the frenzy-api repo's deploy/ folder), in project
  frenzy-dev-450203. It's just a third and fourth hostname (odosia.app,
  www.odosia.app) on nginx alongside api.odosia.app — no separate hosting
  infra to run or pay for.

  One-time setup (only needed once, may already be done):
  1. In Cloudflare DNS, add A records for odosia.app and www.odosia.app
     pointing at odosia-vm's external IP (same IP api.odosia.app uses).
  2. On the VM, run frenzy-api's deploy/scripts/setup-ssl.sh — it now also
     requests a Let's Encrypt cert for odosia.app + www.odosia.app and
     nginx.conf already has server blocks ready to serve this repo's files
     from /opt/odosia/website.
  3. In this repo's GitHub -> Settings -> Secrets and variables -> Actions,
     add GCE_HOST, GCE_USER, GCE_SSH_KEY (same values used in frenzy-api's
     deploy-backend.yml — a repo's secrets aren't shared across repos, so
     they need to be added here too).

  To update after that: just push to main. .github/workflows/deploy.yml
  rsyncs the site files over SSH straight into /opt/odosia/website on the
  VM; nginx serves them with no restart needed.

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
