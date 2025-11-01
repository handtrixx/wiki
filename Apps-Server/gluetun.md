---
title: Gluetun and NZB
description: VPN Proxy für Docker
published: true
date: 2025-11-01T12:32:54.434Z
tags: docker
editor: markdown
dateCreated: 2025-11-01T08:45:58.904Z
---

# Concept

```mermaid
flowchart LR;
subgraph AA [Docker Containers]
A[gluetun];
B[nzbhydra2];
C[Node.js client];
end
E[Internet];
Z[gluetun VPN Proxy Network];
A --> Z;
B --> Z;
C --> Z;
Z --> E;
```

```mermaid
C4Context
    title System Context diagram for Internet Banking System
    Enterprise_Boundary(b0, "BankBoundary0") {
        Person(customerA, "Banking Customer A", "A customer of the bank, with personal bank accounts.")
        Person(customerB, "Banking Customer B")
        Person_Ext(customerC, "Banking Customer C", "desc")

        Person(customerD, "Banking Customer D", "A customer of the bank, <br/> with personal bank accounts.")

        System(SystemAA, "Internet Banking System", "Allows customers to view information about their bank accounts, and make payments.")

        Enterprise_Boundary(b1, "BankBoundary") {
            SystemDb_Ext(SystemE, "Mainframe Banking System", "Stores all of the core banking information about customers, accounts, transactions, etc.")

            System_Boundary(b2, "BankBoundary2") {
                System(SystemA, "Banking System A")
                System(SystemB, "Banking System B", "A system of the bank, with personal bank accounts. next line.")
            }

            System_Ext(SystemC, "E-mail system", "The internal Microsoft Exchange e-mail system.")
            SystemDb(SystemD, "Banking System D Database", "A system of the bank, with personal bank accounts.")

            Boundary(b3, "BankBoundary3", "boundary") {
                SystemQueue(SystemF, "Banking System F Queue", "A system of the bank.")
                SystemQueue_Ext(SystemG, "Banking System G Queue", "A system of the bank, with personal bank accounts.")
            }
        }
    }

    BiRel(customerA, SystemAA, "Uses")
    BiRel(SystemAA, SystemE, "Uses")
    Rel(SystemAA, SystemC, "Sends e-mails", "SMTP")
    Rel(SystemC, customerA, "Sends e-mails to")
```

