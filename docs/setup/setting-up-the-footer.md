# Setting up the footer

The footer of your project documentation is a great place to add links to
websites or platforms you or your company are using as additional marketing
channels, e.g. :fontawesome-brands-mastodon:{ style="color: #5A4CE0" } or
:fontawesome-brands-youtube:{ style="color: #EE0F0F" }, which you can easily
configure via `mkdocs.yml`.

## Configuration

### Navigation

[:octicons-tag-24: 9.0.0][navigation footer support] ·
:octicons-unlock-24: Feature flag

The footer can include links to the previous and next page of the current page.
If you wish to enable this behavior, add the following lines to `mkdocs.yml`:

```yaml
theme:
  features:
    - navigation.footer
```

[navigation footer support]: https://github.com/squidfunk/mkdocs-material/releases/tag/9.0.0

### Social links

[:octicons-tag-24: 1.0.0][social links support] ·
:octicons-milestone-24: Default: _none_

Social links are rendered next to the copyright notice as part of the
footer of your project documentation. Add a list of social links in `mkdocs.yml`
with:

```yaml
extra:
  social:
    - icon: fontawesome/brands/mastodon # (1)!
      link: https://fosstodon.org/@squidfunk
```

1.  Enter a few keywords to find the perfect icon using our [icon search] and
    click on the shortcode to copy it to your clipboard:

    <div class="mdx-iconsearch" data-mdx-component="iconsearch">
      <input class="md-input md-input--stretch mdx-iconsearch__input" placeholder="Search icon" data-mdx-component="iconsearch-query" value="mastodon" />
      <div class="mdx-iconsearch-result" data-mdx-component="iconsearch-result" data-mdx-mode="file">
        <div class="mdx-iconsearch-result__meta"></div>
        <ol class="mdx-iconsearch-result__list"></ol>
      </div>
    </div>

The following properties are available for each link:

[`icon`](#+social.icon){ #+social.icon }

: :octicons-milestone-24: Default: _none_ · :octicons-alert-24: **Required** –
This property must contain a valid path to any icon bundled with the theme,
or the build will not succeed. Some popular choices:

    * :fontawesome-brands-mastodon: – `fontawesome/brands/mastodon`
      <small>automatically adds [`rel=me`][rel=me]</small>
    * :fontawesome-brands-twitter: – `fontawesome/brands/twitter`
    * :fontawesome-brands-github: – `fontawesome/brands/github`
    * :fontawesome-brands-docker: – `fontawesome/brands/docker`
    * :fontawesome-brands-facebook: – `fontawesome/brands/facebook`
    * :fontawesome-brands-medium: – `fontawesome/brands/medium`
    * :fontawesome-brands-instagram: – `fontawesome/brands/instagram`
    * :fontawesome-brands-linkedin: – `fontawesome/brands/linkedin`
    * :fontawesome-brands-pied-piper-alt: – `fontawesome/brands/pied-piper-alt`
    * :fontawesome-brands-slack: – `fontawesome/brands/slack`
    * :fontawesome-brands-discord: – `fontawesome/brands/discord`

[`link`](#+social.link){ #+social.link }

: :octicons-milestone-24: Default: _none_ · :octicons-alert-24: **Required** –
This property must be set to a relative or absolute URL including the URI
scheme. All URI schemes are supported, including `mailto` and `bitcoin`:

    === ":fontawesome-brands-mastodon: Mastodon"

        ``` yaml
        extra:
          social:
            - icon: fontawesome/brands/mastodon
              link: https://fosstodon.org/@squidfunk
        ```

    === ":octicons-mail-16: Email"

        ``` yaml
        extra:
          social:
            - icon: fontawesome/solid/paper-plane
              link: mailto:<email-address>
        ```

[`name`](#+social.name){ #+social.name }

: :octicons-milestone-24: Default: _domain name from_ `link`_, if available_ –
This property is used as the link's `title` attribute and can be set to a
discernable name to improve accessibility:

    ``` yaml
    extra:
      social:
        - icon: fontawesome/brands/mastodon
          link: https://fosstodon.org/@squidfunk
          name: squidfunk on Fosstodon
    ```

[icon search]: ../reference/icons-emojis.md#search
[social links support]: https://github.com/squidfunk/mkdocs-material/releases/tag/1.0.0
[rel=me]: https://docs.joinmastodon.org/user/profile/#verification

### Copyright notice

[:octicons-tag-24: 0.1.0][copyright notice support] ·
:octicons-milestone-24: Default: _none_

A custom copyright banner can be rendered as part of the footer, which is
displayed next to the social links. It can be defined as part of `mkdocs.yml`:

```yaml
copyright: Copyright &copy; 2016 - 2020 Martin Donath
```

[copyright notice support]: https://github.com/squidfunk/mkdocs-material/releases/tag/0.1.0

### Generator notice

[:octicons-tag-24: 7.3.0][generator notice support] ·
:octicons-milestone-24: Default: `true`

The footer displays a _Made with Material for MkDocs_ notice to denote how
the site was generated. The notice can be removed with the following option
via `mkdocs.yml`:

```yaml
extra:
  generator: false
```

[generator notice support]: https://github.com/squidfunk/mkdocs-material/releases/tag/7.3.0

## Usage

### Hiding prev/next links

The footer navigation showing links to the previous and next page can be hidden
with the front matter `hide` property. Add the following lines at the top of a
Markdown file:

```yaml
---
hide:
  - footer
---
# Document title
```

## Customization

### Custom copyright

[:octicons-tag-24: 8.0.0][custom copyright support] ·
:octicons-file-symlink-file-24: Customization

In order to customize and override the [copyright notice], [extend the theme]
and [override the `copyright.html` partial][overriding partials], which normally
includes the `copyright` property set in `mkdocs.yml`.

[custom copyright support]: https://github.com/squidfunk/mkdocs-material/releases/tag/8.0.0
[copyright notice]: #copyright-notice
[generator notice]: #generator-notice
[extend the theme]: ../customization.md#extending-the-theme
[overriding partials]: ../customization.md#overriding-partials
