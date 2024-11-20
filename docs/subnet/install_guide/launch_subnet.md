---
title: Upgrading the Subnet
# TODO: title
---

# Launch a Subnet

## Requirements
  - OS: Linux. Only Linux is supported for full deployment.

  - OS: Mac is only supported for single machine testing environment.
  
  - docker, docker compose V2. For manual installation of docker compose V2 please refer to: https://docs.docker.com/compose/install/linux/
  
  - Recommended Hardware (per single Subnet node):
    - CPU: 2 Core
    - Memory: 4 GB

  - Web3 wallet with funds. For testing we have faucets provided:
    - https://faucet.apothem.network/ 
    - https://faucet.blocksscan.io/

## Video Walkthrough
<iframe width="720" height="400" src="https://www.youtube.com/embed/m-sPbMrB8ow" frameborder="0" allow="fullscreen"></iframe>

## Generate Subnet Configs With UI

  1. Pull `generator.sh` script from the generator Github repo
  ```
  curl -O https://raw.githubusercontent.com/XinFinOrg/XinFin-Node/master/subnet/deployment-generator/scripts/generate.sh
  ```
  
  2. Run the configuration generator, this will start a local webserver
  ```
  chmod +x generate.sh
  ./generate.sh
  cd generated
  ```

  3. Go to [http://localhost:5210/](http://localhost:5210) in your browser.
  <details>
  <summary>If you are running this on a remote server.</summary>
  <p>
    first use ssh tunnel: <code>ssh -N -L localhost:5210:localhost:5210 USERNAME@IP_ADDRESS -i SERVER_KEY_FILE</code>
  </p>
  </details>


  4. Config the Subnet options per your requirement.
  ![UI](./img/ui.png)

  5. follow the generated instructions in `commands.txt`. In general, the steps are:
      - start Subnet Nodes
      - deploy CSC
      - deploy XDC-Zero (optional)
      - start Subnet Services (relayer, stats-server, frontend)

  6. Once successfully deployed, you can check out [UI usage guide](../usage/ui/1_homepage.md)

## Removing Subnet

  ### Shutdown Subnet
  Under `generated` directory
  ```
  docker compose --env-file docker-compose.env --profile services down 
  docker compose --env-file docker-compose.env --profile machine1 down
  ```

  ### Deleting Subnet 
  Remove `xdcchain*`, `bootnodes`, and `stats-service` directories
  Warning: this cannot be undone
  ``` 
  rm -rf xdcchain* bootnodes stats-service
  ```
