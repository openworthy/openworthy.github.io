---
title: How OpenWorthy decides
---

# How it decides

For each new message OpenWorthy adds up points from facts about it, read from
its headers and from your own history with the sender:

| Fact | Points |
|---|---:|
| It's a reply in a conversation you took part in | +45 |
| You have emailed this sender before | +40 |
| It's a calendar invitation, change or cancellation | +30 |
| You are the only recipient | +20 |
| You usually reply to this sender | up to +25 |
| It came through a mailing list | −25 |
| It's from a no-reply address | −25 |
| You are only copied (Cc) | −30 |
| It was sent automatically (auto-reply, notification) | never marked |

A message scoring **60 or more** is marked. The full list, and every weight,
is in `openworthy config print --defaults`; any of it can be changed.

`openworthy explain --last 10` shows the facts behind each decision:

```
Worth Reading · marked · score 108 (threshold 60)
    +45  you're in this conversation
    +40  you've emailed this sender
    +15  sender is from your organisation
     +8  addressed to you directly
```

## It learns — with arithmetic, not AI

There is no model and no training. OpenWorthy keeps counts per sender, which
fade over three weeks, and adjusts from what you do:

- **You remove its mark by hand** (or say `openworthy reject`): that sender
  counts for less, and that email is never marked again.
- **You mark something yourself**, or quickly answer an email it didn't mark:
  that sender counts for more.
- **You leave marked mail unopened** for days: a little less.

It never changes its own settings. When your corrections point to a change —
"you undid a whole batch; want fewer marks?" — it asks
(`openworthy suggestions`), shows what the change would have done last week,
and every change can be reverted (`openworthy settings`).

## When your computer is off

OpenWorthy marks mail while it runs, so mail that arrives overnight is
marked when your computer wakes. If you would rather it were marked as it
arrives, you can hand the senders it is surest about to the mail server
itself:

```
openworthy rules            # who would be handed over, and why
openworthy rules push       # put those rules on the server
openworthy rules revoke     # take them off again
```

A sender qualifies only after several messages, all worth reading, all
scoring well clear of the threshold, and none you ever unmarked — so the
rules stay a small, safe subset of what OpenWorthy does itself. The rule
only adds the marker: it never moves, archives, reads or deletes anything,
and your own filters are left alone. The engine keeps deciding everything
else as usual.

This uses whatever the mailbox offers: a **Sieve** script (Fastmail,
Dovecot, Stalwart and most self-hosted servers), **Gmail filters**, or
**Outlook message rules**. It is off until you switch it on with
`rulegen.enabled` in the configuration.

## What it changes in your mailbox

Its own marker, one small record per computer (a hidden label or folder, or
a message in an "OpenWorthy" folder on IMAP) so that only one of your
computers marks at a time, and — only if you switch on server-side rules —
rules that add that same marker. It never moves, archives or deletes
mail, never sends anything, and never marks anything as read.
