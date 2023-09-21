# Getting started with Kong API Gateway

Kong API is a scalable, open-source API gateway that provides load balancing, authentication, and other features to help developers build and manage APIs.

The code provided is a configuration file for the Kong API gateway. It defines the settings and configurations for the gateway, such as the hostname, port, and the location of the database.

# Summary

- [Prerequisites](#Prerequisites)
- [Installation](#installation)
- [Usage](#usage)
  - [Browse Customer](#browse-customer-site)
  - [Browse Admin](#browse-admin-api)
  - [Browse ADMIN GUI](#browse-admin-gui)
- [Kong Gateway Setup](#kong-gateway-setup-for-api)
- [FAQ](#faq)
- [Contributing](#contributing)

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Installation

```bash
git clone https://github.com/najeen182/kong-gateway-compose.git
cd kong-gateway-compose
```

## Configuration

### Environment variables

| Variable name                 | Description                                                | Default value | Required?                                      |
| ----------------------------- | ---------------------------------------------------------- | ------------- | ---------------------------------------------- |
| KONG_DATABASE                 | pg database name for kong                                  | kong          | NO will configure from default, if not specify |
| KONG_PG_HOST                  | pg host name                                               | kong-database | NO will configure from default, if not specify |
| KONG_PG_PASSWORD              | pg password                                                | kong          | NO will configure from default, if not specify |
| KONG_PG_USER                  | pg username                                                | kong          | NO will configure from default, if not specify |
| KONG_CASSANDRA_CONTACT_POINTS | pg hostname                                                | kong-database | NO will configure from default, if not specify |
| KONG_CUSTOMER_PORT            | api gateway port that will be consumed by user or frontend | 80            |                                                |
| KONG_ADMIN_API_PORT           | kong ADMIN API PORt                                        | 8001          |                                                |
| KONG_UI_PORT                  | kong manager ui                                            | 8002          |                                                |
| KONG_VERSION                  | kong version                                               | latest        |

## Usage

```bash
docker-compose up -d --wait     #wait till all container are healthy
```

```bash
docker-compose up -d kong kong-manager #if you want to skip kong database
```

### Browse Customer site

Go to [http://localhost/](http://localhost:80)

### Browse ADMIN API

Go to [http://localhost:8001/](http://localhost:8001)

### Browse ADMIN GUI

Go to [http://localhost:8002/manager](http://localhost:8002/manager)

## Kong Gateway Setup For API

Kong gateway setup for our micro services API can be configured via [ADMIN API](http://localhost:8001) or [ADMIN GUI](http://localhost:8002/manager)

[API DOCS](https://docs.konghq.com/gateway/latest/admin-api/)

## FAQ

1. **Unable to start kong or run kong migration**

In some cases, when we run the container via docker compose, sometimes the postgres is not healthy, due to which kong-migration or kong service fails to run, in such case you can run the application with

```bash
docker compose up -d --wait
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss whatyou would like to change.

Please make sure to update tests as appropriate.
