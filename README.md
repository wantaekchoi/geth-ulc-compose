# Ethereum Geth ULC (Ultra Light Clients)

This project allows you to deploy and manage an Ethereum Geth Ultra Light Client (ULC) using Docker.

## Environment Variables

The username for the Geth user in the container can be specified by setting the `GETH_USER` environment variable before running the Docker Compose commands.

In a UNIX-like environment, use `export` to set environment variables:

```bash
# Set the GETH_USER environment variable
export GETH_USER=wantaek
```

In a Windows environment, use `set`:

```cmd
REM Set the GETH_USER environment variable
set GETH_USER=wantaek
```

Please replace `wantaek` with the username you want to use for the Geth user in the container.

## Build

First, build the Docker image.

```bash
docker compose build
```

You can optionally provide a username for the geth user by adding it as a build argument.

```bash
docker compose build --build-arg GETH_USER=$GETH_USER
```

## Run

After the image has been built, you can start your node.

```bash
docker compose up
```

## Configuration

The configuration can be checked using:

```bash
docker-compose config
```

## Ports

The Ethereum Geth Node is exposed on port `8545` for HTTP based JSON-RPC

and on port `30303` for P2P communication.

## Volumes

The Ethereum data is persisted in a volume mounted at `./eth`.
