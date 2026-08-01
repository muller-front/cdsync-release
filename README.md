# CDSync

**Your Google Drive. Locally. Always.**

CDSync is the always-on Google Drive sync client for Linux you've been waiting for. It keeps a real, physical copy of your Google Drive files on your computer — so you can browse, search, edit, and use them with any program, even when you're offline. When you come back online, every change syncs back to the cloud in seconds.

No browser tab. No upload button. No "check if there's a new version of this file". Just your files, where they belong.

---

## ✨ What you get

- 📁 **Real local folder.** `~/GoogleDrive/` (or wherever you choose). Your files. Open them with anything.
- ⚡ **Real-time sync.** Edit a file locally, save, and it's in Google Drive within a second. Edit on another device, and it lands on your computer within a second.
- 🔄 **Two-way sync.** Works in both directions, automatically. No configuration.
- 🖥️ **Tray icon.** A small icon in your system tray shows sync status at a glance — green when idle, working when syncing, red if something needs attention.
- 🔌 **Offline-first.** Once activated, lose your internet connection and keep working. CDSync queues every change and replays them when you're back online. Up to 30 days without a connection.
- 🔒 **One license, one Google account, one machine.** No subscriptions. No recurring fees. Yours, forever.

---

## 🚀 Get started in 4 steps

Once you have your CDSync package (the `cdsync` and `cdsync-tray` binaries plus your personal `license.lic`):

### 1. Put everything in one folder

```bash
mkdir -p ~/cdsync-bundle
mv cdsync cdsync-tray license.lic ~/cdsync-bundle/
cd ~/cdsync-bundle
chmod +x cdsync cdsync-tray
```

### 2. Activate your license

```bash
./cdsync activate
```

A browser window will open for Google sign-in. Log in with the **exact Google account** that's in your license. Once you confirm, the license is bound to this machine — done.

> **Note:** activation needs internet — CDSync verifies your license against its license server and signs you in to Google, both one-time steps. After activation, CDSync keeps working fully offline for up to 30 days between checks.

### 3. Install (one-time setup)

```bash
./cdsync install
```

The installer walks you through a quick wizard: pick your Google Drive remote, pick the local folder to sync into, set how often you want CDSync to double-check everything. It then installs the binaries into `~/.cdsync/`, registers the system services, and sets up the tray icon. Takes about a minute.

### 4. Start syncing

```bash
./cdsync start
```

This launches the background daemon (handles real-time sync of every local change) and opens the tray icon in your system tray. You're done. Files in your local folder and in Google Drive will now stay in sync automatically.

**🎉 Welcome to your Google Drive, on your desktop.**

---

## 🛠️ Daily use

After the initial setup, you mostly don't have to think about CDSync. But when you need it:

| Command | What it does |
|---------|--------------|
| `cdsync status` | Quick check: are the daemon and tray running? |
| `cdsync stop` | Pause syncing (daemon + tray stop) |
| `cdsync start` | Resume syncing (daemon + tray start) |
| `cdsync restart` | Bounce everything — useful after config changes |
| `cdsync uninstall` | Remove CDSync from this machine |

### The tray icon menu

Right-click the tray icon for:

- **Sync Now** — manual immediate sync (the daemon usually does this on every save, but it's here if you want it)
- **Activity** — recent sync events (what changed, when)
- **Config → Force Resync** — repair the sync database if something looks stuck
- **Config → Notifications** — choose: All events / Errors only / Silent
- **Config → Set Interval** — how often the background bisync runs (default: every 5 minutes; lower for paranoid users, higher for laptops)
- **Reactivate...** — re-bind your Google account after hardware changes

---

## 🆘 Need help?

### Common situations

**"Nothing's syncing."**
Click the tray icon → "Sync Now". If that doesn't help, try `cdsync restart` in a terminal.

**"The tray icon is red."**
Click the tray icon → look for the message at the top. Most often: license needs re-binding (click **Reactivate**).

**"I changed my Google password."**
Run `cdsync activate` once. CDSync will re-authenticate and re-bind the new token.

**"I got a new computer."**
Your license is tied to one machine. On the new machine: copy `cdsync`, `cdsync-tray` and `license.lic` over, run `./cdsync activate`, then `./cdsync install`. (Your old machine's activation is invalidated automatically.)

### Where to get support

- **Email:** support@cdsync.example *(update with your real address)*
- **Bug reports:** include `cdsync --version` and a snippet of `~/.cdsync/log/cdsync.log`
- **Updates:** check back at the same place you bought your license

---

## 📋 System requirements

- **Linux** on x86_64 (Ubuntu, Debian, Mint, Fedora, Arch, Pop!_OS — anything modern)
- **systemd** (standard on all the distros above)
- **GTK3** + **AppIndicator** typelibs (one apt/dnf command — the installer will tell you)
- **rclone** ≥ 1.66 (the installer will tell you if yours is older)
- A **Google account** you want to sync

You do **not** need Python, pip, or anything else — the binary ships with everything it needs.

---

## 📜 License

Your `license.lic` is yours. It binds one Google Drive account, on one machine, for as long as you own this copy of CDSync. No telemetry, no ads. CDSync only contacts our license server at activation and during its periodic checks to confirm your license hasn't been revoked — it never uploads your files, your email, or any personal data. The license file is yours to keep; backing up `~/.cdsync/license/` lets you move CDSync to a new machine quickly.

See the `LICENSE` file in this package for the full proprietary terms.

---

*Built with care for Linux users who refuse to settle for browser tabs.*

CDSync — *Your cloud, local, always.*
