# Tidy — User Guide

> Tidy learns how you organize your files and helps put them where they belong.

---

## What is Tidy?

Tidy is a small desktop daemon that lives in your system tray. It watches your
**Downloads** folder, and every time you manually move a file out of it, it
remembers where you put it. After a few moves, it builds a personal model of
*your* way of organizing things — and starts suggesting destinations for new
files automatically.

Tidy never reads file contents. It looks only at filenames, extensions, sizes,
and basic type detection. Everything runs on your machine.

## Installation

### Windows

1. Download `Tidy-windows-x64.exe` from the
   [latest release](https://github.com/fdevelopment-department-ai/tidy-releases/releases/latest).
2. Double-click to run. Windows SmartScreen may warn you about an unsigned
   application — click **More info → Run anyway**.
3. A small **T** icon appears in your notification area, near the clock.

To start Tidy automatically with Windows, drop a shortcut in:

```
%APPDATA%\Microsoft\Windows\Start Menu\Programs\Startup
```

### macOS

1. Download `Tidy-macos.zip` from the latest release.
2. Unzip and move `Tidy.app` to `/Applications`.
3. On first launch, macOS will block it ("unidentified developer").
   Right-click → **Open** → **Open anyway**.
4. The **T** appears in the menubar (top-right of your screen).

To start at login: **System Settings → General → Login Items → +** and add
`Tidy.app`.

### Linux

1. Download `Tidy-linux-x64`.
2. Make it executable and move it somewhere on your `$PATH`:
   ```bash
   chmod +x Tidy-linux-x64
   mv Tidy-linux-x64 ~/.local/bin/tidy
   ```
3. Make sure your desktop environment supports system tray icons. On GNOME you
   may need the **AppIndicator and KStatusNotifierItem Support** extension.
4. Run `tidy` from a terminal or your application launcher.

## First-run experience

The first time you launch Tidy:

- It starts watching `~/Downloads`.
- It does **nothing visible** — no suggestions yet.
- It silently records every file you move out of Downloads.

After ~6 manual moves spread across at least **2 different destination
folders**, Tidy will train its first model in the background. From that
point on, when a new file appears in Downloads, Tidy will check whether it
recognizes a familiar pattern, and if it's confident enough (> 65 %), it will
show a desktop notification suggesting where to move it.

> **You stay in control.** Tidy in v0.1 only **suggests**. It never moves
> files for you.

## The tray menu

Right-click (or click) the tray icon to open the menu:

- **N examples learned · active/paused** — current state.
- **Pause watching / Resume watching** — toggle the watcher.
- **Recent suggestions** — the last 5 suggestions Tidy has shown you, with
  the confidence score.
- **Open data folder** — where the model and database live (see below).
- **About Tidy** — opens the website.
- **Quit** — stop the daemon.

## Where is my data?

Tidy stores everything locally:

- **Windows:** `%APPDATA%\Fdevelopment\Tidy\`
- **macOS:** `~/Library/Application Support/Tidy/`
- **Linux:** `~/.local/share/Tidy/`

Contents:

- `tidy.db` — SQLite database with training samples and recent suggestions.
- `model.joblib` — the trained scikit-learn model.
- `tidy.log` — daily log file.

To reset Tidy completely, quit it and delete this folder.

## Privacy

Tidy runs **entirely offline**. There is no telemetry, no analytics, no cloud
backend. The only network calls Tidy can make are when you explicitly click
"About" (which opens this website in your browser).

## Troubleshooting

**No tray icon on Linux.** Your desktop environment doesn't expose a system
tray by default. Install the AppIndicator extension for GNOME, or use a
desktop environment that supports it (KDE, Cinnamon, MATE, XFCE).

**"Application not signed" on macOS.** Right-click → Open the first time;
macOS will remember your choice.

**The suggestions are wrong.** Tidy needs examples to learn. The more
consistently you sort, the better it gets. If you change your mind about a
destination, simply move files to the new place a few times — the model
will catch up after the next retrain.

**I want a clean slate.** Quit Tidy, delete your data folder, restart.

## License & contact

Tidy is freeware — free to use, redistribution restricted. See `LICENSE.txt`
shipped with the binary. For commercial inquiries: `contact@fdevelopment.fr`.
