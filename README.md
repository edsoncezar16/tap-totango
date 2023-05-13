# tap-totango

`tap-totango` is a Singer tap for totango.

Built with the [Meltano Tap SDK](https://sdk.meltano.com) for Singer Taps.

## Installation

Install from PyPi:

```bash
pipx install tap-totango
```

Install from BitBucket:

```bash
pipx install git+https://bitbucket.org/indiciumtech/tap-totango.git@main
```

## Configuration

### Accepted Config Options

A full list of supported settings and capabilities for this
tap is available by running:

```bash
tap-totango --about
```

### Configure using environment variables

This Singer tap will automatically import any environment variables within the working directory's
`.env` if the `--config=ENV` is provided, such that config values will be considered if a matching
environment variable is set either in the terminal context or in the `.env` file.

### Source Authentication and Authorization

You should create a [Totango API personal access token](https://support.totango.com/hc/en-us/articles/203036939-Personal-Access-Token-and-Service-ID) and provide it as the `auth_token` setting for the tap.

We recommend passing it as an environment variable. For instance, when using the tap with Meltano you should add the following line to you `.env` file:

``` bash
export TAP_TOTANGO_AUTH_TOKEN=< YOUR_PERSONAL_ACCESS_TOKEN >
```

## Usage

You can easily run `tap-totango` by itself or in a pipeline using [Meltano](https://meltano.com/).

### Executing the Tap Directly

```bash
tap-totango --version
tap-totango --help
tap-totango --config CONFIG --discover > ./catalog.json
```

## Developer Resources

Follow these instructions to contribute to this project.

### Initialize your Development Environment

```bash
pipx install poetry
poetry install
```

### Create and Run Tests

Create tests within the `tests` subfolder and
  then run:

```bash
poetry run pytest
```

You can also test the `tap-totango` CLI interface directly using `poetry run`:

```bash
poetry run tap-totango --help
```

### Testing with [Meltano](https://www.meltano.com)

_**Note:** This tap will work in any Singer environment and does not require Meltano.
Examples here are for convenience and to streamline end-to-end orchestration scenarios._

<!--
Developer TODO:
Your project comes with a custom `meltano.yml` project file already created. Open the `meltano.yml` and follow any "TODO" items listed in
the file.
-->

Next, install Meltano (if you haven't already) and any needed plugins:

```bash
# Install meltano
pipx install meltano
# Initialize meltano within this directory
cd tap-totango
meltano install
```

Now you can test and orchestrate using Meltano:

```bash
# Test invocation:
meltano invoke tap-totango --version
# OR run a test `elt` pipeline:
meltano elt tap-totango target-jsonl
```

### SDK Dev Guide

See the [dev guide](https://sdk.meltano.com/en/latest/dev_guide.html) for more instructions on how to use the SDK to
develop your own taps and targets.

## Acknowledgements

Edson Nogueira thanks all members of the Meltaners group @ Indicium Tech, namely Cesar Rubim, Lucas Marques, Guilherme Tavares e Igor Benincá, for the professional guidance.
