# Setting up navigation

A clear and concise navigation structure is an important aspect of good project
documentation. Material for MkDocs provides a multitude of options to configure
the behavior of navigational elements, including [tabs] and [sections], and one
of its flagship features: [instant loading].

[tabs]: #navigation-tabs
[sections]: #navigation-sections
[instant loading]: #instant-loading

## Configuration

### Instant loading

[:octicons-tag-24: 5.0.0][instant loading support] ·
:octicons-unlock-24: Feature flag

When instant loading is enabled, clicks on all internal links will be
intercepted and dispatched via [XHR] without fully reloading the page. Add
the following lines to `mkdocs.yml`:

```yaml
theme:
  features:
    - navigation.instant
```

The resulting page is parsed and injected and all event handlers and components
are rebound automatically, i.e., **Material for MkDocs now behaves like a Single
Page Application**. Now, the search index survives navigation, which is
especially useful for large documentation sites.

[instant loading support]: https://github.com/squidfunk/mkdocs-material/releases/tag/5.0.0
[xhr]: https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest

### Anchor tracking

[:octicons-tag-24: 8.0.0][anchor tracking support] ·
:octicons-unlock-24: Feature flag

When anchor tracking is enabled, the URL in the address bar is automatically
updated with the active anchor as highlighted in the table of contents. Add the
following lines to `mkdocs.yml`:

```yaml
theme:
  features:
    - navigation.tracking
```

[anchor tracking support]: https://github.com/squidfunk/mkdocs-material/releases/tag/8.0.0

### Navigation tabs

[:octicons-tag-24: 1.1.0][navigation tabs support] ·
:octicons-unlock-24: Feature flag

When tabs are enabled, top-level sections are rendered in a menu layer below
the header for viewports above `1220px`, but remain as-is on mobile.[^1] Add
the following lines to `mkdocs.yml`:

[^1]:
    Prior to :octicons-tag-24: 6.2.0, navigation tabs had a slightly different
    behavior. All top-level pages (i.e. all top-level entries directly
    referring to a `*.md` file) defined inside the `nav` entry of `mkdocs.yml`
    were grouped under the first tab which received the title of the first page.
    This made it impossible to include a top-level page (or external link) as a
    tab item, as was reported in #1884 and #2072. From :octicons-tag-24: 6.2.0
    on, navigation tabs include all top-level pages and sections.

```yaml
theme:
  features:
    - navigation.tabs
```

=== "With tabs"

    [![Navigation tabs enabled]][Navigation tabs enabled]

=== "Without"

    [![Navigation tabs disabled]][Navigation tabs disabled]

[navigation tabs support]: https://github.com/squidfunk/mkdocs-material/releases/tag/1.1.0
[navigation tabs enabled]: ../assets/screenshots/navigation-tabs.png
[navigation tabs disabled]: ../assets/screenshots/navigation.png

#### Sticky navigation tabs

[:octicons-tag-24: 7.3.0][sticky navigation tabs support] ·
:octicons-unlock-24: Feature flag

When sticky tabs are enabled, navigation tabs will lock below the header and
always remain visible when scrolling down. Just add the following two feature
flags to `mkdocs.yml`:

```yaml
theme:
  features:
    - navigation.tabs
    - navigation.tabs.sticky
```

=== "With sticky tabs"

    [![Sticky navigation tabs enabled]][Sticky navigation tabs enabled]

=== "Without"

    [![Sticky navigation tabs disabled]][Sticky navigation tabs disabled]

[sticky navigation tabs support]: https://github.com/squidfunk/mkdocs-material/releases/tag/7.3.0
[sticky navigation tabs enabled]: ../assets/screenshots/navigation-tabs-sticky.png
[sticky navigation tabs disabled]: ../assets/screenshots/navigation-tabs-collapsed.png

### Navigation sections

[:octicons-tag-24: 6.2.0][navigation sections support] ·
:octicons-unlock-24: Feature flag

When sections are enabled, top-level sections are rendered as groups in the
sidebar for viewports above `1220px`, but remain as-is on mobile. Add the
following lines to `mkdocs.yml`:

```yaml
theme:
  features:
    - navigation.sections
```

