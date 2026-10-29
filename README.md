# Brain Load

A private, installable feed for everything you don't want to forget: notes, checklists and reminders, organized with #tags.

Brain Load is a progressive web app (PWA). It installs to the home screen, works offline, and keeps your entries on your own device.

## Features

- **Notes, checklists and reminders.** Lists take one item per line; end the first line with `:` to name the list. Reminders can repeat on chosen days.
- **Add to Calendar.** Every reminder has an **Add to Calendar** button. On iPhone, new reminders open the "Add to Calendar" screen as soon as they're saved, so the phone alerts you even when Brain Load is closed. Turn this off in **Settings → Reminders**. On other devices it saves a calendar file to open.
- **One way to organize: #tags.** Type `#work` anywhere in an entry, or tap a suggested tag above the keyboard. Tags appear as chips under the filter row; tap one to see only those entries. While a tag is selected, new entries get it automatically. Note, List and Reminder describe *what* an entry is; tags describe *what it's about*.
- **Tag colors.** Tags you create with **+ New tag** get a small colored dot inside the pill. Pick any of six colors (or none); tap **⋯** on a selected tag to change it later. Tags you only type as `#name` stay plain until you give them a color.
- **Search** covers every entry.
- **Mind map.** Tap the map icon in the header to see everything as a mind map: Brain Load in the middle, a branch for each #tag (or for Notes, Lists and Reminders), your entries on each branch, and list items on the end. Drag to move, pinch or ⌘/Ctrl-scroll to zoom, and tap **Fit** to see it all. Tap a branch to fold it. Tap **+** on a branch to brainstorm new notes straight into it, or **+** under the center to start a new tag. Tap an entry for its options, or tap a list item to check it off.
- **Export as PDF.** Tap the document icon in the header (or **Settings → Export**, or press ⌘/Ctrl+P). Choose everything or just the current view, organize by type, tag or date, and choose whether to include a mind map page and completed reminders. The preview shows the finished document: a cover with totals, a contents page, the mind map, every entry in a clean layout with dates, checklists, due times and tags, and a tag index. Tap **Save as PDF** to save it with the system print dialog. On iPhone, tap Share in the print screen, then Save to Files. Text stays selectable and links stay clickable.
- **Share target.** On Android, share a link or text into Brain Load to start a note.
- **Quick add by voice.** Opening `…/Offload_App/?add=your%20text` saves a note immediately (add `&tag=work` to tag it). Use it from a Siri Shortcut (Dictate Text → URL Encode → Open URLs) or an Android automation app. On iPhone the link opens Safari, which stores entries separately from the home-screen app. `?new=1` just opens the composer; Android's long-press **New note** shortcut uses it. Steps are in **Settings → Quick add by voice**.
- **Your choice of look.** Light, dark or system theme; sans, serif or mono font.
- **Backup.** Copy a JSON backup and import it on another device.

**Live app:** https://ggranger757.github.io/Offload_App/

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
3. Wait a minute, then open https://ggranger757.github.io/Offload_App/.

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
- Brain Load's own reminder alerts only appear while the app is open or running in the background. Use **Add to Calendar** for alerts that arrive when it's closed.
- Apple doesn't let web apps add to the Reminders or Calendar app without the user confirming, so adding to Calendar always takes one tap. Editing a reminder in Brain Load doesn't change a copy already in Calendar.

## License

MIT. See [LICENSE](LICENSE).
