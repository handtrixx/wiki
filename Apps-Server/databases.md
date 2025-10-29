---
title: Databases
description: PSQL, MariaDB, MySQL optimized for Docker
published: true
date: 2025-10-29T15:27:54.511Z
tags: docker
editor: markdown
dateCreated: 2025-10-29T13:32:33.073Z
---

# MariaDB

## compose.yml file
```yaml

```

## .env file

```ini
MARIADB_ROOT_PASSWORD=
MARIADB_DATABASE=
MARIADB_USER=
MARIADB_PASSWORD=
TZ=Europe/Berlin
PUID=1000
PGID=1000
```

## Operations

Dump Database
```bash
docker exec DBCONTAINERNAME sh -c 'exec mysqldump -u"root" -p"ROOTPASSWORD" "DBNAME"' > dump.sql
```

Restore Database
```bash
cat dump.sql | docker exec -i DBCONTAINERNAME sh -c 'exec mysql -u"root" -p"ROOTPASSWORD" "DBNAME"'
```

# PSQL

## Compose File

```yaml
services:
  db:
    container_name: YOURCONTAINERNAME
    image: postgres:15-alpine
    user: "1000:1000"
    environment:
      POSTGRES_DB: YOURDB
      POSTGRES_PASSWORD: YOURPASSWORD
      POSTGRES_USER: YOURUSER
      PUID: 1000
      PGID: 1000
      TZ: Europe/Berlin
    restart: unless-stopped
    volumes:
      - ./db:/var/lib/postgresql/data
    networks:
      default:
 ```

