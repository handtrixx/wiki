---
title: MariaDB
description: Die bessere Alternative zu MySQL
published: true
date: 2025-10-29T12:35:10.087Z
tags: docker
editor: markdown
dateCreated: 2025-10-29T12:35:10.087Z
---

# Compose File
```yaml
  db:
    container_name: YOURCONTAINERNAME
    image: mariadb:10.11
    user: "1000:1000"
    restart: unless-stopped
    command: --transaction-isolation=READ-COMMITTED --log-bin=binlog --binlog-format=ROW --log_bin_trust_function_creators=true
    volumes:
      - ./db:/var/lib/mysql
    environment:
      MARIADB_ROOT_PASSWORD: YOURROOTPASSWORD
      MARIADB_DATABASE: YOURDB
      MARIADB_USER: YOURUSER
      MARIADB_PASSWORD: YOURPASSWORD
      TZ: Europe/Berlin
      PUID: 1000
      PGID: 1000
    networks:
      - default
```