---
name: bow-icons
description: Add icons to an interface with Lucide. Use when a task adds, reviews, or fixes icons in an interface. Covers icon choice, sizing, styling, accessible names and framework-specific setup.
---

# Icons in an interface

Icons help people scan an interface, recognize actions, and read status. They help only when their meaning is clear. This skill gives the rules for adding icons. It covers two ways to ship them: Preact components and static SVG files.

## Steps

Use the steps in order. Each step ends with a condition that tells you the step is done.

### 1. Write the meaning

Write one short phrase for each icon slot. Use a verb for an action (delete, save, open) and a noun for a thing (settings, profile).

Done when every icon slot has one phrase that a person can read as text.

### 2. Run the icon test

Use an icon when these three statements are true:

- People already know the symbol for this action or thing.
- The symbol stays clear in this context.
- The icon sits next to a visible label, or the control shows its name on hover, focus, or tap.

Use text instead of an icon when:

- The meaning is complex, abstract, or easy to misunderstand.
- No common symbol exists for the meaning.
- The control already shows people how it works. Use the built-in cue of the control.

Done when every icon slot has a decision: an icon or text.

### 3. Choose the symbol

- Use one icon style for related controls. Do not mix outline icons and filled icons in the same interface.
- Use the familiar symbol. Use `trash-2` to delete an image. Do not use `image-off`.
- Use the same icon for the same meaning. Use a different icon for a different meaning.
- Choose a symbol that people recognize in any culture. Do not use puns, idioms, or local references.
- Use the action that the context already explains. Do not add the object when the context shows it.
- Make sure that the name exists in the icon list before you import it. Names change between releases. `home` is now `house`. `check-circle` is now `circle-check`. `alert-triangle` is now `triangle-alert`.
- Use [references/symbols.md](references/symbols.md) for common concepts. Make sure that the name exists in the icon list at <https://lucide.dev/icons>.

Done when every icon has one name, and that name means the phrase from step 1.

### 4. Pair the icon with text

- The icon supports the text. The icon does not compete with the text.
- Use icons as visual anchors in lists, menus, cards, and repeated controls.
- Do not add an icon to every line of a list when it only adds noise.
- Do not add a status icon to every row when color, weight, text, or layout already shows the state.
- Keep visible labels in compact layouts when space allows.
- Use an icon-only control only when the symbol is widely understood and the name is available on hover, focus, or tap.

Done when every icon has a visible label, or the control shows its name on hover, focus, or tap.

### 5. Set size and style

- The Lucide defaults are a size of 24 pixels, a color of `currentColor`, and a stroke width of 2.
- Set the icon size to match the text next to it. Use `1em`, or 16 pixels next to 16-pixel text.
- Let the icon take the text color of its element. Icons use `currentColor`.
- Keep one stroke width for all icons in one interface.
- Use `nonScalingStroke` when the icon must keep the same stroke weight at different sizes.

Done when all icons in the interface use one size rule and one stroke width.

### 6. Give the icon an accessible name

- Lucide icons carry `aria-hidden="true"`. Keep it for decorative icons.
- Give a decorative icon no accessible name.
- Put the accessible name on the control, not on the icon inside it.
- Prefer visually hidden text inside the control over `aria-label`.
- Give a standalone icon an accessible name with `aria-label` or with a `title` child.
- Keep the contrast between the icon and its background at 4.5:1 or higher.
- Give state a second cue. Use shape, text, or shading. Do not use color alone.
- Make the control focusable and at least 44 by 44 pixels. The icon itself can be smaller.

Done when every decorative icon stays hidden from screen readers, and every icon control has an accessible name.

### 7. Ship the icon

Read the file for the way the project ships icons, then follow it.

- The project renders Preact: read [references/preact.md](references/preact.md).
- The project ships static HTML, CSS, or server-rendered HTML: read [references/static-svg.md](references/static-svg.md).
- The project uses another framework: apply the same rules with the Lucide package of that framework, for example `lucide-react`.

Done when the icon appears with the size, the color, and the name from the steps above.

### 8. Check the result

Run the check list in [references/checklist.md](references/checklist.md).

Done when every item on the list passes.

## External sources

The rules come from the Lucide guides.

- [How to use Lucide icons](https://lucide.dev/how-to/)
- [Accessibility in depth](https://lucide.dev/how-to/accessibility)
- [How to pick the right icon](https://lucide.dev/how-to/icon-guide)
- [Lucide for Preact](https://lucide.dev/guide/preact/)
- [Lucide static assets](https://lucide.dev/guide/static/)
