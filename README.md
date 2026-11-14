# George Happold's Portfolio

My personal portfolio site: a pixel-art village you can explore. Each page is a different biome, and the villagers at the bottom wander around, stop to chat with each other, and can be picked up and dropped onto another tab to move them to a different biome.

**Live site:** george.happold.org

## Features

- Four pages (Home, Projects, Experience, Contact), each with its own parallax background
- Villagers with idle and walk animations that wander, stop and talk to each other
- Drag and drop villagers anywhere, or onto a tab to send them to that biome
- Light and dark mode switch
- Works on desktop and mobile (touch dragging included)
- No frameworks or build step, just HTML, CSS and JavaScript

## How it works

Everything is in `index.html`, and the code is commented section by section.

- **Sprites:** each animation is a row in a sprite sheet. The page shows one 32x32 frame at a time by sliding the sheet behind a small window with CSS `background-position`, then steps through the frames in a `requestAnimationFrame` loop.
- **Villagers:** each one is a small state machine (idle, walk, chat, held, fall). Falling uses simple gravity, and dragging uses pointer events so mouse and touch work the same way.
- **Parallax:** every background is a stack of image layers that move by different amounts as the mouse moves.
- **Pages:** the URL hash (`#home`, `#projects`, ...) decides which section and background is shown, and villagers belong to a biome.

## Project structure

```
portfolio/
├── index.html              the whole site (HTML, CSS and JavaScript)
├── George_Happold_CV.pdf   linked from the Contact page
└── assets/
    ├── bg/
    │   ├── home/           parallax layers 1.png (back) to 5.png (front)
    │   ├── projects/
    │   ├── experience/
    │   └── contact/
    └── villagers/          villager1.png, villager2.png, ...
```

## Running it locally

There's nothing to install. The simplest way is to serve the folder:

```bash
cd portfolio
python3 -m http.server 8000
```

Then open http://localhost:8000. (Opening `index.html` directly can work too, but a local server behaves like the real site.)

## Customising

The settings are at the top of the script in `index.html`:

- **Add a villager:** add an entry to `CONFIG.villagers` with a biome and the sprite sheet rows for idle and walk.
- **Change frame size or speed:** `frameW`, `frameH`, `scale` and `fps` in `CONFIG`.
- **Change backgrounds:** edit the `BIOMES` object.
- **Change what villagers say:** edit the `LINES` list.

## Deployment

The site is hosted on Cloudflare Pages and connected to this repo, so every push to `main` redeploys it automatically. There is no build command, and the output directory is the repo root.

## Credits

- Villager sprites: [Mini Villagers by LyaseEk](https://lyaseek.itch.io/minifvillagers)
- Backgrounds: [Free Summer Pixel Art Backgrounds by free-game-assets](https://free-game-assets.itch.io/free-summer-pixel-art-backgrounds)
- Fonts: [Silkscreen](https://fonts.google.com/specimen/Silkscreen) and [Nunito](https://fonts.google.com/specimen/Nunito) from Google Fonts

The art belongs to its creators and is used under the licences on their itch.io pages.

## Contact

george@happold.org | [LinkedIn](https://linkedin.com/in/georgehappold) | [GitHub](https://github.com/GeorgeHappold)
