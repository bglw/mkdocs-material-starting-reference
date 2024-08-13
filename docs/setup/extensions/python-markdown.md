# Python Markdown

Material for MkDocs supports a large number of [Python Markdown] extensions,
which is part of what makes it so attractive for technical writing. Following
is a list of all supported extensions, linking to the relevant sections of the
reference for which features they need to be enabled.

[python markdown]: https://python-markdown.github.io/

## Supported extensions

### Abbreviations

[:octicons-tag-24: 1.0.0][abbreviations support] ·
[:octicons-workflow-24: Extension][abbreviations]

The [Abbreviations] extension adds the ability to add a small tooltip to an
element, by wrapping it with an `abbr` tag. Only plain text (no markup) is
supported. Enable it via `mkdocs.yml`:

```yaml
markdown_extensions:
  - abbr
```

No configuration options are available. See reference for usage:

- [Adding abbreviations]
- [Adding a glossary]

  [abbreviations]: https://python-markdown.github.io/extensions/abbreviations/
  [abbreviations support]: https://github.com/squidfunk/mkdocs-material/releases/tag/1.0.0
  [adding abbreviations]: ../../reference/tooltips.md#adding-abbreviations
  [adding a glossary]: ../../reference/tooltips.md#adding-a-glossary

### Admonition

[:octicons-tag-24: 0.1.0][admonition support] ·
[:octicons-workflow-24: Extension][admonition]

The [Admonition] extension adds support for admonitions, more commonly known as
_call-outs_, which can be defined in Markdown by using a simple syntax. Enable
it via `mkdocs.yml`:

```yaml
markdown_extensions:
  - admonition
```

No configuration options are available. See reference for usage:

- [Adding admonitions]
- [Changing the title]
- [Removing the title]
- [Supported types]

  [admonition]: https://python-markdown.github.io/extensions/admonition/
  [admonition support]: https://github.com/squidfunk/mkdocs-material/releases/tag/0.1.0
  [adding admonitions]: ../../reference/admonitions.md#usage
  [changing the title]: ../../reference/admonitions.md#changing-the-title
  [removing the title]: ../../reference/admonitions.md#removing-the-title
  [supported types]: ../../reference/admonitions.md#supported-types

### Attribute Lists

[:octicons-tag-24: 0.1.0][attribute lists support] ·
[:octicons-workflow-24: Extension][attribute lists]

The [Attribute Lists] extension allows to add HTML attributes and CSS classes
to [almost every][attribute lists limitations] Markdown inline- and block-level
element with a special syntax. Enable it via `mkdocs.yml`:

```yaml
markdown_extensions:
  - attr_list
```

No configuration options are available. See reference for usage:

- [Using grids]
- [Adding buttons]
- [Adding tooltips]
- [Using icons with colors]
- [Using icons with animations]
- [Image alignment]
- [Image lazy-loading]

  [attribute lists]: https://python-markdown.github.io/extensions/attr_list/
  [attribute lists support]: https://github.com/squidfunk/mkdocs-material/releases/tag/0.1.0
  [attribute lists limitations]: https://python-markdown.github.io/extensions/attr_list/#limitations
  [adding buttons]: ../../reference/buttons.md#adding-buttons
  [adding tooltips]: ../../reference/tooltips.md#adding-tooltips
  [using icons with colors]: ../../reference/icons-emojis.md#with-colors
  [using icons with animations]: ../../reference/icons-emojis.md#with-animations
  [image alignment]: ../../reference/images.md#image-alignment
  [image lazy-loading]: ../../reference/images.md#image-lazy-loading

### Definition Lists

[:octicons-tag-24: 1.1.0][definition lists support] ·
[:octicons-workflow-24: Extension][definition lists]

The [Definition Lists] extension adds the ability to add definition lists (more
commonly known as [description lists] – `dl` in HTML) via Markdown to a
document. Enable it via `mkdocs.yml`:

```yaml
markdown_extensions:
  - def_list
```

No configuration options are available. See reference for usage:

- [Using definition lists]

  [definition lists]: https://python-markdown.github.io/extensions/definition_lists/
  [definition lists support]: https://github.com/squidfunk/mkdocs-material/releases/tag/1.1.0
  [description lists]: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/dl
  [using definition lists]: ../../reference/lists.md#using-definition-lists

### Footnotes

[:octicons-tag-24: 1.0.0][footnotes support] ·
[:octicons-workflow-24: Extension][footnotes]

The [Footnotes] extension allows to define inline footnotes, which are then
rendered below all Markdown content of a document. Enable it via `mkdocs.yml`:

```yaml
markdown_extensions:
  - footnotes
```

No configuration options are supported. See reference for usage:

- [Adding footnote references]
- [Adding footnote content]

  [footnotes]: https://python-markdown.github.io/extensions/footnotes/
  [footnotes support]: https://github.com/squidfunk/mkdocs-material/releases/tag/1.0.0
  [adding footnote references]: ../../reference/footnotes.md#adding-footnote-references
  [adding footnote content]: ../../reference/footnotes.md#adding-footnote-content

### Markdown in HTML

[:octicons-tag-24: 0.1.0][markdown in html support] ·
[:octicons-workflow-24: Extension][markdown in html]

