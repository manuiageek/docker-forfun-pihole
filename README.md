# Pi-hole — Docker Compose

## Prerequisites
- Linux host (Raspberry Pi or x86) with _static_ IP **192.XXX.XXX.XXX**  
- Docker Engine 20.10+ & Docker Compose v2  
- Two external Docker volumes:
  ```bash
  docker volume create pihole_etc-pihole
  docker volume create pihole_etc-dnsmasq.d
  ```

## What this stack creates
| Resource                | Purpose                              |
|-------------------------|--------------------------------------|
| `pihole` container      | DNS sinkhole + web UI on ports 53/80 |
| Volume `pihole_etc-pihole` | Pi-hole config, gravity DB        |
| Volume `pihole_etc-dnsmasq.d` | custom dnsmasq configs        |

## Usage
```bash
# clone / copy docker-compose.yml
docker compose up -d      # start
docker compose logs -f    # view logs
docker compose down       # stop
```

Access UI: `http://192.XXX.XXX.XXX/admin`  
Default login password: value of `WEBPASSWORD` in _docker-compose.yml_ (change it ASAP).

