# <a name="top">Reg Dev Guide

##### Topics

- [Themes](Themes/README.md)
  - [Theme.config](theme_config/README.md)
  - [File Structure](file_structure/README.md)
- [API Overview](api_docs/README.md)
- [Custom Presenters Fields](presenter_fields/README.md)
- [Custom Venue Fields](venue_fields/README.md)
- [Notifications](notifications/README.md)
- [Registration Importing](reg_import/README.md)

---

## <a name="1">Style Guide

##### About This Guide

- This guide will outline the basic style rules in use throughout this guide. Sticking to a single set of guidelines will help us keep the guide maintainable and clean.
- At the end of the day, these are just guidelines--try to adhere to them as often as possible, but don't fret if it makes sense to break them from time to time. Use your best judgement!
- The guidelines are written assuming you have a decent understanding of Markdown syntax, as it is out of the scope of this guide to cover.
- When in doubt, check the unrendered Markdown source for any of these pages.

##### Headers

- Headers should be created with leading `#` syntax, rather than underlines.
- Headers of all sizes should have one blank line both above and below them.
- Page title should be on the first line of the page as an h1 element, by using `#`
- "Major" headers, to denote sections, should be h2 elements, by using `##`
- "Minor" headers, to denote sub-sections, should be h5 elements, by using `#####`

##### Code

- Code blocks should use Github style "fence" notation, contained within sets of three back-ticks, with the name of the language written in all lowercase next to the first set. [(Fenced Code Blocks)](https://help.github.com/articles/creating-and-highlighting-code-blocks/#fenced-code-blocks)
- Code blocks should always be fully left-aligned to the page's margin, even if the text above is indented (e.g. within a bullet list). This will ensure that the code has plenty of room to display. for example:

```html
<h1>This code block is luxuriously wide!</h1>
```

##### Table of Contents

- Tables of contents should always be created for folders containing multiple pages, and on a "best judgement" basis for single pages with a great deal of content.
- When creating a TOC for a single page, you will need to use `<a>` tags with `name` attributes next to the section's title to specify your anchors.
  - You can use a descriptive name if you would like, or simply a number. e.g. The "Style Guide" heading above is defined as:
  - `## <a name="1">Style Guide`
- It is also a good practice to include a "back to top" link in each section, where "top" is a named anchor attached to the page's title.

[Back to Top](#top)
