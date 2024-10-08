# Reference

Material for MkDocs is packed with many great features that make technical
writing a joyful activity. This section of the documentation explains how to set up
a page, and showcases all available specimen that can be used directly from
within Markdown files.

## Usage

### Setting the page `title`

Each page has a designated title, which is used in the navigation sidebar, for
[social cards] and in other places. While MkDocs attempts to automatically
determine the title of a page in a [four step process], the title can also be
explicitly set with the front matter `title` property:

```yaml
---
title: Lorem ipsum dolor sit amet # (1)!
---
# Document title
```

1.  This line sets the [`title`][title] inside the HTML document's
    [`head`][head] for the generated page to the given value. Note that the
    site title, which is set via [`site_name`][site_name], is appended with a
    dash.

[social cards]: ../setup/setting-up-social-cards.md
[four step process]: https://www.mkdocs.org/user-guide/writing-your-docs/#meta-data
[title]: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/title
[head]: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/head
[site_name]: https://www.mkdocs.org/user-guide/configuration/#site_name

### Setting the page `description`

A Markdown file can include a description that is added to the `meta` tags of
a page, and is also used for [social cards]. It's a good idea to set a
[`site_description`][site_description] in `mkdocs.yml` as a fallback value if
the author does not explicitly define a description for a Markdown file:

```yaml
---
description: Nullam urna elit, malesuada eget finibus ut, ac tortor. # (1)!
---
# Document title
```

1.  This line sets the `meta` tag containing the description inside the
    document `head` for the current page to the provided value.

[site_description]: https://www.mkdocs.org/user-guide/configuration/#site_description

### Setting the page `template`

If you're using [theme extension] and created a new page template in the
`overrides` directory, you can enable it for a specific page. Add the following
lines at the top of a Markdown file:

```yaml
---
template: custom.html
---
# Document title
```

??? question "How to set a page template for an entire folder?"

    With the help of the [built-in meta plugin], you can set a custom template
    for an entire section and all nested pages, by creating a `.meta.yml` file
    in the corresponding folder with the following content:

    ``` yaml
    template: custom.html
    ```

[theme extension]: ../customization.md#extending-the-theme
[built-in meta plugin]: #built-in-meta-plugin

## Customization

### Using metadata in templates

#### :material-check-all: on all pages

In order to add custom `meta` tags to your document, you can [extend the theme
][theme extension] and [override the `extrahead` block][overriding blocks],
e.g. to add indexing policies for search engines via the `robots` property:

```html
{% extends "base.html" %} {% block extrahead %}
<meta name="robots" content="noindex, nofollow" />
{% endblock %}
```

[overriding blocks]: ../customization.md#overriding-blocks

#### :material-check: on a single page

If you want to set a `meta` tag on a single page, or want to set different
values for different pages, you can use the `page.meta` object inside your
template override, e.g.:

```html
{% extends "base.html" %} {% block extrahead %} {% if page and page.meta and
page.meta.robots %}
<meta name="robots" content="{{ page.meta.robots }}" />
{% else %}
<meta name="robots" content="index, follow" />
{% endif %} {% endblock %}
```

You can now use `robots` exactly like [`title`][title] and
[`description`][description] to set values. Note that in this case, the
template defines an `else` branch, which would set a default if none was given.

[title]: #setting-the-page-title
[description]: #setting-the-page-description
