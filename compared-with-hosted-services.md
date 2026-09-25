---
title: OpenWorthy compared with hosted triage services
---

# OpenWorthy compared with hosted triage services

A factual comparison with the general design of hosted email triage services
(services that sort your mail from their own servers). Individual services
differ; check each one's own documentation.

| | OpenWorthy | A hosted triage service |
|---|---|---|
| Where your mail is processed | On your computer | On the service's servers |
| Who can access your mailbox | Only software running on your machine | The service's servers, with the access you granted |
| What is read | Headers only | Varies by service |
| What it does to mail | Adds or removes its own marker | Commonly moves mail into folders |
| Works when your computer is off | With Pro, your mail server marks mail from your most trusted senders as it arrives; everything else when a computer of yours is on (or an always-on machine you own, in Docker) | Yes |
| Explains each decision | Yes, every mark says why | Varies |
| Price | Free for one mailbox; Pro US$39 a year for every mailbox ([pricing](pricing.md)) | Usually a subscription |
| Account with the vendor | None — a Pro licence is text you paste in | Required |

OpenWorthy trades "always on, nothing to install" for "nobody else ever
touches your mailbox." If the second matters more to you,
[install it](install.md).
