# Sarim's Site — Setup Notes

## File structure
```
index.html
assets/
  background.jpg
  now-loading.png
  page-2-elements.png
  earth.png
  page-3-elements.png
  page-3-heart.png
  page-4-elements.png
```
Upload the **whole folder** (index.html + the assets folder together) — the image paths in the code expect `assets/` to sit right next to `index.html`.

## Putting it on GitHub Pages
1. Create a new repo on GitHub (e.g. `sarim`).
2. Upload `index.html` and the `assets/` folder to the root of the repo.
3. Go to repo **Settings → Pages**.
4. Under "Build and deployment," set Source = `Deploy from a branch`, Branch = `main` / `root`.
5. Save — GitHub gives you a live link like `https://yourusername.github.io/sarim/` within a minute or two.

## How the site works
One `index.html`, everything else inline (CSS in `<style>`, logic in `<script>` at the bottom). All your real Canva exports are layered as positioned images inside a fixed 16:9 "canvas" div, which is kept centered and letterboxed at any window size by a small resize script — so positions never drift.

Flow: `loading → welcome (click earth) → family (click heart) → profile (Sarim) → Our Timeline / A poster for you / A video for you`

The earth, heart, and the three Sarim-page buttons are all real click targets (the earth/heart are the actual image elements; the timeline/poster/video buttons are invisible "hotspot" divs positioned exactly over the button graphics baked into `page-4-elements.png`).

## Adding timeline milestones
Open `index.html`, find this block near the top of the `<script>`:

```js
const milestones = [
  { date: "Apr 2026", title: "Found out!", desc: "..." },
  ...
];
```

Copy a line and edit the date/title/desc — the dots, spacing, and click-to-open popup all generate automatically from this array.

## Known limitations / things to know
- **Family reveal isn't figure-by-figure.** Your video animates each family member appearing one at a time, but the Canva export (`page-3-elements.png`) is one flattened image with everyone already in place — there aren't separate cutouts per person. Right now it does a single fade+scale-in for the whole scene. If you want the one-by-one reveal back, you'd need each family member as their own transparent PNG (re-export from Canva selecting just that character) — happy to wire that up once you have them.
- **Poster / video pages are placeholders** — drop an `<img>` or `<video>` tag into the dashed box in the `#poster` / `#video` sections once you have the files.
- **The blank 4th box** on Sarim's profile page (top-left) has no link yet — left open for whatever you decide later.

