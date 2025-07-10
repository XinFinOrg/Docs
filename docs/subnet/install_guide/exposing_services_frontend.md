---
title: Exposing Subnet Frontend
---

# Exposing Subnet Frontend
To allow the Subnet Frontend to be accessible from the public, the following steps are required:

Update the following parameters in `common.env`, replacing `<YOUR_SERVER_IP>` with your actual server IP address or domain name:
```bash
VITE_SUBNET_URL=http://<YOUR_SERVER_IP>:5213
VITE_SUBNET_RPC=http://<YOUR_SERVER_IP>:8545
```

Modify the ports in `docker-compose.yml` as follows:
```yaml
  stats:
    ports:
      - '0.0.0.0:5213:5213'
  frontend:
    ports:
      - '0.0.0.0:5214:5214'
```
Finally, restart Subnet Frontend service:

```
  HOSTPWD=$(pwd)
  docker compose --profile services down frontend
  docker compose --profile services up -d frontend
```