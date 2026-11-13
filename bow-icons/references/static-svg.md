# Static SVG delivery

Use `lucide-static` when the project ships static HTML, CSS, or server-rendered HTML, and it has no component system.

## Choose a format

- Individual SVG files: `node_modules/lucide-static/icons/<name>.svg`. Use them in plain HTML and CSS.
- SVG strings from the package: `import { MessageSquare } from 'lucide-static'`. Use them in Node.js, in server rendering, and in static site generation.
- SVG sprite: the file holds every icon. Do not use it on a site with high traffic.
- Icon font: the file holds every icon. Do not use it on a site with high traffic.

## Individual SVG files

```html
<img src="/icons/smile.svg" alt="Smile" />
```

- Use an empty `alt` for a decorative icon: `alt=""`.
- An SVG file loaded with `<img>` cannot take the styles of the page. The file draws with the size and the color that it sets. Use a CSS mask when the icon must follow the text color and the text size.

```css
.icon {
  display: inline-block;
  width: 1em;
  height: 1em;
  background-color: currentColor;
  mask: url('/icons/smile.svg') no-repeat center / contain;
}
```

```html
<span class="icon" aria-hidden="true"></span>
```

- Pin the version in a CDN URL. Icon names change between releases.

```
https://cdn.jsdelivr.net/npm/lucide-static@{version}/icons/smile.svg
```

## SVG strings

```js
import { MessageSquare } from 'lucide-static';
```

- Each export is a string that holds the SVG markup.
- Names are PascalCase. File names are kebab-case. `message-square.svg` becomes `MessageSquare`.
- Inline markup follows the text color of the page, because it uses `currentColor`.
- Make sure decorative markup has `aria-hidden="true"`. Give meaningful markup `role="img"` and a `title`.

```js
import http from 'http';
import { MessageSquare } from 'lucide-static';

const server = http.createServer((req, res) => {
  res.setHeader('Content-Type', 'text/html');
  res.end(`<p>${MessageSquare}</p>`);
});
```

## Notes

- The package holds every icon. Import only the icons that you use.
- Keep one icon style in the interface. Lucide draws outline icons with a stroke width of 2.
