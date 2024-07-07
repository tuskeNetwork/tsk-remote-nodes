# TSK Remote Nodes


## Requirements

To build the executable binaries, you need:

-   Go >= 1.22
-   NodeJS >= 20

### Server & Prober requirements

-   Linux Machines (AMD64 or ARM64)

### Server requirements

-   MySQL/MariaDB
-   [GeoIP Database](https://dev.maxmind.com/geoip/geoip2/geolite2/) (optional). Place it to `./assets/geoip`, see [./internal/geo/ip.go](./internal/geo/ip.go).

## Installation

### For initial server setup:

1. Download [GeoIP Database](https://dev.maxmind.com/geoip/geoip2/geolite2/) and place it to `./assets/geoip`. (see [./internal/geo/ip.go](./internal/geo/ip.go)).
2. Pepare your MySQL/MariaDB.
3. Copy `.env.example` to `.env` and edit it to match with server environment.
4. Build the binary with `make server` (or `make build` to build both **server** and **client** binaries).
5. Run the service with `./bin/tsk-nodes-server-linux-<YOUR_CPU_ARCH> serve`.

Systemd example: [./deployment/init/tsk-nodes-server.service](./deployment/init/tsk-nodes-server.service).

### For initial prober setup:

1. Create API key for prober
2. Copy `.env.example` to `.env` and edit it to match with prober environment.
3. Build the binary with `make client` (or `make build` to build both **server** and **client** binaries).
4. Run the service with `./bin/tsk-nodes-client-linux-<YOUR_CPU_ARCH> probe`.

Systemd example: [tsk-nodes-prober.service](./deployment/init/tsk-nodes-prober.service) and [tsk-nodes-prober.timer](./deployment/init/tsk-nodes-prober.timer).

## Development and Deployment

See the [Makefile](./Makefile).

