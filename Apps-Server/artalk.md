---
title: Artalk
description: Dein eigenes Kommentar-Managementsystem
published: true
date: 2025-10-27T10:45:30.040Z
tags: docker
editor: markdown
dateCreated: 2025-10-27T10:33:21.545Z
---

[Artalk](https://artalk.js.org), eine in GO geschriebene Anwendung, dient dazu eine Kommentarfunktion in WebApps einzubinden und zu verwalten. Das kann entweder durch eine native Integration wie bei [Wiki.js](/Apps-Server/wikijs) oder manuell ober die Artalk API erfolgen. Artalk ist Open-Source und lässt sich, wie im Beispiel hier, in einem Docker Container auf einem Server betreiben.

<video width="480px" autoplay>
  <source src="/assets/linux/artalk/artalk.webm" type="video/webm">
  Your browser does not support the video tag.
</video>

# Compose File
Das zugehörige Docker Compose File `compose.yml` kann so aussehen:

```yaml
services:
  artalk:
    container_name: artalk
    image: artalk/artalk-go
    restart: unless-stopped
    volumes:
      - ./data:/data
    networks:
      default:
      caddy:
    environment:
      - TZ=Euorope/Berlin
      - ATK_LOCALE=en
      - ATK_SITE_DEFAULT=wiki
      - ATK_SITE_URL=https://wiki.niklas-stephan.de
networks:
  caddy:
    external: true
```

# Konfiguration

Nach dem hochfahren des Service muss zunächst ein neuer Admin user angelegt werden. Folgender Befehl erledigt das:

```bash
docker exec -it artalk artalk admin
```

# Alternativen zur Artalk
- https://commento.io
- https://disqus.com