---
title: How OpenWorthy works
---

# How it works

## What it looks at

OpenWorthy asks of each new email the questions you would ask at a glance,
using only who sent it, to whom, and which conversation it belongs to — and
your own history with the sender, which it learns from your Sent folder, on
your computer, when you connect:

- **Is it a conversation you're in?** A reply to something you wrote counts
  for a lot.
- **Do you write to this person?** People you email count for more, and
  people you usually reply to count for more still.
- **Is it an invitation?** Meeting invitations, changes and cancellations.
- **Is it written to you?** Mail to you alone counts for more; being copied
  counts for less.
- **Is it sent in bulk?** Newsletters, mailing lists and no-reply addresses
  count for less. Automatic messages, like out-of-office replies, are never
  marked.

An email that clears the bar gets the mark. The app shows why for every one,
in words: "You're in this conversation · You've emailed them 14 times".

## What it never does

- It never opens the text of an email or an attachment.
- It never moves, archives or deletes mail, never sends anything, and never
  marks anything as read.
- It never sends anything about you or your mail anywhere — not to us, not to
  anyone. [Check it yourself](verify.md).
- There is no AI model, here or anywhere else. Just the questions above.

## You stay in charge

- **Preview first.** A new mailbox starts with a preview of what OpenWorthy
  would mark. Nothing is marked until you press Start, and anything you
  untick teaches it what you don't need.
- **Take a mark off** in any mail app, or press *Not worth it* in
  OpenWorthy: that sender counts for less, and that email is never marked
  again.
- **Mark something yourself**, or quickly answer an email it didn't mark:
  that sender counts for more. Leaving marked mail unopened for days counts
  a little against the sender.
- **Undo** any group of marks from the Activity screen.
- **Mark more or fewer** with Sensitivity, which shows what the change would
  have done last week before you apply it.
- **It asks before it changes.** When your corrections point to a better
  setting, it suggests it and waits for your yes. Every change can be
  reverted in Settings.

## When your computer is off

OpenWorthy marks mail while one of your computers is on, so mail that
arrives overnight is marked when your computer wakes.

With [Pro](pricing.md) you can have your mail server itself mark mail from
the senders OpenWorthy is surest about, as it arrives — only people whose
every message was worth reading. Those rules only ever add the mark and
never touch filters of your own. Switch them on in Settings, under *Mark
mail while this computer is off*, and off again at any time.

## What it changes in your mailbox

Only three things: its own mark; a small note per computer, so that if you
use OpenWorthy on more than one computer only one of them marks at a time;
and, if you switch them on, the server rules above. Nothing else.

Technical details, for those who want them:
[command line, servers and NAS](command-line.md).
