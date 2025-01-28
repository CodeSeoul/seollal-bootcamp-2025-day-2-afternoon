# Seollal Bootcamp 2025 Day 2 Afternoon

This repository is meant to catch everyone up with the current state of things for starting the afternoon of Day 2.


## Setup for Development

```shell
python -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -e ".[dev]"
pre-commit install
```

## Formatting

```shell
ruff check --fix .
```

## Running

### For Dev

```shell
source .venv/bin/activate  # if not done already
docker compose up -d
run
```

### Dockerized

#### Build the Image

```shell
# Build the image defined in the current directory, tagging it with the name "seollal-bootcamp"
docker build . -t seollal-bootcamp
```

#### Run the Container

```shell
docker compose up -d
# This runs the image as a container named backend-server, deletes the container when it stops,
# joins it to the network of the containers running via docker compose, publishes the container's
# port 80 to our port 8080, and sets the environment variables properly
docker run --name backend-server --rm \
    --network seollal-bootcamp-2025-backend_default \
    --env DB_HOST=database \
    --publish 8080:80 \
    seollal-bootcamp
```

## Stopping

Ctrl + C, then

```shell
docker compose down
```
