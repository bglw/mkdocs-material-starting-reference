---
status: new
---

# Setting up social cards

Material for MkDocs can automatically create beautiful social cards for your
documentation, which appear as link previews on social media platforms. You
can select from several [pre-designed layouts][default layouts] or create
[custom layouts] to match your unique style and branding.

<figure markdown>

[![Layout default variant]][layout default variant]

  <figcaption markdown>

Social card of our [formatting] reference

  </figcaption>
</figure>

[custom layouts]: #customization
[formatting]: ../reference/formatting.md

## Configuration

### Built-in social plugin

[:octicons-tag-24: 8.5.0][social cards support] ·
:octicons-cpu-24: Plugin ·
:octicons-beaker-24: Experimental

The built-in social plugin automatically generate a custom preview image for
each page. Install all dependencies for image processing[^1] and add the
following lines to `mkdocs.yml`:

[^1]:
    The awesome thing about social cards is that they are generated during
    build time and directly distributed with your documentation, no external
    services involved. While it would technically be simpler to generate
    social cards using a web browser and an automation framework like
    [Puppeteer], it would add further liabilities to the toolchain, with the
    potential to make build pipelines more complex and resource intense.

    For this reason, Material for MkDocs again follows its core principle of
    making it as simple and powerful as possible, providing an easy-to-use
    framework for building [custom layouts] using Python image processing
    libraries.

```yaml
plugins:
  - social
```

The following configuration options are available:

[`enabled`](#+social.enabled){ #+social.enabled }

: :octicons-milestone-24: Default: `true` – This option specifies whether
the plugin is enabled when building your project. If you want to speed up
local builds, you can use an [environment variable]:

    ``` yaml
    plugins:
      - social:
          enabled: !ENV [CI, false]
    ```

[social cards support]: https://github.com/squidfunk/mkdocs-material/releases/tag/8.5.0
[puppeteer]: https://github.com/puppeteer/puppeteer
[environment variable]: https://www.mkdocs.org/user-guide/configuration/#environment-variables

#### Social cards

The following configuration options are available for card generation:

[`cards`](#+social.cards){ #+social.cards }

: :octicons-milestone-24: Default: `true` – This option specifies whether
to generate social card images. If you want to switch the plugin off, e.g.
for local builds, you can use an [environment variable]:

    ``` yaml
    plugins:
      - social:
          cards: !ENV [CI, false]
    ```

[`cards_dir`](#+social.cards_dir){ #+social.cards_dir }

: :octicons-milestone-24: Default: `assets/images/social` – This option
specifies where the generated social cards will be stored. While it's
usually not necessary to change this option, change it with:

    ``` yaml
    plugins:
      - social:
          cards_dir: assets/images/social
    ```

[`cards_layout_options`](#+social.cards_layout_options){ #+social.cards_layout_options }

: [:octicons-tag-24: 9.1.10][layout options support] · :octicons-milestone-24:
Default: _none_ – This option allows to set [parameters] as provided by
the layout specification. For [custom layouts], this key can be used to
provide layout-specific options, making layouts entirely configurable.

    ---

    All [`default`][default layouts] layouts expose the following parameters:

    [`background_color`](#+social.cards_layout_options.background_color){ #+social.cards_layout_options.background_color }

    :   Set a background color, which can be a [CSS color keyword], or a 3, 4, 6
        or 8 letter HEX color code. Alpha channels are supported as well:

        ``` yaml
        plugins:
          - social:
              cards_layout_options:
                background_color: "#0FF1CE"
        ```

    [`color`](#+social.cards_layout_options.color){ #+social.cards_layout_options.color }

    :   Set a foreground color, which can be a [CSS color keyword], or a 3, 4, 6
        or 8 letter HEX color code. The color is primarily used to tint text and
        icons:

        ``` yaml
        plugins:
          - social:
              cards_layout_options:
                color: "#0FF1CE"
        ```

    [`font_family`](#+social.cards_layout_options.font_family){ #+social.cards_layout_options.font_family }

    :   Set a font family. This overrides the [font] that is set as part of the
        theme configuration. The [built-in social plugin] will automatically
        download the font from [Google Fonts]:

        ``` yaml
        plugins:
          - social:
              cards_layout_options:
                font_family: Ubuntu
        ```

[`cards_exclude`](#+privacy.cards_exclude){ #+privacy.cards_exclude }

: :octicons-milestone-24: Default: _none_ – This option allows to exclude
certain subsections of your documentation from generating social cards:

    ``` yaml
    plugins:
      - social:
          cards_exclude:
            - changelog/*.md
    ```

[color palette]: ./changing-the-colors.md#color-palette
[primary color]: ./changing-the-colors.md#primary-color
[accent color]: ./changing-the-colors.md#accent-color
[font]: ./changing-the-fonts.md#regular-font
[google fonts]: https://fonts.google.com/
[layout options]: #+social.cards_layout_options
[page icon]: ../reference/index.md#setting-the-page-icon
[layout default]: ../assets/screenshots/social-cards.png
[layout default variant]: ../assets/screenshots/social-cards-variant.png
[layout default accent]: ../assets/screenshots/social-cards-accent.png
[layout default invert]: ../assets/screenshots/social-cards-invert.png
[template variables]: https://www.mkdocs.org/dev-guide/themes/#template-variables
[parameters]: #parameters
[default layouts]: #+social.cards_layout
[css color keyword]: https://developer.mozilla.org/en-US/docs/Web/CSS/color_value#color_keywords
[layout options support]: https://github.com/squidfunk/mkdocs-material/releases/tag/9.1.10

## Usage

If you want to adjust the title or set a custom description for the social card,
you can set the front matter `title` and `description` properties, which take
precedence over the default values.

- [Changing the title]
- [Changing the description]

  [changing the title]: ../reference/index.md#setting-the-page-title
  [changing the description]: ../reference/index.md#setting-the-page-description

### Choosing a font

Some fonts do not contain CJK characters, like for example the
[default font, `Roboto`][font]. In case your `site_name`, `site_description`, or
page title contain CJK characters, choose another font from [Google Fonts] which
comes with CJK characters, e.g. one from the `Noto Sans` font family:

=== "Chinese (Simplified)"

    ``` yaml
    plugins:
      - social:
          cards_font: Noto Sans SC
    ```

=== "Chinese (Traditional)"

    ``` yaml
    plugins:
      - social:
          cards_font: Noto Sans TC
    ```

=== "Japanese"

    ``` yaml
    plugins:
      - social:
          cards_font: Noto Sans JP
    ```

=== "Korean"

    ``` yaml
    plugins:
      - social:
          cards_font: Noto Sans KR
    ```
