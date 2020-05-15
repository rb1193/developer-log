# CSS

## Gotchas

It isn't possible to use CSS3 transitions to `height: auto`. There are several workarounds involving either JS (slow and janky) or fixing the height of the object somehow but they're all flawed as of May 2020. Best to try to prevent designers doing things like sliding accordions unless you know exactly what content is going in them.
