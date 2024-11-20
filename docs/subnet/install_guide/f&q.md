---
title: Upgrading the Subnet
# TODO: title
---

# Common Issues and Troubleshooting

## Common Issues 
  - Subnet blocks are not being mined.
    1. First confirm that the Subnet nodes are able to communicate with each other through the network layer. Run the check peer script `generated/scripts/check-peers.sh` the number of peers should be one less than number of subnet nodes. For example, if there are 3 Subnet nodes in total, each node should have 2 peers.

    2. If the nodes are peering but still not mining, it could be a low memory issue. In Docker configs you can try to increase memory or swap. Then, in case of fresh Subnet, [delete data and start the nodes again](./1_launch_subnet.md/#deleting-subnet). ![Docker Memory Config](./img/docker_mem.png)

    3. Docker engine in Mac OS can be inconsistent after long-running or high-load. It could help to restart the machine and [hard reset the subnet](./1_launch_subnet.md#deleting-subnet ) to get it running.

  - Subnet node does not boot with error log `Fatal: Error starting protocol stack: listen unix /work/xdcchain/XDC.ipc: bind: invalid argument`

  This is due to the volume mount path being too long. The mounth path is your current directory (also can check with `pwd` command). Please move the `generated` folder to a shorter path and try again.

  - Docker image startup fails with `SIGKILL` or `Error code: 137` found in logs. (Issue found in Frontend image)

  This error occurs because Docker ran Out Of Memory (OOM). You can increase the memory limit in [Docker settings](https://docs.docker.com/desktop/settings/mac/#:~:text=lower%20the%20number.-,Memory,-.%20By%20default%2C%20Docker)

   


## Troubleshooting Scripts
  - `generated/scripts/check-mining.sh`

  This will check your current block in Subnet

  - `generated/scripts/check-peers.sh`
  
  This will check the number of peers of your Subnet node


## Telegram Troubleshooting Support Group
  https://t.me/+jvkX6LaLEEthZWM1


## Frequently Asked Questions

 - How many Subnet nodes should I have?

  Even one node is enough to start the Subnet blockchain! However, for better decantralized security, 3+ nodes is recommended. At least 2/3 of all nodes must be online and honest to mine blocks.

 - For testing, should I checkpoint the Subnet to devnet or testnet?
 
  Testnet, devnet will be less stable due to frequent development changes.

 - Where are all the Subnet tokens, how do I use the Subnet?

  In XDC-Subnet all initial tokens are assigned to the Grandmaster wallet (check keys.json). You can transfer them to any wallet address. Check [Faucet](../usage/2_faucet.md).

- How can I manage Subnet tokens?

  1. Check [here](../usage/2_faucet.md) for how you can use the Subnet Faucet to easily transfer Subnet tokens to your users.
  2. You can use any web3 wallet and connect to the Subnet RPC as a custom network, then transfer to other addresses.

 - How can I easily give out Subnet tokens to my users?
 
  We have provided a Faucet server for you to deploy under `generated/scripts/faucet-server.sh`. Anyone with access to the faucet page can request for tokens.
  Please check (faucet page)

 - Which files contain sensitive data and private keys?

  common.env, contract_deploy.env, keys.json, and subnet*.env. Please make sure these files are kept securely.

- This function didn't work/I have encoutered an unexpected bug

  For troubleshooting we can help you at [Telegram Support Group](./3_troubleshooting.md#telegram-troubleshooting-support-group) and we will check as soon as possible.

  Other channels for suggestions/requests include [XDC Forum](https://forum.xinfin.org/) and [GitHub Issues](https://github.com/XinFinOrg/XDC-Subnet/issues)

- How do I change the Relayer Wallet/Parentchain Wallet?

  You can [update services configs](./2_configs_explanation.md#updating-services-configs) in common.env to change the Relayer key
