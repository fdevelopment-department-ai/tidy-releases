# Tidy

> *"Tidy puts things where they belong."*

A small, quiet, well-behaved daemon. Lives in your tray. Watches your Downloads folder. Notices that you always move invoices to `Compta`, photos to `Camera Roll`, contracts to `Legal`. After a handful of examples, it starts whispering suggestions.

**Local. Free. Cross-platform.** Your files never leave your machine.

🌐 **[fdevelopment-department-ai.github.io/tidy-releases](https://fdevelopment-department-ai.github.io/tidy-releases/)**

---

## ⬇ Download

|  | Platform | Installer |
|---|---|---|
| 🪟 | Windows 10 / 11 | [**Tidy-Setup-windows-x64.exe**](../../releases/latest) |
| 🍎 | macOS 11+ | [**Tidy.dmg**](../../releases/latest) |
| 🐧 | Linux (x64) | [**Tidy-x86_64.AppImage**](../../releases/latest) |

Prefer the raw binary? `Tidy.exe`, `Tidy-macos.zip` and `Tidy-linux-x64` are also attached to each release.

[**See all releases ↗**](../../releases)

---

## 🌱 How it works

1. **Install Tidy.** A small **T** appears in your system tray. You forget about it.
2. **Sort files like you always do.** Move an invoice to `Compta`. A photo to `Camera Roll`.
3. **Tidy is watching.** Silently. It remembers each `(file → destination)` pair *locally*, on your disk.
4. **After 6 examples** spread over 2 destinations, a scikit-learn classifier trains itself in the background.
5. **When a new file lands**, Tidy quietly nudges you: *"Move this to Compta?"* — only if confidence ≥ 65 %.

No automation, no surprises. **Tidy only proposes.** You stay in charge.

---

## 📚 Read more

- 🇬🇧 [User guide (English)](docs/user-guide.en.md)
- 🇫🇷 [Guide utilisateur (Français)](docs/user-guide.fr.md)

---

## 🔒 Privacy, in one paragraph

Tidy looks at filenames, extensions, sizes, and a magic-byte sniff for type detection. **It does not read the contents of your files.** The trained model lives on your disk, in your user data folder. It is never sent anywhere. To erase everything Tidy has learned: quit it, delete the data folder. Done.

Data folder paths:
- **Windows** — `%APPDATA%\Fdevelopment\Tidy\`
- **macOS** — `~/Library/Application Support/Tidy/`
- **Linux** — `~/.local/share/Tidy/`

---

## 🛠 License

Freeware. Free to use, no redistribution. See [LICENSE.txt](LICENSE.txt) bundled with the binary.

Built with care in France by **[Fdevelopment](mailto:contact@fdevelopment.fr)**.

*Built quietly, like Tidy itself.*
