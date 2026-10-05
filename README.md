# datasource-queen

A text-only settlement game whose world is an embedded SQL database paged into a distributed key-value store, so each turn is durable.

## What it is for

It is the multiplayer fabric's durable-state data source, and the game is the workload that exercises it. Each resident is a database of its own, each cycle is a transaction, and an HTN planner makes the ruler's choices. The store's virtual file system keeps no local database file, so a resident's state can move between machines without a copy. [docs/design.md](docs/design.md) carries the design.

## Build and run

```sh
cmake -B build
cmake --build build
./build/queen play 200
```

The build needs the key-value store's C client library and SQLite installed on the host, and a run needs a live key-value cluster. `queen` with no arguments prints its usage. `docker compose run ci` runs the same build and play in a container that brings its own cluster.

## Licence

LICENSE and CITATION.cff say MIT, but the SPDX headers in `src/` and `test/` say Apache-2.0, so the two disagree until one is changed.
