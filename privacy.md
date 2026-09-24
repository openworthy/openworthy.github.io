---
title: Privacy
---

# Privacy, in plain words

**Nothing about you or your mail ever leaves your computer.**

- **We never see your email.** OpenWorthy runs on your computer and talks
  directly to your email provider. Your mail goes nowhere else — not to us,
  not to anyone.
- **It reads headers, not messages.** Sender, recipients, date, subject,
  conversation and mailing-list headers. Never the text of an email, never an
  attachment.
- **What it keeps, on your computer only:** its decisions and counts of how
  often you correspond with each sender. Addresses and message IDs are stored
  as keyed one-way hashes, so the database is meaningless if copied. Subjects
  are not stored. Passwords and sign-in tokens live in your OS keychain.
- **What it changes in your mailbox:** its own "Worth Reading" marker, and a
  small record per computer (a random ID and a time) so your computers take
  turns. With Pro's server-side rules switched on, also rules on your mail
  server that add the same marker — never touching rules of your own.
- **Updates:** the app checks for a new version by downloading a public file
  from this website. It sends nothing about you or your mail; like any web
  request, the website's host (GitHub) sees your IP address. You can switch
  it off in Settings.
- **Buying Pro** happens in your web browser, through our reseller Paddle.
  We receive your email address, country and, if you give it, your name, to
  send your licence and support you. Your licence is checked on your
  computer; OpenWorthy never contacts us about it.
- **No telemetry, no crash reports, no analytics.** If you report a bug, you
  choose what to attach; `openworthy doctor --bundle` replaces every address,
  subject and server name with a meaningless token first.
- **No AI model** reads your mail — locally or anywhere else.
- **Leaving is complete:** `openworthy account remove` deletes the local data
  and credentials and, for Google, revokes access.

**Don't take our word for it:** every connection OpenWorthy makes can be
watched with free tools — [here's how](https://openworthy.github.io/verify/).

The formal policy, including Google API user-data terms, is the
[privacy policy](https://openworthy.github.io/privacy-policy/).
