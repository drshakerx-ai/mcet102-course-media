# GitHub Pages delivery for the course site

The course app now loads files directly from this repository's GitHub Pages site rather than copying them into the app.

- Hosting source: main branch, repository root, static files preserved by `.nojekyll`.
- Course media base: `https://drshakerx-ai.github.io/mcet102-course-media/public`
- Example video: `https://drshakerx-ai.github.io/mcet102-course-media/public/videos/Exp01/MCET102_Exp01_Step01.mp4`
- Example lab: `https://drshakerx-ai.github.io/mcet102-course-media/public/labs/MCET102_Exp01_Virtual_Lab.html`

All 90 uploaded MP4 videos, 12 HTML labs, and the manifest remain in their original `public/` paths unchanged. Future uploads go in those same folders on main; GitHub Pages republishes automatically. There is no need to copy files into Lovable. Preserve case-sensitive filenames matching course.json. If an uploaded file changes, update the SHA-256 manifest as part of that media update.

The frontend app uses one media address for video playback, per-video blob downloads, experiment ZIPs, lab availability checks, iframes, and new-tab links. Missing files show the course's existing coming-soon state.

When a student is signed in on the course site, the lab URL includes `sid`, `name`, and `section`, encoded as URL query parameters. The lab can read these using `new URLSearchParams(location.search)`. These are convenience fields, not authenticated access credentials. The lab runs on the GitHub Pages origin, separate from the course site's per-student localStorage. Do not upload private student records, passwords, or API keys. Keep supporting assets relative to the lab HTML so the repository subpath works.

This repository hosts public course media only. It is separate from Lovable's app-code Git sync.
