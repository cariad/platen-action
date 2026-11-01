# platen-action

A GitHub Action that presses the values in a YAML file into templates with [Platen](https://cariad.github.io/platen/).

## Usage

To press every template in your repository's `templates` directory into `build`, with the values in `values.yml`:

```yaml
jobs:
  build:
    runs-on: ubuntu-26.04
    permissions:
      contents: read

    steps:
      - uses: actions/checkout@<commit> # <release>
        with:
          persist-credentials: false

      - uses: cariad/platen-action@<commit> # <release>
        with:
          templates: templates
          values: values.yml
          output: build
```

## Inputs

| Input            | Required | Description                                                          |
| ---------------- | -------- | -----------                                                          |
| `templates`      | Yes      | The template or directory of templates to press.                     |
| `values`         | Yes      | The YAML file of values to press into the templates.                 |
| `output`         | Yes      | The file or directory to press the templates into.                   |
| `platen-version` | No       | The version of Platen to press with. Defaults to the latest release. |

## Security

Templates are code. Platen renders them with Jinja, which isn't sandboxed, so a template can run any code with the job's files, environment, and secrets.

You must press only templates that you trust, and never press a pull request's templates in a job with secrets or a token that can write.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) to set up the project.
