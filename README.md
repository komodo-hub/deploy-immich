# Deploy Immich

Part of the [*Komodo Hub* collection.](https://github.com/komodo-hub/komodo-hub)

Runs Immich media server.

https://immich.app/docs/install/docker-compose

## Komodo Resource TOML

```toml
[[stack]]
name = "immich"
[stack.config]
repo = "komodo-hub/deploy-immich"
environment = """
  ## https://github.com/immich-app/immich/pkgs/container/immich-server/versions?filters%5Bversion_type%5D=tagged
  IMMICH_VERSION = release
  IMMICH_PORT = 2283

  ## Configure data directories
  UPLOAD_LOCATION = library
  DB_DATA_LOCATION = db-data

  RESTART = unless-stopped
  LOGGING_DRIVER = local

  DB_USERNAME = postgres
  DB_PASSWORD = [[IMMICH_DB_PASSWORD]]
  DB_DATABASE_NAME = immich

  REDIS_TAG = 6.2-alpine
  PGVECTO_TAG = pg14-v0.2.0
"""

[[variable]]
name = "IMMICH_DB_PASSWORD"
value = "your_db_password"
```