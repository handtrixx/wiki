---
title: PostgreSQL
description: Die PSQL Datenbank optimiert für und durch Docker
published: true
date: 2025-10-29T12:44:19.078Z
tags: docker
editor: markdown
dateCreated: 2025-10-29T12:29:18.468Z
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

