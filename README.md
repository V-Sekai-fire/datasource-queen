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

A run needs a live key-value cluster, and `queen` with no arguments prints its usage. `docker compose run ci` runs the same build and play in a container that brings its own cluster.

## Licence

MIT; see LICENSE.
