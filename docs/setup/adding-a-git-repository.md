# Adding a git repository

If your documentation is related to source code, Material for MkDocs provides
the ability to display information to the project's repository as part of the
static site, including stars and forks. Furthermore, the
[date of last update and creation], as well as [contributors] can be shown.

## Configuration

### Repository

[:octicons-tag-24: 0.1.0][repository support] ·
:octicons-milestone-24: Default: _none_

In order to display a link to the repository of your project as part of your
documentation, set [`repo_url`][repo_url] in `mkdocs.yml` to the public URL of
your repository, e.g.:

```yaml
repo_url: https://github.com/squidfunk/mkdocs-material
```

The link to the repository will be rendered next to the search bar on big
screens and as part of the main navigation drawer on smaller screen sizes.
Additionally, for public repositories hosted on [GitHub] or [GitLab], the
number of stars and forks is automatically requested and rendered.

GitHub repositories also include the tag of the latest release.[^1]

[^1]:
    Unfortunately, GitHub only provides an API endpoint to obtain the [latest
    release] - not the latest tag. Thus, make sure to [create a release] (not
    pre-release) for the latest tag you want to display next to the number of
    stars and forks.

[repository support]: https://github.com/squidfunk/mkdocs-material/releases/tag/0.1.0
[repo_url]: https://www.mkdocs.org/user-guide/configuration/#repo_url
[latest release]: https://docs.github.com/en/rest/reference/releases#get-the-latest-release
[create a release]: https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository#creating-a-release

#### Repository name

[:octicons-tag-24: 0.1.0][repository name support] ·
:octicons-milestone-24: Default: _automatically set to_ `GitHub`, `GitLab` _or_
`Bitbucket`

MkDocs will infer the source provider by examining the URL and try to set the
_repository name_ automatically. If you wish to customize the name, set
[`repo_name`][repo_name] in `mkdocs.yml`:

```yaml
repo_name: squidfunk/mkdocs-material
```

[repository name support]: https://github.com/squidfunk/mkdocs-material/releases/tag/0.1.0
[repo_name]: https://www.mkdocs.org/user-guide/configuration/#repo_name

#### Repository icon

[:octicons-tag-24: 5.0.0][repository icon support] ·
:octicons-milestone-24: Default:
:fontawesome-brands-git-alt: – `fontawesome/brands/git-alt`

While the default repository icon is a generic git icon, it can be set to
any icon bundled with the theme by referencing a valid icon path in
`mkdocs.yml`:

```yaml
theme:
  icon:
    repo: fontawesome/brands/git-alt # (1)!
```

1.  Enter a few keywords to find the perfect icon using our [icon search] and
    click on the shortcode to copy it to your clipboard:

    <div class="mdx-iconsearch" data-mdx-component="iconsearch">
      <input class="md-input md-input--stretch mdx-iconsearch__input" placeholder="Search icon" data-mdx-component="iconsearch-query" value="git" />
      <div class="mdx-iconsearch-result" data-mdx-component="iconsearch-result" data-mdx-mode="file">
        <div class="mdx-iconsearch-result__meta"></div>
        <ol class="mdx-iconsearch-result__list"></ol>
      </div>
    </div>

Some popular choices:

- :fontawesome-brands-git: – `fontawesome/brands/git`
- :fontawesome-brands-git-alt: – `fontawesome/brands/git-alt`
- :fontawesome-brands-github: – `fontawesome/brands/github`
- :fontawesome-brands-github-alt: – `fontawesome/brands/github-alt`
- :fontawesome-brands-gitlab: – `fontawesome/brands/gitlab`
- :fontawesome-brands-gitkraken: – `fontawesome/brands/gitkraken`
- :fontawesome-brands-bitbucket: – `fontawesome/brands/bitbucket`
- :fontawesome-solid-trash: – `fontawesome/solid/trash`

  [repository icon support]: https://github.com/squidfunk/mkdocs-material/releases/tag/5.0.0
  [repository icon default]: https://github.com/squidfunk/mkdocs-material/blob/master/material/.icons/fontawesome/brands/git-alt.svg
  [icon search]: ../reference/icons-emojis.md#search

#### Code actions

[:octicons-tag-24: 9.0.0][code actions support] ·
:octicons-unlock-24: Feature flag

If the [repository URL] points to a valid [GitHub], [GitLab] or [Bitbucket]
repository, [MkDocs] provides a setting called [`edit_uri`][edit_uri], which
resolves to the subfolder where your documentation is hosted.

