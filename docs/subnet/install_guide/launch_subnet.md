---
title: Launch a Subnet
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

<iframe width="768" height="432" src="https://www.youtube.com/embed/m-sPbMrB8ow" title="Setting Up Your Own XDC-Subnet Tutorial" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


## Generate Subnet Configs With UI

  1. Pull `generator.sh` script from the generator Github repo
  ```
  curl -O https://raw.githubusercontent.com/XinFinOrg/Subnet-Deployment/master/deployment-generator/scripts/generate.sh
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
    **if you're using VSCode to SSH, the port might be forwarded to your machine automatically (no need for above step) 
  </p>
  </details>


  4. Config the Subnet options per your requirement.
  ![UI](../img/ui.png)

  5. follow the generated instructions in `commands.txt`. In general, the steps are:
      - start Subnet Nodes
      - deploy CSC
      - deploy XDC-Zero (optional)
      - start Subnet Services (relayer, stats-server, frontend)

  6. Once successfully deployed, you can check out [UI usage guide](../using_subnet.md)

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
