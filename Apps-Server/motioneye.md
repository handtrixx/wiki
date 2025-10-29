---
title: motionEye
description: Kameraufzeichnungen
published: true
date: 2025-10-29T12:44:14.835Z
tags: docker, homeserver
editor: markdown
dateCreated: 2025-10-29T10:11:09.042Z
---

# Quellen
https://github.com/motioneye-project/motioneye/tree/main

# Docker Compose File

```yaml
services:
  motioneye:
    # ToDo: Change from unstable dev/edge to stable GitHub registry release and Docker registry release, once available
    image: ghcr.io/motioneye-project/motioneye:edge  # https://github.com/motioneye-project/motioneye/pkgs/container/motioneye
    ports:
      - "8081:8081"
      - "8765:8765"
    volumes:
      - etc_motioneye:/etc/motioneye
      - var_lib_motioneye:/var/lib/motioneye

volumes:
  etc_motioneye:
  var_lib_motioneye:
```