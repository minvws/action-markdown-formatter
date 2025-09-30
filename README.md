# Markdown Autoformatter GitHub Action

This GitHub Action automatically formats Markdown files in your repository using
Prettier. It ensures that your Markdown files adhere to a consistent style,
making them easier to read and maintain.

## Usage

To use the action, add it to a workflow in your repository, that triggers on
pull requests affecting Markdown files. Below is an example workflow
configuration:

```yaml
name: Format Markdown
on:
  pull_request:
    paths:
      - "**/*.md"

jobs:
  format-markdown:
    runs-on: ubuntu-latest
    permissions:
      contents: write
      pull-requests: write
    steps:
      - uses: minvws/action-markdown-formatter@v1
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
```

This workflow will run the action whenever a pull request is opened or updated
that includes changes to Markdown files. The action will format the files and
commit the changes back to the pull request. Note that it will commit each
individual file separately, which may result in multiple commits if multiple
files are changed.

## Configuration

You can customize the default behavior of the action by providing a prettier
configuration file (e.g., `.prettierrc`, `.prettierrc.json`, etc.) in the root
of your repository. For more information on Prettier configuration options,
please refer to the
[Prettier documentation](https://prettier.io/docs/configuration).

## Contribution

If you plan to make non-trivial changes, we recommend to open an issue
beforehand where we can discuss your planned changes. This increases the chance
that we might be able to use your contribution (or it avoids doing work if there
are reasons why we wouldn't be able to use it).

Git commits must be signed. Please check the
[Signing commits documentation on GitHub](https://docs.github.com/en/github/authenticating-to-github/signing-commits).

## License

This repository is released under the EUPL 1.2 license.
[See LICENSE.txt](./LICENSE.txt) for details.

## Part of iCore

This package is part of the iCore project.
