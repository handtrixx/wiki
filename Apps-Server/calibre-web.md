---
title: Calibre Web
description: Deine Bibliothek immer im Zugriff
published: true
date: 2025-10-27T10:58:04.500Z
tags: docker
editor: markdown
dateCreated: 2025-10-27T10:58:04.500Z
---

Auch bei mir haben sich eBooks neben "echten" Büchern nicht nur im Urlaub, sondern im Alltag etabliert. [Calibre-Web](https://github.com/janeczku/calibre-web) bietet uns die Möglichkeit unsere [Calibre](https://calibre-ebook.com) Bibliothek in einer hübschen Web UI zu verpacken, und sogar Bücher von dort direkt z.B. an mein Kindle zu senden.

![calibre.png](/assets/linux/calibre/calibre.png){.align-center}

# Compose File

So kann euer ```compose.yml``` zum Beispiel aussehen:

```yaml
services:
  calibre:
    image: lscr.io/linuxserver/calibre-web:latest
    container_name: calibre
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Europe/Berlin
      - DOCKER_MODS=linuxserver/mods:universal-calibre #optional
    volumes:
      - ./data:/config
      - /storage/storagefs/media/books:/books
    restart: unless-stopped
    networks:
      - caddy
networks:
    caddy:
        external: true
```

# Konfiguration, Wartung und Tools
Admin Password setzen:
```bash
docker exec -it calibre python3 /app/calibre-web/cps.py -p /config/app.db -s admin:NEWPASSWORD
```
Bücher aus anderer Quelle importieren:
```bash
docker exec -it calibre sh -c "calibredb add --with-library /books --recurse /import --automerge ignore"
```

# Alternativen zu Calibre-Web
- [Kavita](https://www.kavitareader.com)