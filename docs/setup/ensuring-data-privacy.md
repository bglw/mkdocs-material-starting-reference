# Ensuring data privacy

Material for MkDocs makes compliance with data privacy regulations very easy,
as it offers a native [cookie consent] solution to seek explicit consent from
users before setting up [analytics]. Additionally, external assets can be
automatically downloaded for [self-hosting].

[cookie consent]: #cookie-consent
[analytics]: setting-up-site-analytics.md
[self-hosting]: #built-in-privacy-plugin

## Configuration

### Cookie consent

[:octicons-tag-24: 8.4.0][cookie consent support] ·
:octicons-milestone-24: Default: _none_ ·
:octicons-beaker-24: Experimental

Material for MkDocs ships a native and extensible cookie consent form which
asks the user for consent prior to sending requests to third parties. Add the
following to `mkdocs.yml`:

```yaml
extra:
  consent:
    title: Cookie consent
    description: >- # (1)!
      We use cookies to recognize your repeated visits and preferences, as well
      as to measure the effectiveness of our documentation and whether users
      find what they're searching for. With your consent, you're helping us to
      make our documentation better.
```

1.  You can add arbitrary HTML tags in the `description`, e.g. to link to your
    terms of service or other parts of the site.

The following properties are available:

[`title`](#+consent.title){ #+consent.title }

: :octicons-milestone-24: Default: _none_ · :octicons-alert-24: **Required** –
This property sets the title of the cookie consent, which is rendered at the
top of the form and must be set to a non-empty string.

[`description`](#+consent.description){ #+consent.description }

: :octicons-milestone-24: Default: _none_ · :octicons-alert-24: **Required** –
This property sets the description of the cookie consent, is rendered below
the title, and may include raw HTML (e.g. a links to the terms of service).

[`cookies`](#+consent.cookies){ #+consent.cookies }

: :octicons-milestone-24: Default: _none_ – This property allows to add custom
cookies or change the initial `checked` state and name of built-in cookies.
Currently, the following cookies are built-in:

    - __Google Analytics__ – `analytics` (enabled by default)
    - __GitHub__ – `github` (enabled by default)

    Each cookie must receive a unique identifier which is used as a key in the
    `cookies` map, and can be either set to a string, or to a map defining
    `name` and `checked` state:

    ===  "Custom cookie name"

        ``` yaml
        extra:
          consent:
            cookies:
              analytics: Custom name
        ```

    ===  "Custom initial state"

        ``` yaml
        extra:
          consent:
            cookies:
              analytics:
                name: Google Analytics
                checked: false
        ```

    ===  "Custom cookie"

        ``` yaml
        extra:
          consent:
            cookies:
              analytics: Google Analytics # (1)!
              custom: Custom cookie
        ```

        1.  If you define a custom cookie as part of the `cookies` property,
            the `analytics` cookie must be added back explicitly, or analytics
            won't be triggered.

    If Google Analytics was configured via `mkdocs.yml`, the cookie consent will
    automatically include a setting for the user to disable it. [Custom cookies]
    can be used from JavaScript.

[`actions`](#+consent.actions){ #+consent.actions }

: :octicons-milestone-24: Default: `[accept, manage]` – This property defines
which buttons are shown and in which order, e.g. to allow the user to accept
cookies and manage settings:

    ``` yaml
    extra:
      consent:
        actions:
          - accept
          - manage # (1)!
    ```

    1.  If the `manage` settings button is omitted from the `actions` property,
        the settings are always shown.

    The cookie consent form includes three types of buttons:

    - `accept` – Button to accept selected cookies
    - `reject` – Button to reject all cookies
    - `manage` – Button to manage settings

When a user first visits your site, a cookie consent form is rendered:

[![Cookie consent enabled]][cookie consent enabled]

[custom cookies]: #custom-cookies
[cookie consent support]: https://github.com/squidfunk/mkdocs-material/releases/tag/8.4.0
[cookie consent enabled]: ../assets/screenshots/consent.png

#### Change cookie settings

In order to comply with GDPR, users must be able to change their cookie settings
at any time. This can be done by adding a simple link to your [copyright notice]
in `mkdocs.yml`:

```yaml
copyright: >
  Copyright &copy; 2016 - 2023 Martin Donath –
  <a href="#__consent">Change cookie settings</a>
```

[copyright notice]: setting-up-the-footer.md#copyright-notice

## Customization

### Custom cookies

If you've customized the [cookie consent] and added a `custom` cookie, the user
will be prompted to accept your custom cookie. Use [additional JavaScript] to
check whether the user accepted it:

=== ":octicons-file-code-16: `docs/javascripts/consent.js`"

    ``` js
    var consent = __md_get("__consent")
    if (consent && consent.custom) {
      /* The user accepted the cookie */
    }
    ```

=== ":octicons-file-code-16: `mkdocs.yml`"

    ``` yaml
    extra_javascript:
      - javascripts/consent.js
    ```

[additional javascript]: ../customization.md#additional-javascript
