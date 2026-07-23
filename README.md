# mobidraw

[![Project: mobidraw](https://img.shields.io/badge/project-mobidraw-blue?style=flat-square)](https://github.com/krishkr-ctl/mobidraw)
[![License: MIT](https://img.shields.io/badge/license-MIT-lightgrey?style=flat-square)](LICENSE)

A simple, mobile-first drawing web app built with plain HTML, CSS and JavaScript. Designed to be lightweight and easy to extend — great as a learning project, demo, or quick drawing utility.

---

## Demo

Open `index.html` in your browser (desktop or mobile) to start drawing. The app supports touch and mouse input. For local development you can use a static server:

```bash
npx http-server .
# then open http://localhost:8080
```

(Consider enabling GitHub Pages for an online demo: Settings → Pages → Deploy from main branch.)

## Features

- Draw with touch or mouse
- Choose stroke color
- Adjust brush size
- Clear canvas
- Save drawing as PNG
- Minimal dependencies — no frameworks required

## How it works (brief)

The core is an HTML5 <canvas> element. The app:

- Listens for pointer/touch/mouse events (pointerdown, pointermove, pointerup or touchstart/touchmove/touchend)
- Tracks the current pointer position and draws strokes using the 2D canvas context
- Exposes simple UI controls (color, brush size, clear, save) which manipulate canvas drawing state

This approach keeps the app small and compatible across modern browsers.

## Suggested file structure

If you prefer separating files, a typical layout looks like:

- index.html — main page & markup
- styles.css — UI styles and responsive rules
- script.js — canvas logic (event handlers, drawing, save/clear functions)
- assets/ — optional images or icons

If your HTML already bundles styles and scripts inline, that works too.

## Configuration & customization examples

- Change default color and brush size in the script (look for `context.strokeStyle` and `context.lineWidth`).
- Add an undo feature by storing an array of canvas image snapshots (use canvas.toDataURL()).
- Support multi-touch gestures (pinch-to-zoom) by listening for touch events and handling scale transforms.
- Export higher-resolution images by drawing to an offscreen canvas at a larger scale before calling `toDataURL()`.

Example: set default brush size in `script.js`:

```js
// default settings
let brushSize = 6; // pixels
let brushColor = '#000000';
context.lineWidth = brushSize;
context.strokeStyle = brushColor;
```

## Development

- Edit the HTML/CSS/JS files in your editor of choice.
- Use a local static server while developing to avoid CORS issues and to enable quick refreshes:

```bash
# using a simple node server
npx http-server .
```

- Test on desktop and a mobile device (or use device emulation in Chrome DevTools).

## Accessibility & UX notes

- Ensure UI controls have accessible labels (use `<label>` or `aria-label`) so screen readers can describe color/brush controls.
- Make interactive elements large enough for touch (recommended minimum: 44x44 CSS pixels).
- Provide sufficient color contrast for any UI text and icons.

## Browser support

Designed for modern browsers with HTML5 canvas and pointer/touch events support. Works in Chrome, Firefox, Safari, Edge on mobile and desktop. If you need to support very old browsers, consider polyfills.

## Troubleshooting

- Canvas appears blank: check that `canvas.width`/`canvas.height` are set and the drawing code uses correct coordinates.
- Drawings look jagged: enable `context.lineJoin = 'round'` and `context.lineCap = 'round'` and use smoothing techniques (interpolate between points).
- Save/export fails: ensure you call `canvas.toDataURL('image/png')` after any drawing operations and trigger a download from an anchor with `download` attribute.

## Roadmap / Ideas

- Add undo/redo
- Layers support
- Pressure sensitivity for stylus devices
- Share drawings via Web Share API or upload to a backend
- Add presets (brush shapes, textures)

If you'd like help implementing any of these, I can open issues and provide starter code.

## Contributing

Contributions, issues and feature requests are welcome!

1. Fork the project
2. Create your feature branch (`git checkout -b feature/my-feature`)
3. Commit your changes (`git commit -m "Add some feature"`)
4. Push to the branch (`git push origin feature/my-feature`)
5. Open a Pull Request

When opening a PR, please include a short description of changes and screenshots or a small demo if applicable.

## Credits

Created by @krishkr-ctl.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Need more specific content? I can:

- Embed screenshots or a demo GIF (add files to the repo and I'll update the README with the images),
- Add a sample `script.js` with undo/save features, or
- Create a CONTRIBUTING.md and ISSUE_TEMPLATEs to help manage contributions.
