# my Little World ♡

A dreamy pink, responsive apology-and-memory website for Yogyata. Includes two photo slots, one video slot, a gentle quiz, surprise notes, poetry and a final letter.

## Important privacy note
This project includes **server-side password protection** in `functions/_middleware.js`. Deploy it to **Cloudflare Pages connected to this GitHub repository** to use that protection. GitHub Pages alone only serves static files and cannot run this authentication middleware; do not publish this project on GitHub Pages if you need the password gate. A public GitHub repository also exposes the source code, but not the secret environment variables.

## Deploy with GitHub + Cloudflare Pages
1. Create a GitHub repository (private is fine) and upload the contents of this folder to its root.
2. In Cloudflare, open **Workers & Pages → Create → Pages → Connect to Git** and select the repository.
3. Framework preset: **None**. Build command: leave blank. Build output directory: `/` (the repository root).
4. In the Pages project, open **Settings → Variables and Secrets** and add these as encrypted secrets:
   - `SITE_PASSWORD`: choose a strong password and share it only with Yogyata.
   - `SESSION_SECRET`: generate a long random secret (at least 32 random characters).
5. Redeploy. Open the `*.pages.dev` URL and test the password gate in a private/incognito browser.
6. To use `ourlittleworld.in`, add it under **Custom domains** in the Cloudflare Pages project and follow Cloudflare's DNS instructions. Do not point the domain to GitHub Pages if you want this middleware protection.

The login cookie lasts seven days. Use `/logout` to sign out. Change the password by updating the `SITE_PASSWORD` secret and redeploying.

## Add your real memories
Replace these files with your own media, keeping the filenames:
- `assets/photo-1-placeholder.svg` → rename your first image to `photo-1-placeholder.svg` only if it is actually an SVG; easier: update the `src` in `index.html` to `assets/photo-1.jpg` and add that file.
- `assets/photo-2-placeholder.svg` → update the second image `src` similarly, e.g. `assets/photo-2.jpg`.
- Add your video as `assets/our-memory.mp4` and change the video element to `src="assets/our-memory.mp4"` (remove the current empty video `src` if desired).
- Optional: add a royalty-free or personally owned audio file as `assets/music.mp3` for the music toggle.

The photo/video chooser on the page creates **local previews only**. It does not upload files to the server or save them for other visitors. To share your actual memories with Yogyata, commit the chosen media files to the repository (prefer a private repo and keep video files reasonably compressed).

## Local preview
Open `index.html` in a browser to preview the design. The password gate only works when deployed as Cloudflare Pages Functions.
