# Contributing

## Required tools

- [mise](https://mise.jdx.dev/)

## Setup

1. Clone this repository.

   ```bash
   git clone git@github.com:cariad/platen-action.git
   ```

1. Change into the repository's directory.

   ```bash
   cd platen-action
   ```

1. Install the project's tools.

   ```bash
   mise install
   ```

1. To verify the setup, run the linters and check they all pass.

   ```bash
   mise run lint
   ```

## Testing

CI's `test` job runs the action on every runner in its matrix. It presses `tests/template.txt` with `tests/values.yml` and checks the result, which shows that the action installed Platen and passed it every input.

## Bumping versions

Dependabot bumps the actions in `action.yml` and `.github/workflows/`. Bump everything else by hand:

- **Platen:** nothing to bump, because the action runs the latest release, and so does CI.
- **Python:** when Platen needs a newer Python, `python-version` in `action.yml`.
- **mise:** `min_version` in `.config/mise.toml`, and `version` in the `jdx/mise-action` step in `.github/workflows/ci.yml`.
- **Tools:** `.config/mise.toml`, then run `mise lock`.
- **Runners:** the `test` matrix and the `lint` job's `runs-on` in `.github/workflows/ci.yml`.
