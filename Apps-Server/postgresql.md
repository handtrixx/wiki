---
title: Databases
description: PSQL, MariaDB, MySQL optimized for Docker
published: true
date: 2025-10-29T15:18:23.070Z
tags: docker
editor: markdown
dateCreated: 2025-10-29T13:32:33.073Z
---

# Compose File

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

