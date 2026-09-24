---
title: A self-hosted alternative to SaneBox
---

# A self-hosted alternative to SaneBox

SaneBox is a well-known hosted service that connects to your mailbox from its
own servers and sorts your mail for you. If you want a similar result without
connecting your mailbox to anyone's servers, OpenWorthy is an alternative
that runs on hardware you own.

The approach differs in two deliberate ways:

- **Where it runs.** OpenWorthy runs on your computer (or your own NAS, in
  Docker). There is no account with us and no server of ours in the path.
- **Mark, don't move.** Hosted sorters typically move less important mail into
  a separate folder. OpenWorthy leaves everything in your inbox and adds a
  **Worth Reading** label, flag or category to what needs you — so nothing
  important is ever hidden in a folder you forget to check.

What you give up: OpenWorthy works while one of your computers (or your NAS)
is running — with [Pro](pricing.md), your mail server also marks mail from
your most trusted senders while they are all off — and it has no web
dashboard; you use it from its own app or the command line.

See the [factual comparison](compared-with-hosted-services.md) or
[install it](install.md).