[![](https://mermaid.ink/img/pako:eNqdVV1v2jAU_StXfuqkjBG-FU2TCNBqD0jd2r1MkSqTXMBqYiPbWWEV_32Ok0AA027LC9i-x-ce3-PrVxKLBElAJr2J4Bq3OuJgPs10ivCwUxozqFYgYXQlaQZLIeGrmZIcNYSUPzO-qmJL9KxY3Eim8CkUOU-o3N0s2h5EpIiup9oR-QCvJaL47lEqwW_iXGmRoRzX8cXuk2oSxhEp5sdQh4FYgl4jLEykBy9Mr2FjN6KpnQMax4ZQq5ahu0oWOslCB-RpttUH2MQJm5Q5Jqhiu8FV1qkTPn1b4ueF_PTlfaFH0rIyN-XP2B7rteqVxGkqXtSBXYEW8IvhCzBuKp9RzQQHuhC5LrJi8pTdA8oTyOgzwobuMnQk5LSHf26PM3cclUwXtgblYFbA5tSkZpyJTj0PWkhUQNO0PsjYTNisi9BLVQflXkOVlpQrGhdhZoQ6Pld1TLChqnOuquOQdVmkpi-qSzg-8aITFjpgYW0mVY7_-rYAL658yji2Lpj3V3Qfy2IvxuxjRllaMZd5PBpuZs1nCOcslkKJpYbZNl5TvkLAJuSSuDZAxTJ1CJ7ClGq6oAr_V7mjrseCds8L2i1pFtdde0z8W445VrnfOnK_BRtxPfHWGyaw0EYJ7hwEd-8R_EMHrYxw9vdgjZB9x7TZzJv954dCddisjDwuNy72SZwryvrsAXmiKuuo6s7PH-8dQBN-8rycIE2fMxDikZVkCQm0zNEjJtIsmiGxVY2IOanMHGBQNHgqnyMS8b3BbCj_KURWw6TIV2sSLGmqzCjfJFTjtHw-DyGG27wgxcmSwB927B4keCVbEnT6o1Z3MOr7vj_q9bpdv--RHQkGndZgODALo17f73X94d4jvy1ruzUa9tuNz_cIJsx0vnn5vttnfv8HXlGGxg?type=png)](https://mermaid.live/edit#pako:eNqdVV1v2jAU_StXfuqkjBG-FU2TCNBqD0jd2r1MkSqTXMBqYiPbWWEV_32Ok0AA027LC9i-x-ce3-PrVxKLBElAJr2J4Bq3OuJgPs10ivCwUxozqFYgYXQlaQZLIeGrmZIcNYSUPzO-qmJL9KxY3Eim8CkUOU-o3N0s2h5EpIiup9oR-QCvJaL47lEqwW_iXGmRoRzX8cXuk2oSxhEp5sdQh4FYgl4jLEykBy9Mr2FjN6KpnQMax4ZQq5ahu0oWOslCB-RpttUH2MQJm5Q5Jqhiu8FV1qkTPn1b4ueF_PTlfaFH0rIyN-XP2B7rteqVxGkqXtSBXYEW8IvhCzBuKp9RzQQHuhC5LrJi8pTdA8oTyOgzwobuMnQk5LSHf26PM3cclUwXtgblYFbA5tSkZpyJTj0PWkhUQNO0PsjYTNisi9BLVQflXkOVlpQrGhdhZoQ6Pld1TLChqnOuquOQdVmkpi-qSzg-8aITFjpgYW0mVY7_-rYAL658yji2Lpj3V3Qfy2IvxuxjRllaMZd5PBpuZs1nCOcslkKJpYbZNl5TvkLAJuSSuDZAxTJ1CJ7ClGq6oAr_V7mjrseCds8L2i1pFtdde0z8W445VrnfOnK_BRtxPfHWGyaw0EYJ7hwEd-8R_EMHrYxw9vdgjZB9x7TZzJv954dCddisjDwuNy72SZwryvrsAXmiKuuo6s7PH-8dQBN-8rycIE2fMxDikZVkCQm0zNEjJtIsmiGxVY2IOanMHGBQNHgqnyMS8b3BbCj_KURWw6TIV2sSLGmqzCjfJFTjtHw-DyGG27wgxcmSwB927B4keCVbEnT6o1Z3MOr7vj_q9bpdv--RHQkGndZgODALo17f73X94d4jvy1ruzUa9tuNz_cIJsx0vnn5vttnfv8HXlGGxg)

# compose.yml file
```yaml
services:
  gluetun:
    image: qmcgaw/gluetun:latest
    container_name: gluetun
    cap_add:
      - NET_ADMIN
    devices:
      - /dev/net/tun:/dev/net/tun
    environment:
      VPN_SERVICE_PROVIDER: ${VPN_SERVICE_PROVIDER}
      VPN_TYPE: ${VPN_TYPE}
      WIREGUARD_PRIVATE_KEY: ${WIREGUARD_PRIVATE_KEY}
      WIREGUARD_ADDRESSES: ${WIREGUARD_ADDRESSES}
      SERVER_COUNTRIES: ${SERVER_COUNTRIES}
    volumes:
      - ./gluetun:/gluetun
    ports:
      - 8089:8080
      - 5076:5076
    restart: unless-stopped
    healthcheck:
      test: ["CMD-SHELL", "wget -qO- https://ipinfo.io/ip || exit 1"]
      interval: 30s
      timeout: 10s
      retries: 5
  nzbhydra2:
    image: lscr.io/linuxserver/nzbhydra2:latest
    container_name: nzbhydra2
    network_mode: "service:gluetun"
    depends_on:
      gluetun:
        condition: service_healthy
    environment:
      PUID: ${PUID}
      PGID: ${PGID}
      TZ: ${TZ}
    volumes:
      - ./nzbhydra:/config
      - ./downloads:/downloads
    restart: unless-stopped
    healthcheck:
      test: ["CMD-SHELL", "curl https://ipinfo.io/ip || exit 1"]
      interval: 30s
      timeout: 10s
      retries: 5
  sabnzbd:
    image: lscr.io/linuxserver/sabnzbd:latest
    container_name: sabnzbd
    user: "1000:1000"
    network_mode: "service:gluetun"
    depends_on:
      gluetun:
        condition: service_healthy
    environment:
      PUID: ${PUID}
      PGID: ${PGID}
      TZ: ${TZ}
    volumes:
      - ./sabnzbd:/config
      - /storage/storagefs/downloads/complete:/downloads
      - /storage/storagefs/downloads/incomplete:/incomplete-downloads
    restart: unless-stopped
    healthcheck:
      test: ["CMD-SHELL", "wget -qO- https://ipinfo.io/ip || exit 1"]
      interval: 30s
      timeout: 10s
      retries: 5
```

# .env file
```ini
PUID=1000
PGID=1000
TZ=Europe/Berlin

VPN_SERVICE_PROVIDER=yourprovider
VPN_TYPE=wireguard
WIREGUARD_PRIVATE_KEY=yourprivatekey
WIREGUARD_ADDRESSES=providersnetwork
SERVER_COUNTRIES=yourcountries
```

# Prompts
 test from host: 
 ```bash
 docker run --rm --network=container:gluetun alpine:3.20 sh -c "apk add wget && wget -qO- https://ipinfo.io"
```

test from guest:
```guest
wget -qO- https://ipinfo.io/ip
```
# Sources
- https://hub.docker.com/r/qmcgaw/gluetun
- https://docs.linuxserver.io/images/docker-sabnzbd/
- https://docs.linuxserver.io/images/docker-nzbhydra2/