The [Markdown in HTML] extension allows for writing Markdown inside of HTML,
which is useful for wrapping Markdown content with custom elements. Enable it
via `mkdocs.yml`:

```yaml
markdown_extensions:
  - md_in_html
```

> By default, Markdown ignores any content within a raw HTML block-level
> element. With the `md_in_html` extension enabled, the content of a raw HTML
> block-level element can be parsed as Markdown by including a `markdown`
> attribute on the opening tag. The `markdown` attribute will be stripped from
> the output, while all other attributes will be preserved.

No configuration options are available. See reference for usage:

- [Image captions]

  [markdown in html]: https://python-markdown.github.io/extensions/md_in_html/
  [markdown in html support]: https://github.com/squidfunk/mkdocs-material/releases/tag/0.1.0
  [image captions]: ../../reference/images.md#image-captions

### Table of Contents

[:octicons-tag-24: 0.1.0][table of contents support] ·
[:octicons-workflow-24: Extension][table of contents]

The [Table of Contents] extension automatically generates a table of contents
from a document, which Material for MkDocs will render as part of the resulting
page. Enable it via `mkdocs.yml`:

```yaml
markdown_extensions:
  - toc:
      permalink: true
```

The following configuration options are supported:

[`title`](#+toc.title){ #+toc.title }

: [:octicons-tag-24: 7.3.5][title support] ·
:octicons-milestone-24: Default: _automatically set_ – This option sets the
title of the table of contents in the right navigation sidebar, which is
normally automatically sourced from the translations for the [site language]
as set in `mkdocs.yml`:

    ``` yaml
    markdown_extensions:
      - toc:
          title: On this page
    ```

[`permalink`](#+toc.permalink){ #+toc.permalink }

: :octicons-milestone-24: Default: `false` – This option adds an anchor link
containing the paragraph symbol `¶` or another custom symbol at the end of
each headline, exactly like on the page you're currently viewing, which
Material for MkDocs will make appear on hover:

    === "¶"

        ``` yaml
        markdown_extensions:
          - toc:
              permalink: true
        ```

    === "⚓︎"

        ``` yaml
        markdown_extensions:
          - toc:
              permalink: ⚓︎
        ```

[`permalink_title`](#+toc.permalink_title){ #+toc.permalink_title }

: :octicons-milestone-24: Default: `Permanent link` – This option sets the
title of the anchor link which is shown on hover and read by screen readers.
For accessibility reasons, it might be beneficial to change it to a more
discernable name, stating that the anchor links to the section itself:

    ``` yaml
    markdown_extensions:
      - toc:
          permalink_title: Anchor link to this section for reference
    ```

[`slugify`](#+toc.slugify){ #+toc.slugify }

: :octicons-milestone-24: Default: `headerid.slugify` – This option allows for
customization of the slug function. For some languages, the default may not
produce good and readable identifiers – consider using another slug function
like for example those from [Python Markdown Extensions][slugs]:

    === "Unicode"

        ``` yaml
        markdown_extensions:
          - toc:
              slugify: !!python/object/apply:pymdownx.slugs.slugify
                kwds:
                  case: lower
        ```

    === "Unicode, case-sensitive"

        ``` yaml
        markdown_extensions:
          - toc:
              slugify: !!python/object/apply:pymdownx.slugs.slugify
        ```

[`toc_depth`](#+toc.toc_depth){ #+toc.toc_depth }

: :octicons-milestone-24: Default: `6` – Define the range of levels to be
included in the table of contents. This may be useful for project
documentation with deeply structured headings to decrease the length of the
table of contents, or to remove the table of contents altogether:

    === "Hide levels 4-6"

        ``` yaml
        markdown_extensions:
          - toc:
              toc_depth: 3
        ```

    === "Hide table of contents"

        ``` yaml
        markdown_extensions:
          - toc:
              toc_depth: 0
        ```

The other configuration options of this extension are not officially supported
by Material for MkDocs, which is why they may yield unexpected results. Use
them at your own risk.

[table of contents]: https://python-markdown.github.io/extensions/toc/
[table of contents support]: https://github.com/squidfunk/mkdocs-material/releases/tag/0.1.0
[title support]: https://github.com/squidfunk/mkdocs-material/releases/tag/7.3.5
[site language]: ../changing-the-language.md#site-language
[slugs]: https://facelessuser.github.io/pymdown-extensions/extras/slugs/

### Tables

[:octicons-tag-24: 0.1.0][tables support] ·
[:octicons-workflow-24: Extension][tables]

The [Tables] extension adds the ability to create tables in Markdown by using a
simple syntax. Enable it via `mkdocs.yml` (albeit it should be enabled by
default):

```yaml
markdown_extensions:
  - tables
```

No configuration options are available. See reference for usage:

- [Using data tables]
- [Column alignment]

  [tables]: https://python-markdown.github.io/extensions/tables/
  [tables support]: https://github.com/squidfunk/mkdocs-material/releases/tag/0.1.0
  [using data tables]: ../../reference/data-tables.md#usage
  [column alignment]: ../../reference/data-tables.md#column-alignment