=== "With sections"

    [![Navigation sections enabled]][Navigation sections enabled]

=== "Without"

    [![Navigation sections disabled]][Navigation sections disabled]

[navigation sections support]: https://github.com/squidfunk/mkdocs-material/releases/tag/6.2.0
[navigation sections enabled]: ../assets/screenshots/navigation-sections.png
[navigation sections disabled]: ../assets/screenshots/navigation.png

Both feature flags, [`navigation.tabs`][tabs] and
[`navigation.sections`][sections], can be combined with each other. If both
feature flags are enabled, sections are rendered for level 2 navigation items.

### Navigation expansion

[:octicons-tag-24: 6.2.0][navigation expansion support] ·
:octicons-unlock-24: Feature flag

When expansion is enabled, the left sidebar will expand all collapsible
subsections by default, so the user doesn't have to open subsections manually.
Add the following lines to `mkdocs.yml`:

```yaml
theme:
  features:
    - navigation.expand
```

=== "With expansion"

    [![Navigation expansion enabled]][Navigation expansion enabled]

=== "Without"

    [![Navigation expansion disabled]][Navigation expansion disabled]

[navigation expansion support]: https://github.com/squidfunk/mkdocs-material/releases/tag/6.2.0
[navigation expansion enabled]: ../assets/screenshots/navigation-expand.png
[navigation expansion disabled]: ../assets/screenshots/navigation.png

### Section index pages

[:octicons-tag-24: 7.3.0][section index pages support] ·
:octicons-unlock-24: Feature flag

When section index pages are enabled, documents can be directly attached to
sections, which is particularly useful for providing overview pages. Add the
following lines to `mkdocs.yml`:

```yaml
theme:
  features:
    - navigation.indexes # (1)!
```

1.  This feature flag is not compatible with [`toc.integrate`][toc.integrate],
    as sections cannot host the table of contents due to missing space.

=== "With section index pages"

    [![Section index pages enabled]][Section index pages enabled]

=== "Without"

    [![Section index pages disabled]][Section index pages disabled]

In order to link a page to a section, create a new document with the name
`index.md` in the respective folder, and add it to the beginning of your
navigation section:

```yaml
nav:
  - Section:
    - section/index.md # (1)!
    - Page 1: section/page-1.md
    ...
    - Page n: section/page-n.md
```

1.  MkDocs also considers files called `README.md` as [index pages].

[section index pages support]: https://github.com/squidfunk/mkdocs-material/releases/tag/7.3.0
[section index pages enabled]: ../assets/screenshots/navigation-index-on.png
[section index pages disabled]: ../assets/screenshots/navigation-index-off.png
[toc.integrate]: #navigation-integration
[index pages]: https://www.mkdocs.org/user-guide/writing-your-docs/#index-pages

### Table of contents

#### Anchor following

[:octicons-tag-24: 8.5.0][anchor following support] ·
:octicons-beaker-24: Experimental

When anchor following for the [table of contents] is enabled, the sidebar is
automatically scrolled so that the active anchor is always visible. Add the
following lines to `mkdocs.yml`:

```yaml
theme:
  features:
    - toc.follow
```

[anchor following support]: https://github.com/squidfunk/mkdocs-material/releases/tag/8.5.0

#### Navigation integration

[:octicons-tag-24: 6.2.0][navigation integration support] ·
:octicons-unlock-24: Feature flag

When navigation integration for the [table of contents] is enabled, it is always
rendered as part of the navigation sidebar on the left. Add the following lines
to `mkdocs.yml`:

```yaml
theme:
  features:
    - toc.integrate # (1)!
```

1.  This feature flag is not compatible with
    [`navigation.indexes`][navigation.indexes], as sections cannot host the
    table of contents due to missing space.

=== "With navigation integration"

    [![Navigation integration enabled]][Navigation integration enabled]

=== "Without"

    [![Navigation integration disabled]][Navigation integration disabled]

[table of contents]: extensions/python-markdown.md#table-of-contents
[navigation integration support]: https://github.com/squidfunk/mkdocs-material/releases/tag/7.3.0
[navigation integration enabled]: ../assets/screenshots/toc-integrate.png
[navigation integration disabled]: ../assets/screenshots/navigation-tabs.png
[navigation.indexes]: #section-index-pages

