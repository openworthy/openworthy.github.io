---
title: Command line, servers and NAS
---

# Command line, servers and NAS

Everything the app does, OpenWorthy also does from the command line — for
servers, a NAS, scripts, or people who simply prefer a terminal. Most people
never need this page: [the app](install.md) does it all.

## Install

OpenWorthy is a single program with no dependencies. Download it for your
system from the [releases page](https://github.com/openworthy/openworthy.github.io/releases),
check it against `SHA256SUMS` (and its signature `SHA256SUMS.asc`), or use a
package manager:

| System | Command |
|---|---|
| macOS (Homebrew) | `brew install --cask openworthy/openworthy/openworthy` |
| Windows (winget) | `winget install OpenWorthy.OpenWorthy` |
| Windows (Scoop) | `scoop bucket add openworthy https://github.com/openworthy/scoop-openworthy` then `scoop install openworthy` |
| Debian / Ubuntu | download the `.deb`, then `sudo apt install ./openworthy_*.deb` |
| Fedora / RHEL | download the `.rpm`, then `sudo dnf install ./openworthy_*.rpm` |
| Docker (NAS, Raspberry Pi) | see [Docker](#docker) |

## Set up an account

```
openworthy account add you@example.com
```

Microsoft accounts open a browser to sign in. Gmail accounts do too when
your copy of OpenWorthy includes Google sign-in (`openworthy version` shows
it); otherwise they use an app password, or your own Google Cloud app
(`--client-id`). Other providers ask for an app password; `account add`
tells you where your provider issues one. Credentials are stored in your
operating system's keychain, never in a file.

A new account starts in preview, and marks nothing until you have looked:

```
openworthy run --once      # learn from your Sent folder, decide recent mail
openworthy preview         # what it would mark, and why
openworthy start --account ID [--reject KEY]   # start; leave out any it got wrong
openworthy run             # keep running; marks new mail as it arrives
```

`openworthy run` keeps going until you stop it (`openworthy stop`). While it
runs, every other command talks to it — including the app, if you use both.

## Everyday commands

| Command | What it does |
|---|---|
| `openworthy status` | Whether it is running, and each account's state |
| `openworthy explain --last 10` | Why recent emails were or weren't marked |
| `openworthy reject KEY` / `keep KEY` | "Not worth it" / "worth it" for one email; it learns from both |
| `openworthy activity` | Recent groups of marks and undos |
| `openworthy undo --since 2h` | Take off marks OpenWorthy added (also `--batch ID`) |
| `openworthy suggestions` | Settings changes your corrections point to; nothing changes without your yes |
| `openworthy calibrate` | What marking more or fewer would have done last week |
| `openworthy settings` | Every settings change, and `settings revert N` |
| `openworthy digest` | Today's list of emails worth reading |
| `openworthy contacts import FILE` | Count the people in a vCard file as known |
| `openworthy licence add FILE` | Add a Pro licence (`-` reads it from the terminal) |
| `openworthy help` | Every command |

The configuration is a commented text file: `openworthy config print` shows
it, and `openworthy config validate` checks your edits.

## Mail marked while your computer is off (Pro)

Set `enabled = true` under `[rulegen]` in the configuration (or switch it on
in the app's Settings), then:

```
openworthy rules            # who would be handed to the mail server, and why
openworthy rules push       # put those rules on the server
openworthy rules revoke     # take them off again
```

It uses what the mailbox offers: a Sieve script (Fastmail, Dovecot, Stalwart
and most self-hosted servers), Gmail filters, or Outlook message rules. The
rules only add the mark, and never touch rules of your own.

## More than one computer

Run OpenWorthy on as many computers as you like. They agree, through a small
record kept in your mailbox, that only one of them marks at a time; if that
one sleeps or shuts down, another takes over within about ten minutes.
`openworthy status` shows which is active.

## Docker

For an always-on machine you own:

```
docker run -d --name openworthy --restart unless-stopped \
  -v openworthy:/data \
  -e OPENWORTHY_KEYRING_PASSPHRASE='a long passphrase of your choice' \
  ghcr.io/openworthy/openworthy
```

A container has no OS keychain, so credentials are kept in an encrypted file
in the volume, unlocked by that passphrase (at least 12 characters). To keep
the passphrase out of the environment, put `passphrase_file = "/run/secrets/…"`
under `[keyring]` in `/data/config.toml` and mount the secret there.

Add an account with `docker exec -it openworthy openworthy account add …`.
IMAP accounts with an app password work anywhere; Gmail and Microsoft
sign-in opens a browser, so do it on a computer, or use an app password.

## Check it

```
openworthy doctor
```

If something is wrong, `openworthy doctor --bundle` writes a diagnostic file
with every address, subject and server name replaced by a meaningless token.
Nothing is sent: read it, and attach it to a bug report if you wish.

## Remove it

```
openworthy undo --since 30d            # optional: take its marks off
openworthy account remove ID --yes     # deletes local data; revokes Google access
```

Then delete the program and its data folder (`openworthy doctor` shows where).
