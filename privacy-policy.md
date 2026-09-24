---
title: Privacy policy
---
{% comment %}
The formal policy Google's verification and Paddle's review ask for. It
describes how the software actually behaves; have it reviewed for your
jurisdiction. The seller and contact come from _config.yml.
{% endcomment %}
# OpenWorthy privacy policy

*Last updated: 24 September 2026*

OpenWorthy is software that runs on your own computer and marks the email
worth opening. This policy explains what it does with your information.

## The short version

- OpenWorthy runs **only on your device**. **Nothing about you or your mail
  is ever sent to us** or to anyone else.
- It reads **message headers only** — who a message is from and to, its
  thread and list headers — and **never the content** of your email.
- It changes your mailbox in only two ways: adding or removing its own
  marker (a label, category or flag called "Worth Reading"), and keeping one
  small coordination record per computer you run it on, so that only one of
  your computers marks mail at a time. The record holds nothing but a random
  computer ID and a time: a hidden label in Gmail, a hidden folder in
  Outlook, or on other providers a short message in a folder named
  "OpenWorthy".
- If you switch on **server-side rules**, it also creates rules in your
  mailbox — a Sieve script, Gmail filters or Outlook message rules — that
  add the same marker to mail from senders your own history shows are worth
  reading, so that mail is marked while your computer is off. Those rules
  only ever add the marker, and OpenWorthy never changes or deletes a rule
  or filter you made yourself. `openworthy rules revoke` removes them. For
  Gmail this asks for one extra permission, to manage filters; without the
  feature it is never requested.

## What OpenWorthy accesses

To decide which messages are worth opening, OpenWorthy reads these header
fields of messages in your inbox and sent folder: sender, recipients,
reply-to, date, message and thread identifiers, subject, content type,
mailing-list headers, automated-message headers and authentication results.
It does not read message bodies or attachments.

## Where your data goes

Nowhere beyond your device. OpenWorthy connects directly from your computer
to your email provider (for example Google or Microsoft). No email data, and
nothing about you, passes through or is stored on any server of ours.

On your device, OpenWorthy keeps a small database of its decisions and of how
often you correspond with each sender. Email addresses and message
identifiers in it are stored as keyed cryptographic hashes, not in readable
form. Message subjects are not stored. Sign-in tokens and app passwords are
kept in your operating system's keychain.

OpenWorthy sends no analytics, telemetry or crash reports. If you choose to
report a bug, you decide what to attach.

Every connection OpenWorthy makes, and how to watch them yourself, is listed
in [Check it yourself](verify.md).

## Updates

The OpenWorthy app checks for a new version by downloading a public file
from our website, openworthy.github.io, when it starts and once a day. The
request carries nothing about you or your mail. As with any web request, the
website's host, GitHub, receives your IP address and the details of the
request, such as its time, under [GitHub's privacy
statement](https://docs.github.com/site-policy/privacy-policies/github-general-privacy-statement).
You can switch the check off in the app's Settings. The engine and the
command-line program never check for updates.

## Buying Pro

Pro is sold by our reseller, Paddle.com, the Merchant of Record for every
order. Checkout takes place in your web browser on Paddle's pages, and Paddle
processes your payment details under [its own privacy
notice](https://www.paddle.com/legal/privacy); we never see them. Paddle
shares with us your email address, country, and name if you give it, and
what you bought, which we use only to issue your licence, send it to you and
support you. We keep them for as long as your licence is valid and as
required for our tax and accounting records.

Your licence is a short signed text that contains your email address. It is
stored on your computer and checked there; OpenWorthy never sends it, or
anything else, to us.

## Our website

This website is hosted by GitHub Pages. We use no cookies, analytics or
trackers on it. GitHub receives visitors' IP addresses to serve the pages,
under the GitHub privacy statement linked above.

## Google user data

OpenWorthy's use and transfer of information received from Google APIs
adheres to the [Google API Services User Data
Policy](https://developers.google.com/terms/api-services-user-data-policy),
including the Limited Use requirements. Gmail data is used only to provide
OpenWorthy's labelling feature to you, is never transferred to others, is
never used for advertising, and is never read by humans.

## Your control

- **Stop at any time:** `openworthy account remove <account> --yes` deletes
  the account's local data and credentials and, for Google, revokes
  OpenWorthy's access.
- **Revoke access yourself:** Google — myaccount.google.com/permissions;
  Microsoft — account.live.com/consent/Manage or your organisation's My Apps.
- **Undo marks:** `openworthy undo` removes only the marks OpenWorthy added.

## Contact

{{ site.seller }} · [{{ site.contact }}](mailto:{{ site.contact }})
