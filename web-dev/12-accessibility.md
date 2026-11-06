# Web Accessibility Engineering

Accessibility is a core quality attribute. Build inclusive behavior into components and workflows rather than treating it as a final audit.

## Foundations

Use semantic HTML first. Native buttons, links, headings, labels, lists, tables, and form controls provide expected keyboard and assistive-technology behavior. Add ARIA only when native semantics are insufficient; incorrect ARIA can make experiences worse.

## Keyboard and focus

- Every interactive control is reachable and operable by keyboard.
- Focus order follows the visual and logical reading order.
- Focus is visible and never obscured.
- Dialogs manage focus, support Escape where appropriate, and return focus to the trigger.
- Avoid keyboard traps except within intentionally modal interactions.

## Content and visuals

Use meaningful headings, descriptive link text, labels and instructions, sufficient contrast, and text alternatives for informative images. Do not rely on color alone. Respect reduced-motion preferences and avoid flashing content.

## Forms

Associate labels programmatically, explain required formats, identify errors in text, and connect error messages to fields. Preserve entered data after validation errors. Announce dynamic status changes appropriately without overwhelming screen readers.

## Testing

Combine automated checks with manual keyboard, screen-reader, zoom/reflow, and mobile testing. Automated tools catch only a subset of issues. Include users with disabilities in research where possible.

## Checklist

- [ ] Semantic structure and heading order are meaningful.
- [ ] Keyboard access and visible focus work.
- [ ] Forms have labels and actionable errors.
- [ ] Contrast, zoom, reflow, and text resizing are usable.
- [ ] Images and media have appropriate alternatives/captions.
- [ ] Motion and dynamic updates are considerate.
- [ ] Automated and manual testing are part of delivery.
