# Preact delivery

Use `lucide-preact` when the project renders Preact.

## Import one icon

```jsx
import { Camera } from 'lucide-preact';

export function Toolbar() {
  return <Camera />;
}
```

- Each icon is a Preact component that renders an inline SVG element.
- The package uses ES modules. The bundler drops icons that you do not import. Import icons one by one.
- All SVG attributes work as props.

## Props

| Prop | Type | Default | Use |
| --- | --- | --- | --- |
| `size` | number | 24 | Pixel size of the icon. |
| `color` | string | `currentColor` | Stroke color of the icon. |
| `strokeWidth` | number | 2 | Weight of the stroke. |
| `nonScalingStroke` | boolean | false | Keep the stroke width constant at every size. |

```jsx
<Camera size={48} color="red" strokeWidth={1} />
```

## Style all icons

- Use CSS first. Every icon has the class `lucide`.

```css
.lucide {
  color: #ffadff;
  width: 48px;
  height: 48px;
  stroke-width: 1px;
}
```

- CSS wins over the props. Use `LucideProvider` when needing to override size, color, or stroke for many icons but not for all of them.

```jsx
import { LucideProvider, Home } from 'lucide-preact';

export function App() {
  return (
    <LucideProvider color="red" size={48} strokeWidth={2}>
      <Home />
    </LucideProvider>
  );
}
```

- Keep the stroke weight constant at every size with `vector-effect: non-scaling-stroke` in CSS, or with the `nonScalingStroke` prop on one icon.

## Give the icon an accessible name

- Icons ship with `aria-hidden="true"`. A name removes it.

```jsx
<House aria-label="This is my house" />
<House><title>This is my house</title></House>
```

- Put the name of an icon button on the button.

```jsx
<button aria-label="Go to home">
  <House />
</button>
```

- Visually hidden text is more reliable than `aria-label`.

```jsx
<button className="btn-icon">
  <House />
  <span className="sr-only">Go to home</span>
</button>
```

## Compose icons

- Nest one icon inside another to build a custom icon. Keep `x` and `y` inside the 24 by 24 viewBox of the outer icon.
- Native SVG children work. Use a `circle` for a badge, and `text` for a short mark.

```jsx
import { Scan, User } from 'lucide-preact';

<Scan size={48} nonScalingStroke>
  <User size={12} x={6} y={6} nonScalingStroke />
</Scan>
```

## Notes

- Fills are not official in Lucide. The `fill` prop works on some icons. Check the result in the browser.
- Some icons have more than one name. Use the current name from the icon list at <https://lucide.dev/icons>.
