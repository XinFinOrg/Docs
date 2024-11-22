---
title: Upgrading the Subnet
---
# Upgrading the Subnet 
## Updating Configs
### Upgrading Subnet Deployment
#### Create a Subnet backup
1. [Shutdown the subnet](./1_launch_subnet.md#shutdown-subnet )

2. Make a copy of `xdcchain` directory

#### Update Subnet Versions
1. Go to `docker-compose.yml` under `generated` directory. 
2. Change the docker image tag of your desired component(s).
3. Run:
```
  docker compose --env-file docker-compose.env --profile machine1 up -d
  docker compose --env-file docker-compose.env --profile services up -d
```

Using `latest` tag is not recommended since not all components version are not guaranteed to be compatible.

### Updating Services Configs
1. Shut down subnet services
```
docker compose --env-file docker-compose.env --profile services down
```
2. Update configuration (usually ENVs inside common.env file)

3. Start subnet services
```
docker compose --env-file docker-compose.env --profile services up -d
```

