---
title: Check it yourself
---

# Check it yourself

**In short:** day to day, OpenWorthy connects to your email provider and
nothing else; the table below lists the few other moments, such as checking
for a new version. A free firewall app can show you every connection it
makes, and this page walks you through it, step by step.
If your firm has someone who looks after its computers, this is the page to
hand them.

OpenWorthy's code is not public, so you should not have to take our word for
what it does. You don't need the code to check its central promise —
**nothing about you or your mail ever leaves your computer** — because that
promise is about where data goes, and every connection a program makes can be
watched from outside it, with free tools, in a few minutes.

## What you should see

OpenWorthy is two programs: the **engine** (`openworthy`), which reads
headers and marks mail, and the **app** (`OpenWorthy`), the window you use.
With the app closed the engine keeps running on its own.

| When | Program | Connects to |
|---|---|---|
| Always, while it runs | engine | **Your mail provider, and nothing else.** IMAP: your provider's IMAP server (port 993), and its ManageSieve server (port 4190) if you use server-side rules. Gmail: `gmail.googleapis.com` and `oauth2.googleapis.com`. Microsoft: `graph.microsoft.com` and `login.microsoftonline.com` |
| Adding a mailbox | engine | Your computer's own DNS resolver, to look up your email domain's mail servers. Signing in to Google or Microsoft opens your web browser at their sign-in page |
| Removing a Google account | engine | `oauth2.googleapis.com`, to revoke OpenWorthy's access |
| Checking for updates (on by default; switch it off in Settings) | app | `openworthy.github.io`, to download a public file listing the newest version. Installing an update downloads it from `github.com` and GitHub's download servers |
| Only when you choose | your browser | The pricing page and checkout open in your web browser — OpenWorthy itself is not involved |

What you should **never** see: any other destination. There is no analytics
or crash-reporting service, and checking a Pro licence makes no connection at
all — it is verified on your computer. If you ever see OpenWorthy connect
anywhere not listed here, please [tell us](https://github.com/openworthy/openworthy.github.io/issues).

Two things you may see that are not OpenWorthy: your operating system checking
the app's signature when it is first opened (macOS asks Apple), and your
browser, when you open a link.

## On a Mac: LuLu

[LuLu](https://objective-see.org/products/lulu.html) is a free, open-source
firewall from Objective-See that asks you about every new outgoing connection.

1. Install LuLu and allow its network extension when macOS asks.
2. Open OpenWorthy. For each new connection LuLu shows which program is
   connecting (the app, or the engine inside it at
   `OpenWorthy.app/Contents/Helpers/openworthy`) and the destination's name
   or address. Allow the ones in the table above.
3. LuLu's *Rules* window then lists every destination OpenWorthy has ever
   asked for. Check it again after a day or a week of normal use.

Without installing anything, Terminal shows the connections open right now:

```
lsof -i -P -a -c '/openworthy/i'
```

Addresses are shown by their reverse names; Google's end in `1e100.net`.

## On Linux: OpenSnitch or `ss`

[OpenSnitch](https://github.com/evilsocket/opensnitch) is a free,
open-source application firewall. Once installed, it asks about each new
connection, naming the program and the destination host; allow the ones in
the table above, and its rules list shows everything OpenWorthy has asked
for.

Without installing anything, this shows the connections open right now:

```
sudo ss -tnp | grep -i openworthy
```

## On Windows: Resource Monitor or TCPView

**Resource Monitor** is built in: press Start, type `resmon`, open the
*Network* tab, and tick `openworthy.exe` and `OpenWorthy.exe` under
*Processes with Network Activity*. *TCP Connections* then lists every address
they are connected to.

[TCPView](https://learn.microsoft.com/sysinternals/downloads/tcpview), a free
tool from Microsoft, shows the same live, with host names.

## In Docker

The image holds nothing but the engine — no shell — so watch it from the
host. On a Linux host, this lists the container's open connections:

{% raw %}
```
sudo nsenter -t "$(docker inspect -f '{{.State.Pid}}' openworthy)" -n ss -tn
```
{% endraw %}

## Other things you can check

- **What it changed in your mailbox:** its own "Worth Reading" marker, and
  one small record per computer you run it on (a random ID and a time). Look
  in your mail app.
- **What it keeps:** `openworthy doctor` shows where its data folder is.
  Addresses in its database are one-way hashes; subjects are not stored.
- **Bug reports hold nothing you don't choose to send:** `openworthy doctor
  --bundle` writes a file on your computer, with every address, subject and
  server name replaced by a meaningless token. Read it before attaching it.
- **Reviews by others:** the macOS app is notarized by Apple, the Windows
  installer is signed, and Google reviews how OpenWorthy uses Gmail before
  its built-in Gmail sign-in is offered.

See also: [privacy, in plain words](privacy.md).
