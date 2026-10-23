# crewcontrol.app

Static site for Crew Control, served by GitHub Pages at https://www.crewcontrol.app (see `CNAME`). No build step.

- `index.html` + `assets/home.css`: marketing page
- `support/`, `privacy/` + `assets/page.css`: text pages
- `.well-known/`: universal links (`apple-app-site-association`) and Android `assetlinks.json`. `_config.yml` makes Jekyll publish this folder.
- `assets/shots/`: app screenshots, 990px wide WebP (3× the ~300px phone frame, so they stay sharp on Retina)
- `assets/img/`: icon sizes, App Store badge, `og.png` share image (1200×630)

App Store: https://apps.apple.com/app/crew-control-ultra-crewing/id6777703899

## Refreshing screenshots

They come from the raw App Store captures in the app repo:

```
R=../CrewControl/.claude/tmp/appstore/raw/iphone
for s in raceControl pitStop crew plan packing turnaround debrief home stop; do
  magick $R/$s.png -filter Lanczos -resize 990x -quality 88 -define webp:use-sharp-yuv=true assets/shots/$s.webp
done
```

Preview locally with `python3 -m http.server -d .` (paths are root-relative, so opening the file directly won't load assets).
