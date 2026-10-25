# Atlas

Atlas is a live map that runs on your own computer or phone: weather radar, traffic, aircraft, trains, places,
directions and much more, in one window. This page explains how to install it, step by step.

**Download page:** [the newest version](https://github.com/rubyodingus/atlas-releases/releases/latest) (or [all versions](https://github.com/rubyodingus/atlas-releases/releases)).
On that page, open **Assets** and download the one file for your device:

| Your device | Download this file |
|---|---|
| Windows 10 or 11 | `Atlas-Setup-<version>.exe` |
| Ubuntu, Linux Mint, Debian, Pop!_OS | `atlas_<version>_amd64.deb` |
| Any other Linux (Fedora, Arch, openSUSE ...) | `Atlas-<version>-x86_64.AppImage` |
| Android phone or tablet | `Atlas-<version>.apk` |

You don't need any of the other files. (`atlas-<version>.zip` is what installed copies update themselves with;
`SHA256SUMS` is for checking a download, see the end of this page.)

The warnings below are **expected**: Atlas is a small project without a paid "code-signing certificate", so Windows,
Android and some Linux app stores don't know it yet. Every download is still checked: see *Checking a download*.

---

## Windows 10 / 11

1. Download `Atlas-Setup-<version>.exe`. If your browser says the file "isn't commonly downloaded", choose
   **Keep** (in Edge: the **...** menu next to the download → **Keep** → **Show more** → **Keep anyway**).
2. Double-click it. Windows shows a blue box: **"Windows protected your PC"**. Click **More info**, then
   **Run anyway**. This appears because the installer isn't signed with a certificate; it is expected.
   If instead it says **"Smart App Control blocked an app that may be unsafe"**, there is no Run anyway button:
   open **Windows Security** → **App & browser control** → **Smart App Control settings** → **Off**, then
   double-click the installer again. (Smart App Control is an extra check on some new Windows 11 PCs that blocks
   every program without a certificate; once turned off, Windows can't turn it back on without a reset, but
   Microsoft Defender and SmartScreen keep protecting the PC as before.)
