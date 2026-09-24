---
title: An email filter that doesn't read your email
---

# An email filter that doesn't read your email

Most "smart inbox" tools work by giving a company's servers access to your
mailbox, where software reads your mail to sort it. If you'd rather nobody's
software reads your email but your own, the design has to be different, not
just the privacy policy.

OpenWorthy is built that way:

1. **It runs on your own computer.** There is no service to trust because
   there is no service. The connection goes from your machine straight to
   Gmail, Outlook or your IMAP server.
2. **It only asks for headers.** For Gmail it requests `format=metadata`; for
   IMAP, `BODY.PEEK[HEADER.FIELDS (…)]`; for Microsoft, an explicit field
   list with no body. There is no code path that fetches a message body — and
   the test suite fails if one ever appears.
3. **It decides from facts you'd use yourself:** Is this a reply to me? Have I
   written to this person? Am I the only recipient? Is it a mailing list?
4. **It marks; it doesn't move.** Nothing disappears into a folder you forget
   to check. The Worth Reading label shows up in your normal mail app and on
   your phone.

[How it decides](how-it-works.md) · [Install](install.md)
