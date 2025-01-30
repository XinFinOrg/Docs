---
title: Configs Explanation
---

# Configs Explanation

## Files under 'generated' directory 
After the generator has succesfully run, all generated files will be under 'generated' directory. These files can be edited if you would like to further customize your subnet. Below is a description of each generated file and how it is used.

- commands.txt - The generated instructions to launch the subnet.
- common.env - The config parameters for Subnet services.
- contract_deploy.env - The config file used for CSC deployment.
- subnet*.env - The config parameters for each Subnet node.
- genesis.json - The 'block 0' of the Subnet. Initializes the blockchain for subnet nodes.
- genesis_input.yml - An intermediate file used in config generation.
- keys.json - Generated keypairs or custom keypairs by user input. Please be mindful to keep the credentials secure.
- docker-compose.yml - The main deployment file. Includes docker images versions, startup commands, network configurations.
- docker-compose.env - The config injection path that docker uses to point to other *.env files.

### common.env
- PARENTNET_URL - RPC of the parentnet
- SUBNET_URL - RPC of the Subnet
- PARENTNET_WALLET - Public key of the Relayer wallet
- PARENTNET_WALLET_PK - Private key of the Relayer wallet
- VITE_SUBNET_URL - URL of stats server backend that is passed to your local browser
- VITE_SUBNET_RPC - URL of the Subnet RPC that is passed to your local browser
- CHECKPOINT_CONTRACT - Checkpoint Smart Contract address
- STATS_SECRET - Secret used by stats server backend
- EXTIP - Configured IP of bootnode
- BOOTNODE_PORT - Configured port of bootnode

### subnet*.env
- INSTANCE_NAME - Subnet node name
- PRIVATE_KEY - Subnet node private key
- BOOTNODES - Subnet bootnode to connect and discover other Subnet nodes
- NETWORK_ID - Subnet network ID
- SYNC_MODE - Node operation mode (full or archive)
- RPC_API - enabled api's scheme such as eth, xdpos, debug, net
- STATS_SERVICE_ADDRESS - Stats server backend URL
- STATS_SECRET - Secret to authenticate with Stats server
- PORT - Subnet node port for communication with other Subnet nodes
- RPCPORT - Subnet node port for accepting RPC calls
- WSPORT -  Subnet node port for accepting Websocket connections
- LOG_LEVEL - Desired logging level. 2=Warn, 3=Info, 4=Debug.



## Subnet Ports
1. Subnet Nodes - 3 ports are used per each subnet, RPC port, WS port, and Peering port. The port number is incremented by 1 for the next subnet node. For example subnet1's RPC is 8545, subnet2's RPC will be 8546 and so on.
  - RPC PORT - 8545, 8546, 8547, ... This is the API port, for outside chain communication to issue transaction or query chaindata.
  - WS PORT - 9555, 9556, 9557, ... This is not used currently.
  - Peering port - 20303, 20304, 20305, ... This is used for subnet nodes and bootnode peering and communication.
  - Subnet ports config can be changed in `subnetX.env` for each individual subnet.
2. Bootnode - port 20301
  - Bootnode port can be changed at `BOOTNODE_PORT` under `common.env`. Also in each `subnetX.env`, `BOOTNODES` port has to be changed.
3. Stats Server (UI backend) - port 5213. 
4. UI Frontend - port 5214.
5. Relayer UI - port 5215.
6. Faucet Server - port 5211
7. Generator UI - port 5210.
<!-- 7. Explorer UI - port -->

