---
title: Webtop
description: Dein Desktop im Browser
published: true
date: 2025-10-29T12:44:17.555Z
tags: docker
editor: markdown
dateCreated: 2025-10-29T10:23:00.748Z
---

# Docker Compose File
```yaml
services:
  webtop:
    image: lscr.io/linuxserver/webtop:fedora-kde
    container_name: webtop
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Europe/Berlin
      - CUSTOM_USER=YOURUSER
      - PASSWORD=YOURPASSWORD
      - DISABLE_IPV6=true #optional
      - LC_ALL=de_DE.UTF-8 #optional
      - TITLE=Webtop #optional
      - DOCKER_MODS=lscr.io/linuxserver/mods:universal-unrar6|linuxserver/mods:universal-package-install
      - INSTALL_PACKAGES=flatpak|dialog|dnf-plugins-core|ark
    volumes:
      - ./data:/config
      - /storage/storagefs:/config/storagefs
    ports:
      - 3000:3000
      - 3001:3001
    shm_size: "2gb" #optional
    restart: unless-stopped
    networks:
      - caddy
networks:
  caddy:
    external: true

```


# Quellen
https://docs.linuxserver.io/images/docker-webtop/