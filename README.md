# T-Digest Polars Plugin

This Polars plugin is a wrapper around the [T-Digest Rust implementation](https://docs.rs/tdigest/latest/tdigest/). It not only provides means to compute an estimated qunatile, but exposes the tdigest creation and merging functionality so it can be used to estimate quantiles in a distributed environment.

For an example see the [Yellow Taxi Notebook](./tdigest_yellow_taxi.ipynb). Note that this example is a bit artifical as it doesn't distribute the computation. It is mainly meant to show how to use the plugin with multiple partitions of a dataset. It does not make sense to use this plugin for computations on a single machine as the tdigest computation essentially adds overhead to the percentile computation and is therefore slower than computing the actual percentile.

# How to contribute

## Dev setup

Setup your virtual environment with a python version `>=3.8`, e.g. use `python -m venv .env`.
Install the python dependencies used for development:
```bash
python -m pip install -r requirements.txt
```

Install [Rust](https://rustup.rs/).

## Build

In order to build the package, please run `maturin develop`. If you want to test performance, run `maturin develop --release`. 

## Commit / Release

Before committing and pushing your work, make sure to run

```
cargo fmt --all && cargo clippy --all-features
python -m ruff check . --fix --exit-non-zero-on-fix
```

and resolve any errors.