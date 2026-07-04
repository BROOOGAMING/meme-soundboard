# Sound Machine

A click-to-play soundboard for your YouTube clip library. Static site — no build step, no backend.

## 1. Add your audio files

Drop your actual `.mp3` files into the `sounds/` folder. **File names must match exactly** (case-sensitive), because the page looks for `sounds/<name>.mp3`.

Example — for the pad labeled "spiderman meme song" to work, you need:
```
sounds/spiderman-meme-song.mp3
```

The full list of expected file names is at the top of `index.html` inside the `clips` array. If you rename, add, or remove files, just edit that array to match — one name per line, no `.mp3` extension in the array (the code appends it automatically).

Any file that's missing just shows up dimmed on the page instead of breaking anything.

## 2. Test it locally

You can't just double-click `index.html` in some browsers because of how audio loading works with `file://` paths. Easiest fix — run a tiny local server from inside the project folder:

```bash
# Python (already on most systems)
python3 -m http.server 8000
```

Then open `http://localhost:8000` in your browser.

## 3. Deploy — GitHub Pages

1. Create a new repo on GitHub and push this folder to it:
   ```bash
   git init
   git add .
   git commit -m "sound machine"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
2. On GitHub: **Settings → Pages → Source → Deploy from a branch → main / (root)** → Save.
3. Your site goes live at `https://<your-username>.github.io/<repo-name>/` within a minute or two.

## 4. Deploy — Vercel (alternative)

1. Push the folder to a GitHub repo (same steps as above).
2. Go to [vercel.com](https://vercel.com) → **Add New Project** → import the repo.
3. Framework preset: **Other** (it's a static site, no build command needed).
4. Deploy. Vercel gives you a live URL immediately.

Either option works fine — GitHub Pages is simpler for a plain static page like this; Vercel is nice if you want custom domains or plan to add more later.

## Notes

- Audio files can get large — GitHub has a 100MB per-file limit and repos start warning around 1GB total. If your library grows a lot, consider Git LFS or hosting the mp3s elsewhere (e.g. a CDN) and pointing the `clips` array at full URLs instead of local paths.
- The search bar filters by name, so as your collection grows you can still find a clip fast.
