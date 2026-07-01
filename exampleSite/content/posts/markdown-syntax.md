+++
title = 'Markdown Syntax Guide'
date = 2026-07-01T12:00:00Z
draft = false
toc = true
tags = ['syntax', 'markdown', 'test']
+++

A complete reference of Markdown elements rendered by the **ReaderFirst** theme. Use this page to verify typography, spacing, color contrast in both light and dark modes, and that the table of contents (TOC) on the right tracks every heading below.

## Headings

The following six headings descend through every level from H1 to H6. They are intentionally short so you can see how each level's font size, weight, and vertical rhythm differs.

# H1 — Heading Level One

## H2 — Heading Level Two

### H3 — Heading Level Three

#### H4 — Heading Level Four

##### H5 — Heading Level Five

###### H6 — Heading Level Six

## Inline Formatting

A paragraph demonstrating **bold text**, *italic text*, ***bold italic***, ~~strikethrough~~, and `inline code`. You can also link out to the [Hugo documentation](https://gohugo.io/documentation/) or reference a [relative post](/posts/post-1/) on this very site. The sentence ends with an emoji-style punctuation mark—this em dash is paired with the previous word to test that horizontal spacing around punctuation reads well at body width.

Two more sentences follow to form a real paragraph rather than a one-liner. They exist only to make the line break and justification behavior visible at the reading column width configured by the theme. Longer paragraphs help confirm that measure (characters per line) stays within a comfortable reading range of roughly 60–75 characters.

## Blockquotes

> Single-line blockquote: a reader lives a thousand lives before he dies. The man who never reads lives only one.
>
> A second paragraph inside the same blockquote, separated from the first by a blank `>` line. This is the canonical way to keep multiple paragraphs under one quote.
>
> > A nested blockquote. Nesting should be visually offset—extra left border, indent, or tinted background—so readers can tell who is quoting whom.
> >
> > Nesting can go deeper still, but deeper than two levels usually hurts readability.

## Lists

### Unordered List

- First item in an unordered list
- Second item with a child list
  - Nested child A
  - Nested child B
    - Deeper grandchild
- Third item, back to the top level

### Ordered List

1. First ordered item
2. Second ordered item with a nested list
   1. Nested ordered child 1
   2. Nested ordered child 2
3. Third ordered item, returning to top level

### Mixed Nested List

1. Ordered top level
   - Unordered child
     - Deeper unordered grandchild
2. Another ordered top level
   - Another unordered child

## Table — Alignment Test

A table with three columns, each demonstrating a different alignment: left, center, and right.

| Feature        | Status      | Score |
| :------------- | :---------: | ----: |
| Minimal layout | Done        |    95 |
| Dark mode      | Done        |    92 |
| TOC generation | Done        |    88 |
| JSON Feed      | Done        |    90 |
| Accessibility  | In progress |    74 |

## Code Block with Syntax Highlighting

A fenced code block with language hint, used to verify the highlighter style (`github`) and that line wrapping behaves inside the reading column.

```go
package main

import "fmt"

func main() {
    names := []string{"ReaderFirst", "Hugo", "Markdown"}
    for i, name := range names {
        fmt.Printf("%d: hello from %s\n", i, name)
    }
}
```

A second fenced block in a different language confirms the highlighter handles multiple grammars:

```python
def greet(names):
    for i, name in enumerate(names):
        print(f"{i}: hello from {name}")

if __name__ == "__main__":
    greet(["ReaderFirst", "Hugo", "Markdown"])
```

And a JavaScript block for the web-native case:

```javascript
const names = ["ReaderFirst", "Hugo", "Markdown"];
names.forEach((name, i) => {
  console.log(`${i}: hello from ${name}`);
});
```

## Image

A test image placed on its own line, followed by a caption paragraph. The image should scale to the reading column width, never overflow horizontally, and keep its aspect ratio in both light and dark modes.

![Bryce Canyon test photo used to verify responsive image rendering](/posts/post-3/bryce-canyon.jpg)

## Horizontal Rule

A thematic break below separates sections. It should render as a thin, low-contrast rule aligned to the reading column.

---

## Final Paragraph

If every element above renders cleanly—correct heading hierarchy, readable measure, aligned table columns, syntax-highlighted code, responsive image, and a working TOC—then the theme's reading-first typography is verified. Any drift here is a regression to fix before release.