If your default branch is called `main`, change the setting to:

```yaml
edit_uri: edit/main/docs/
```

After making sure that `edit_uri` is correctly configured, buttons for code
actions can be added. Two types of code actions are supported: `edit` and `view`
(GitHub only):

=== ":material-file-edit-outline: Edit this page"

    ``` yaml
    theme:
      features:
        - content.action.edit
    ```

=== ":material-file-eye-outline: View source of this page"

    ``` yaml
    theme:
      features:
        - content.action.view
    ```

The icon of the edit and view buttons can be changed with the following lines:

```yaml
theme:
  icon:
    edit: material/pencil # (1)!
    view: material/eye
```

1.  Enter a few keywords to find the perfect icon using our [icon search] and
    click on the shortcode to copy it to your clipboard:

    <div class="mdx-iconsearch" data-mdx-component="iconsearch">
      <input class="md-input md-input--stretch mdx-iconsearch__input" placeholder="Search icon" data-mdx-component="iconsearch-query" value="material pencil" />
      <div class="mdx-iconsearch-result" data-mdx-component="iconsearch-result" data-mdx-mode="file">
        <div class="mdx-iconsearch-result__meta"></div>
        <ol class="mdx-iconsearch-result__list"></ol>
      </div>
    </div>

[code actions support]: https://github.com/squidfunk/mkdocs-material/releases/tag/9.0.0
[repository url]: #repository
[github]: https://github.com/
[gitlab]: https://about.gitlab.com/
[bitbucket]: https://bitbucket.org/
[mkdocs]: https://www.mkdocs.org
[edit_uri]: https://www.mkdocs.org/user-guide/configuration/#edit_uri

### Revisioning

The following plugins are fully integrated with Material for MkDocs, allowing
for showing the [date of last update and creation] of a document, as well as
links to all [contributors] or [authors] involved.

[date of last update and creation]: #document-dates
[contributors]: #document-contributors
[authors]: #document-authors

#### Document dates

[:octicons-tag-24: 4.6.0][document dates support] ·
[:octicons-cpu-24: Plugin][git-revision-date-localized]

The [git-revision-date-localized] plugin adds support for adding the date of
last update and creation of a document at the bottom of each page. Install it
with `pip`:

```
pip install mkdocs-git-revision-date-localized-plugin
```

Then, add the following lines to `mkdocs.yml`:

```yaml
plugins:
  - git-revision-date-localized:
      enable_creation_date: true
```

The following configuration options are supported:

[`enabled`](#+git-revision-date-localized.enabled){ #+git-revision-date-localized.enabled }

: :octicons-milestone-24: Default: `true` – This option specifies whether
the plugin is enabled when building your project. If you want to switch
the plugin off, e.g. for local builds, use an [environment variable]:

    ``` yaml
    plugins:
      - git-revision-date-localized:
          enabled: !ENV [CI, false]
    ```

[`type`](#+git-revision-date-localized.type){ #+git-revision-date-localized.type }

: :octicons-milestone-24: Default: `date` – The format of the date to be
displayed. Valid values are `date`, `datetime`, `iso_date`, `iso_datetime`
and `timeago`:

    ``` yaml
    plugins:
      - git-revision-date-localized:
          type: date
    ```

[`enable_creation_date`](#+git-revision-date-localized.enable_creation_date){ #+git-revision-date-localized.enable_creation_date }

: :octicons-milestone-24: Default: `false` – Enables the display of the
creation date of the file associated with the page next to the last updated
date at the bottom of the page:

    ``` yaml
    plugins:
      - git-revision-date-localized:
          enable_creation_date: true
    ```

[`fallback_to_build_date`](#+git-revision-date-localized.fallback_to_build_date){ #+git-revision-date-localized.fallback_to_build_date }

: :octicons-milestone-24: Default: `false` – Enables falling back to
the time when `mkdocs build` was executed. Can be used as a fallback when
the build is performed outside of a git repository:

    ``` yaml
    plugins:
      - git-revision-date-localized:
          fallback_to_build_date: true
    ```

The other configuration options of this extension are not officially supported
by Material for MkDocs, which is why they may yield unexpected results. Use
them at your own risk.

[document dates support]: https://github.com/squidfunk/mkdocs-material/releases/tag/4.6.0
[git-revision-date-localized]: https://github.com/timvink/mkdocs-git-revision-date-localized-plugin