### Back-to-top button

[:octicons-tag-24: 7.1.0][back-to-top button support] ·
:octicons-unlock-24: Feature flag

A back-to-top button can be shown when the user, after scrolling down, starts
to scroll up again. It's rendered centered and just below the header. Add the
following lines to `mkdocs.yml`:

```yaml
theme:
  features:
    - navigation.top
```

[back-to-top button support]: https://github.com/squidfunk/mkdocs-material/releases/tag/7.1.0

## Usage

### Hiding the sidebars

The navigation and/or table of contents sidebars can be hidden for a document
with the front matter `hide` property. Add the following lines at the top of a
Markdown file:

```yaml
---
hide:
  - navigation
  - toc
---
# Document title
```

=== "Hide navigation"

    [![Hide navigation enabled]][Hide navigation enabled]

=== "Hide table of contents"

    [![Hide table of contents enabled]][Hide table of contents enabled]

=== "Hide both"

    [![Hide both enabled]][Hide both enabled]

[hide navigation enabled]: ../assets/screenshots/hide-navigation.png
[hide table of contents enabled]: ../assets/screenshots/hide-toc.png
[hide both enabled]: ../assets/screenshots/hide-navigation-toc.png

### Hiding the navigation path

While the [navigation path] is rendered above the main headline, sometimes, it
might be desirable to hide it for a specific page, which can be achieved with
the front matter `hide` property:

```yaml
---
hide:
  - path
---
# Document title
```

[navigation path]: #navigation-path

## Customization

### Keyboard shortcuts

Material for MkDocs includes several keyboard shortcuts that make it possible
to navigate your project documentation via keyboard. There are two modes:

[`search`](#mode:search){ #mode:search }

: This mode is active when the _search is focused_. It provides several key
bindings to make search accessible and navigable via keyboard:

    * ++arrow-down++ , ++arrow-up++ : select next / previous result
    * ++esc++ , ++tab++ : close search dialog
    * ++enter++ : follow selected result

[`global`](#mode:global){ #mode:global }

: This mode is active when _search is not focussed_ and when there's no other
focussed element that is susceptible to keyboard input. The following keys
are bound:

    * ++f++ , ++s++ , ++slash++ : open search dialog
    * ++p++ , ++comma++ : go to previous page
    * ++n++ , ++period++ : go to next page

Let's say you want to bind some action to the ++x++ key. By using [additional
JavaScript], you can subscribe to the `keyboard$` observable and attach
your custom event listener:

=== ":octicons-file-code-16: `docs/javascripts/shortcuts.js`"

    ``` js
    keyboard$.subscribe(function(key) {
      if (key.mode === "global" && key.type === "x") {
        /* Add custom keyboard handler here */
        key.claim() // (1)!
      }
    })
    ```

    1.  The call to `key.claim()` will execute `preventDefault()` on the
        underlying event, so the keypress will not propagate further and
        touch other event listeners.

=== ":octicons-file-code-16: `mkdocs.yml`"

    ``` yaml
    extra_javascript:
      - javascripts/shortcuts.js
    ```

[additional javascript]: ../customization.md#additional-javascript

### Content area width

The width of the content area is set so the length of each line doesn't exceed
80-100 characters, depending on the width of the characters. While this
is a reasonable default, as longer lines tend to be harder to read, it may be
desirable to increase the overall width of the content area, or even make it
stretch to the entire available space.

This can easily be achieved with an [additional style sheet] and a few lines
of CSS:

=== ":octicons-file-code-16: `docs/stylesheets/extra.css`"

    ``` css
    .md-grid {
      max-width: 1440px; /* (1)! */
    }
    ```

    1.  If you want the content area to always stretch to the available screen
        space, reset `max-width` with the following CSS:

        ``` css
        .md-grid {
          max-width: initial;
        }
        ```

=== ":octicons-file-code-16: `mkdocs.yml`"

    ``` yaml
    extra_css:
      - stylesheets/extra.css
    ```

[additional style sheet]: ../customization.md#additional-css
