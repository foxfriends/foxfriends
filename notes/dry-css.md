# DRY-CSS

__DRY CSS__ is a @[CSS methodology][css-methodologies] that emphasizes @[DRY][].
Rather than writing 1 block of styles for each selector, oftentimes repeating
the actual rules applied to each, DRY CSS basically says to write each rule only
once, and list off all the @[selectors][css-selector] to which it applies.

While I don't personally suggest holding to this strictly at all times, in certain
situations it really does help a lot. At the very least, it's at least worth remembering
that you can list multiple selectors for a rule, so there's no need to repeat whole
blocks for similar elements.
