# lpshipit

Helpful utility for merging launchpad MPs (only works for git repos)

## Installation

Requires Python 3.10 or newer and [uv](https://docs.astral.sh/uv/getting-started/installation/).

Install from a checkout as an isolated uv tool:

```sh
git clone https://github.com/philroche/lpshipit.git
cd lpshipit
uv tool install .
```

You can also install directly from Git:

```sh
uv tool install git+https://github.com/philroche/lpshipit.git
```

Once a release containing this packaging is published to PyPI, install it with:

```sh
uv tool install lpshipit
```

If uv's tool directory is not on your `PATH`, run `uv tool update-shell` and
restart your shell. All Python dependencies, including `launchpadlib`, are
installed automatically in the tool's isolated environment.

The package provides three commands:

```sh
lpshipit --help
lpmpmessage --help
lpmptox --help
```

Git must be installed to work with repositories. Running tests with `lpmptox`
also requires `tox` on your `PATH` (for example, `uv tool install tox`). Its
`--environment` option requires a configured LXD installation with the `lxc`
command, plus `petname`.

Upgrade a PyPI or Git installation with `uv tool upgrade lpshipit`. To reinstall
from an updated checkout, run `uv tool install --force .`.

## Development

```sh
uv sync --locked
uv run lpshipit --help
uv run lpmpmessage --help
uv run lpmptox --help
```

Dependencies are declared in `pyproject.toml`, and `uv.lock` records the resolved
versions for reproducible development. To update dependencies, run
`uv lock --upgrade` followed by `uv sync --locked`.

Build a source distribution and wheel with `uv build`, and publish them with
`uv publish`. To bump the version in the package metadata, lockfile, and snap,
run `uv run bump-my-version bump patch` (this also creates a commit and tag).
