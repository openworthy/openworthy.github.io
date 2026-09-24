---
title: Install OpenWorthy
---

# Install

**Most people:** download the app for your system from the
[releases page](https://github.com/openworthy/openworthy.github.io/releases) —
`OpenWorthy_…_macos_arm64.dmg` (Apple silicon), `…_macos_amd64.dmg` (Intel
Mac), `…_windows_amd64_setup.exe`, or the Linux `.deb`/`.rpm`. Open it and it
walks you through connecting your email. Closing its window leaves OpenWorthy
marking mail in the background; *Help → Stop OpenWorthy* stops it.

**Command line, servers and NAS:** OpenWorthy is also a single program with no dependencies. Download it for your
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
| Docker (NAS, Raspberry Pi) | see below |

## Set up an account

```
openworthy account add you@example.com
```

Microsoft accounts open a browser to sign in. Gmail accounts do too when
your copy of OpenWorthy includes Google sign-in (`openworthy version` shows
it); otherwise they use an app password, or your own Google Cloud app
(`--client-id`, see the app registration guide). Other providers ask for an
**app password** — `account add` tells you where your provider issues one. Passwords and sign-in tokens are stored in your operating system's
keychain, never in a file.

A new account starts in **preview**: OpenWorthy works out what it would mark
and marks nothing until you have looked.

```
openworthy run --once      # learn from your Sent folder, decide recent mail
openworthy preview         # what it would mark, and why
openworthy start --account ID [--reject KEY]   # start; leave out any it got wrong
openworthy run             # keep running; marks new mail as it arrives
```

`openworthy run` keeps going until you stop it. While it runs, every other
command talks to it, and it writes a short daily list of the emails worth
reading.

## More than one computer

Run OpenWorthy on as many of your computers as you like. They agree among
themselves, through a small record kept in your mailbox, that **only one of
them marks mail at a time**; if that one sleeps or shuts down, another takes
over within about ten minutes. `openworthy status` shows which is active.

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
