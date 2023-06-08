# Geth ULC Docker Compose

This project sets up a Dockerized instance of Geth (Go Ethereum) running in Ultra Light Client (ULC) mode.

## Prerequisites

- Docker and Docker-compose installed on your machine.
- Understanding of Ethereum, Geth and Docker is recommended.

## Setup Instructions

1. Clone the repository:

   ```
   git clone <repository-url>
   ```

1. Navigate to the cloned repository:

   ```
   cd <repository-directory>
   ```

1. Start the Docker service with a specified network. You can specify `--goerli`, `--mainnet` or `--sepolia` as a command line option to determine which network you would like to connect to:

   ```
   # For Ethereum mainnet
   EXTRA_OPTS='--mainnet' docker-compose up -d

   # For Görli network
   EXTRA_OPTS='--goerli' docker-compose up -d

   # For Sepolia network
   EXTRA_OPTS='--sepolia' docker-compose up -d
   ```

The provided `docker-compose.yml` file configures a Geth instance in ULC mode, listening on HTTP, and connected to specified trusted ULC servers.

You may replace the servers listed in `--ulc.servers` with addresses of your trusted servers.

## Ports

The service exposes the following ports:

- 8545: JSON-RPC HTTP interface
- 30303: P2P network interface

## Persisting data

Blockchain data is persisted in a Docker volume mapped to `./eth` in your host system.

## JSON-RPC APIs

The service enables the following JSON-RPC APIs: `eth`, `net`, `web3`, `debug`, and `admin`.

## Security

Ensure to properly manage your Docker environment and restrict access to your system, as your Geth instance will allow external connections due to the `--http.addr=0.0.0.0` and `--http.vhosts=\*` settings. Consider additional security measures for production environments.

## Notes

This setup allows you to select the network for the Geth ULC client to connect to. You can specify --goerli, --mainnet or --sepolia using the EXTRA_OPTS environment variable while starting the docker service.

## Contributing

For any issues, questions, or suggestions for improvement, please open an issue in the GitHub issue tracker. Contributions are welcome.