3. Click **Next** through the installer and **Install**. You don't need an administrator password: Atlas installs for
   your Windows account only. On the way you can choose the East Tennessee starter data (ticked; untick it if you
   live elsewhere or are on a limited connection, see [Starter data](#first-start-all-devices)), a desktop shortcut,
   and whether Atlas starts when you sign in. The starter data download shows its progress and has a **Cancel**
   button; if it is cancelled or fails, Atlas is still installed and works.
4. Leave **Open Atlas** ticked and click **Finish**: Atlas opens in its own window. Later, start it from the Start
   menu (**Atlas**). Next: [First start](#first-start-all-devices).

Closing the window leaves Atlas running in the background, so the next window opens at once. To stop it: Start menu
→ **Stop Atlas**.

Running the same (or a newer) installer again repairs or upgrades Atlas and keeps your settings and data.

## Linux: Ubuntu, Mint, Debian (.deb)

1. Download `atlas_<version>_amd64.deb`.
2. Double-click it. Your software installer opens (App Center, Software Manager or similar). It may say the
   package is from an unknown or third-party source, or "potentially unsafe": that is expected, because Atlas is not
   in your distribution's own collection. Click **Install** and type your password. (If a different program opens,
   right-click the file → **Open With** → your software installer; or in a terminal:
   `sudo apt install ./atlas_<version>_amd64.deb`.)
3. Open **Atlas** from your app menu. Next: [First start](#first-start-all-devices).

A newer `.deb` installs over the old one and keeps your settings and data. If Atlas is running while you install
it, the next click on **Atlas** in the app menu restarts it with the new version.

## Linux: any distribution (AppImage)

1. Download `Atlas-<version>-x86_64.AppImage`. It is the whole program in one file; it brings its own Python, so
   nothing else is needed.
2. Allow it to run, once: right-click the file → **Properties**, then on Ubuntu switch on **Executable as Program**;
   on Linux Mint open **Permissions** and tick **Allow executing file as program** (other desktops use similar
   words; or in a terminal: `chmod +x Atlas-*.AppImage`). Linux asks this for every program you download; it is
   expected.
3. Double-click it. The first start adds **Atlas** to your app menu (pointing at this file: keep it where it is, or
   start it once more after moving it). Next: [First start](#first-start-all-devices).

If it doesn't start at all, your system may lack FUSE, which AppImages use: install your distribution's `fuse3`
package, or start it from a terminal with
`TMPDIR="$XDG_RUNTIME_DIR" ./Atlas-<version>-x86_64.AppImage --appimage-extract-and-run` (the `TMPDIR` part keeps
the unpacked copy in a folder only you can write to).

**On Linux, closing the window leaves Atlas running in the background**, so the next window opens at once.
To stop it: right-click **Atlas** in the app menu → **Stop Atlas**. It also stops when
you log out. If you already run Atlas another way on this computer, the menu entry simply opens that one.

## Android

1. On the phone, download `Atlas-<version>.apk` (open this page in the phone's browser). If Chrome says the file
   might be harmful, tap **Download anyway**.
2. Tap the download. Android asks to allow your browser (or Files app) to **install unknown apps**: tap
   **Settings**, switch **Allow from this source** on, and go back.
3. Tap **Install**. If Google Play Protect asks to scan the app, tap **Scan app** (it is installed after the scan)
   or **Install without scanning**; if it says it doesn't recognise the app, tap **More details** → **Install
   anyway**. This appears because Atlas isn't from the Play Store; it is expected.
4. Open **Atlas**. The first start takes a minute or two (it sets itself up). Next:
   [First start](#first-start-all-devices).

Android 7 or newer, on a 64-bit phone or tablet (almost every phone from the last several years). A newer `.apk`
installs over the old one and keeps your data. Atlas also updates itself inside the app (see *Updates*), so you
rarely need a new `.apk`.

---

## First start (all devices)

Atlas asks for one thing: a free **TomTom key** (it draws the traffic and live road speeds).

1. Go to [developer.tomtom.com](https://developer.tomtom.com/user/register) and register (free; no card needed).
2. After signing in, open your **Dashboard** → **API & SDK keys** (or **Keys**) and copy your key (TomTom usually makes one for you,
   called "My first API key"; if the list is empty, click **Add key**).
3. In Atlas's **Welcome** window, paste it into the TomTom key box. You may also type your home town (where the
   map opens; optional). Click **Save**. That's all: everything else works without an account.

**Starter data (optional).** Atlas can download starter data for a region (today: East Tennessee, about 400 MB: the
road map for directions, map tiles, places and more), so the map is quick from the start. Atlas checks the download
against its signed list before using it. Skip it if you live elsewhere or are on a limited connection: Atlas then
fetches only what you look at. Where it is offered: on Windows in the installer (to get it later, run the installer
again and tick it); on Linux at the first start (later: right-click **Atlas** in the app menu → **Get starter map
data**); on Android before the map opens (**Download…**, **Choose file…** for a copy you have, or **Start empty**;
later: **Settings → About**).

## Updates

Atlas looks for a new version each time it starts (and once a day while it runs). When there is one, a bar at the
top of the map says so: click **Update**. Atlas downloads it, checks it, installs it and starts again by itself, then
shows what's new. Each update is signed, and Atlas refuses one that isn't (or that was changed on the way). It never
touches your settings, keys, notes or saved places, and if a new version doesn't start, the one you had comes back.

**Settings → About** shows your version, has **Check for updates**, lets you turn the daily check off, and has **Go
back** to return to the version you had before, if an update doesn't suit you.

## Uninstalling

- **Windows:** Settings → Apps → Installed apps → the **...** next to **Atlas** → **Uninstall** (Windows 10: Apps &
  features → **Atlas** → **Uninstall**). It asks whether to delete your settings and data as well; the answer **No**
  (keep them) is the default, so a later install finds them again. The starter data is removed either way; the
  installer offers it again.
- **Linux (.deb):** remove **Atlas** in your software app (or `sudo apt remove atlas`). Your settings and data stay
  in your home folder (`~/.config/atlas`, `~/.local/share/atlas`); delete those folders to remove them too.
- **Linux (AppImage):** stop Atlas (app menu → right-click **Atlas** → **Stop Atlas**), then delete the AppImage
  file; its app menu entry disappears with it. Your settings and data stay in the same folders as above.
- **Linux, either way:** the program itself is kept in `~/.local/share/atlas/app` (that is where updates go); delete
  that folder too if you want it gone completely.
- **Android:** uninstalling an app always deletes its data on Android. To keep yours, first use **Settings →
  Profile → Export** and save the file.

## Privacy

Everything Atlas knows about you (your keys, settings, notes, saved places) stays on your device and is never sent
anywhere. To draw the map, Atlas asks public servers only for the area on screen, snapped to a grid.

## Checking a download

Each version's page lists `SHA256SUMS` (the fingerprint of every file) and `SHA256SUMS.sig` (its signature).

1. The file's fingerprint must match its line in `SHA256SUMS`:
   - Windows (PowerShell): `Get-FileHash .\Atlas-Setup-<version>.exe` (it prints the fingerprint in capitals:
     that's fine, compare the letters and digits)
   - Linux: `sha256sum --ignore-missing -c SHA256SUMS`
2. `SHA256SUMS` must be signed by the Atlas release key (fingerprint SHA256:ZE+OCmjm7UhqjS/vLyHU44b23McxXqi/1KtlNQwwIz8). Save this line as a file
   called `allowed_signers`:

   ```
   atlas-release ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIDDA8NBKvOTo7FSuN/YfEy6AX9YyTJKeNIMOujNIggJz
   ```

   (in Notepad choose **Save as type: All files**, so it isn't saved as `allowed_signers.txt`), then run, in the
   folder with the three files:
   - Linux, macOS: `ssh-keygen -Y verify -f allowed_signers -I atlas-release -n atlas-release -s SHA256SUMS.sig < SHA256SUMS`
   - Windows (PowerShell or Command Prompt):
     `cmd /c "ssh-keygen -Y verify -f allowed_signers -I atlas-release -n atlas-release -s SHA256SUMS.sig < SHA256SUMS"`

   It must say **Good "atlas-release" signature**.

## Help

If Atlas says another program uses its port, restart the computer; if it keeps happening, open an issue.

Open an issue on this repository (the **Issues** tab) and say which device and version you have and what happened.
Never paste your TomTom key or an exported profile into an issue: issues are public.
