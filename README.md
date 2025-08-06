# nginx_poc

A proof-of-concept project demonstrating Nginx as a load balancer for 3 backend servers,
running under a Docker container using Docker Compose.

## Quick Start

```sh
git clone https://github.com/deck451/nginx_poc.git
cd nginx_poc
docker compose up --build
```

## Usage

Run the following command multiple times and observe the requests being served by all three
backend servers, in a round-robin fashion:

```sh
curl http://localhost:82
```
