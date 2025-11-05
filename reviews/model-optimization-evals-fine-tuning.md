# Review: "Model optimization with evals and fine-tuning" HTML draft

## Summary
The draft is well structured and accessible overall, but a few refinements will improve performance, semantics, and machine readability.

## Issues & Recommendations

1. **Defer loading of large remote images.**
   Both figures pull high-resolution Unsplash assets synchronously:
   ```html
   <img src="https://images.unsplash.com/photo-1520607162513-77705c0f0d4a?...">
   ...
   <img src="https://images.unsplash.com/photo-1527477396000-e27163b481c2?...">
   ```
   Add `loading="lazy"` (and ideally explicit `width`/`height`) so the hero content renders faster and avoids cumulative layout shift for readers who never scroll to the art.

2. **Represent grouped resource links as lists.**
   Sections such as “Resources and links” and the fine-tuning resource cluster use a bare `<div class="links">` wrapper with multiple anchors. Screen readers won’t announce the collection as a list, which makes navigation harder. Wrap each cluster in a semantic list (`<ul><li><a>…`) to communicate that they’re related items.

3. **Mark up the update timestamp with `<time>`.**
   The metadata line currently presents “Updated Nov 2025” as plain text. Using a `<time datetime="2025-11-01">` (or the exact day if known) improves machine readability for search engines and assistive tech without changing the visual design.

## Nice touches
* Clear heading hierarchy with skip-link support.
* Thoughtful use of `aria-labelledby` and descriptive alt text on imagery.
