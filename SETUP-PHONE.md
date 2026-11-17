# Trip Viewer - one-time setup (about 15 minutes)

## Already set up? Turning on check-ins (2 minutes)
Check-ins (Arrived / Leaving) need permission to write one small file per trip.
1. dropbox.com/developers/apps › your app › **Permissions** tab › also tick **files.content.write** › **Submit**.
2. Upload the new viewer files to the `trip-viewer` repo (replace all of them, including the new **leaflet** folder:
   on the repo page, **Add file › Upload files**, drag in everything, **Commit changes**).
3. On the phone: open the viewer, ⚙ › **Disconnect Dropbox**, then **Save & Connect Dropbox** and **Allow** again
   (the old sign-in doesn't carry the new permission). Put the phone's name in ⚙ while you're there.
4. Update Travel Planner 2.0 on both computers. Each trip's phone copy is refreshed on the next sync.


You'll do three things: put the viewer on GitHub Pages, make a small Dropbox "app" so the
viewer is allowed to read your trip files, and point Travel Planner 2.0's sync at that folder.

## 1. Put the viewer on GitHub (computer)
1. Go to https://github.com/new
   - Repository name: `trip-viewer`
   - Public (Pages is free for public repos; only the viewer's code is in it, never your trips)
   - Click **Create repository**.
2. On the new repo page, click **uploading an existing file**. Drag in all the files from
   this folder (index.html, sw.js, manifest.webmanifest, the three .png icons, README.md).
   Click **Commit changes**.
3. Repo **Settings › Pages**: Source = **Deploy from a branch**, Branch = **main**, folder **/ (root)**, **Save**.
   After a minute or two the viewer is live at **https://t-fultz.github.io/trip-viewer/**

## 2. Make the Dropbox app (computer)
1. Go to https://www.dropbox.com/developers/apps and click **Create app**.
   - **Scoped access**
   - **App folder** (the viewer can only see one folder - not the rest of your Dropbox)
   - Name: anything unique, e.g. `Fultz Trip Viewer`
2. **Permissions** tab: tick **files.metadata.read**, **files.content.read** and **files.content.write**, then **Submit**.
   (Do this before signing in on the phone.)
3. **Settings** tab:
   - Under **OAuth 2 › Redirect URIs** add exactly: `https://t-fultz.github.io/trip-viewer/` and click **Add**.
   - **Allow public clients (Implicit Grant & PKCE)** must say **Allow**.
   - Copy the **App key** (not the secret - the viewer never needs the secret).

## 3. Phone
1. Open **https://t-fultz.github.io/trip-viewer/** in Safari.
2. Tap **Set Up**, paste the App key, leave Folder blank, tap **Save & Connect Dropbox**, sign in, tap **Allow**.
3. Share button › **Add to Home Screen** so it opens like an app.

Signing in creates a folder in your Dropbox: **Dropbox › Apps › Fultz Trip Viewer** (your app's name).

## 4. Point Travel Planner 2.0 at that folder (each computer)
Menu › **Sync Folder…** › **Change Folder…** › choose **Dropbox/Apps/Fultz Trip Viewer**.
Do the computer with the newest trips first, then the other one. (The viewer can only see
that one folder, so 2.0's sync has to live there rather than in Claude Apps.)
Back on the phone, tap ⟳.

## On the road
- **Arrived / Leaving now / Passed** on each stop records the time. The hotel at the end of a day gets
  **Arrived**, then **Leaving (next morning)**. Tap **Edit** (or ⋯) to fix a time you forgot to tap, or mark a stop skipped.
- Once you've checked in, the day shows **Running X min behind / ahead** and the rest of the day's times are
  adjusted (~). A stop with a fixed leave time (checkout, a reservation) absorbs the difference.
- No signal? Check-ins are kept on the phone and sent when it's back online.
- **Navigate in Maps** opens Apple Maps with driving directions. The **Map** tab shows the day's route and pins
  (✓ = done); **Where am I** shows your position.
- On the computer, the **Actual** tab shows planned vs actual for every stop, and the Overview gets an Actual column.
  Check-ins go into a separate "… .progress.json" file - the trip plan is never changed. **Clear Check-ins…**
  there starts over (e.g. after a test run).

## Notes
- The plan is edited on a computer only; the phone picks it up on the next ⟳.
- A trip shows on the phone once Travel Planner 2.0 has saved it to that folder (turning sync on does it).
- Days with two plans show the plan that's chosen on the computer.
- Disconnect any time in the viewer's ⚙, or remove access at dropbox.com › Settings › Connected apps.
