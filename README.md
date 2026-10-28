# Offload

A private, installable feed for everything you don't want to forget: notes, checklists and reminders, organized with #tags.

Offload is a progressive web app (PWA). It installs to the home screen, works offline, and keeps your entries on your own device.

## Features

- **Notes, checklists and reminders.** Lists take one item per line; end the first line with `:` to name the list. Reminders can repeat on chosen days.
- **Add to Calendar.** Every reminder has an **Add to Calendar** button. On iPhone, new reminders open the "Add to Calendar" screen as soon as they're saved, so the phone alerts you even when Offload is closed. Turn this off in **Settings → Reminders**. On other devices it saves a calendar file to open.
- **One way to organize: #tags.** Type `#work` anywhere in an entry, or tap a suggested tag above the keyboard. The switch at the top picks a view (All, Notes, Lists, Reminders); the tag pills under it narrow that view to one tag. Whenever a tag, Pinned or a search narrows the view, a bar says how many entries are hidden and **Show all** brings them back. Every count matches what you'll see. While a tag is selected, new entries get it automatically. Note, List and Reminder describe *what* an entry is; tags describe *what it's about*.
- **Tag colors.** Hashtags show as bold colored text. Give a tag its own color (six choices, or none) when you create it with **+ Tag**, or select it and tap **Edit tag**. Tags without a chosen color use the theme's accent.
- **Search** covers every entry. Press `/` to jump to it.
- **A real desktop layout.** On screens 1024px and wider, Offload shows a sidebar with views and tags, the capture box at the top with your newest entries right under it, and (from 1280px) an Upcoming reminders panel. Hover an entry to pin, edit or delete it. Press `N` to start a new entry and Ctrl/⌘ + Enter to save.
- **Share target.** On Android, share a link or text into Offload to start a note.
- **New note shortcut.** On Android, press and hold the Offload icon and choose **New note** to open straight to the composer.
- **Your choice of look.** A near-black dark theme by default for new installs, plus light and system; sans, serif or mono font.
- **Backup.** Copy a JSON backup and import it on another device.

**Live app:** https://ggranger757.github.io/OffloadApp/

## Project layout

```
index.html            the app, served by GitHub Pages (built from src/app.html)
manifest.webmanifest  install details: name, icons, colors
sw.js                 offline support (built from src/sw.js)
icons/                app icons
.nojekyll             tells GitHub Pages to serve the files as they are
src/                  source for index.html and sw.js
build.py              rebuilds index.html, sw.js and manifest.webmanifest
tools/make_icons.py   regenerates the icons (needs Pillow)
```

## Publish with GitHub Pages

The built app is committed at the top of the repository, so GitHub Pages serves it directly.

1. Push the files to the `main` branch.
2. Open **Settings → Pages**. Set **Source** to **Deploy from a branch**, branch **main**, folder **/ (root)**, and save.
3. Wait a minute, then open https://ggranger757.github.io/OffloadApp/.

### Making changes

Edit `src/app.html`, then rebuild and commit the result:

```sh
python3 build.py
git add -A && git commit -m "Update app" && git push
```

To try it locally first, run `python3 -m http.server 8080` in the repository folder and open http://localhost:8080.

### Install on a phone

- **iPhone (Safari):** open the address, tap Share → Add to Home Screen.
- **Android (Chrome):** open the address, tap the menu → Install app.

## Limits

- Entries live on one device. Use **Settings → Backup** to move them.
- Offload's own reminder alerts only appear while the app is open or running in the background. Use **Add to Calendar** for alerts that arrive when it's closed.
- Apple doesn't let web apps add to the Reminders or Calendar app without the user confirming, so adding to Calendar always takes one tap. Editing a reminder in Offload doesn't change a copy already in Calendar.

## License

MIT. See [LICENSE](LICENSE).
