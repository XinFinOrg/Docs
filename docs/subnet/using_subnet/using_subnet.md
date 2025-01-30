---
title: Using Subnet
---
# UI Usage Guide
The guide for XDC Subnet user interface
## Homepage

Once subnet is successfully deployed. The homepage will show the following.

![Homepage 1](../img/homepage_1.png)

1. The Subnet blockchain state. You can see the current 'Not Confirmed' and 'Confirmed' blocks. 'Confirmed' or 'committed' blocks should be 3 blocks behind latest blocks.
2. The Subnet blockchain AS KNOWN by the Parentchain. The Relayer periodically calls the Checkpoint Smart Contract to update the Subnet status (default every 2 minutes).
3. The Network Info card shows the Subnet throughput state, by default Blocktime should be every 2 seconds. It also indicates the Parentchain network
4. The Relayer Info card shows the Relayer status. Which Checkpoint Smart Contract (CSC) it calls, Subnet blocks in the backlog, and the remaining wallet funds.
5. The Masternodes Info card shows the Subnet nodes status. By default, all Subnet nodes are Masternodes and all should be active.





In the lower half of the homepage there are more information as shown.

![Homepage 2](../img/homepage_2.png)



1. This card shows further details of subnet blocks, including their height, hash, proposer, and confirmation status. The left side of 'confirmation status' shows the block being committed in the Subnet chain and the right side shows the block hash being recorded in the Parent chain. 

2. This card shows a detailed view of the subnet nodes including their address. The status also differrentiates inactive nodes to 'penalty' or 'standby'

3. Additionally, you can select the UI theme (light or dark) by toggling this button.


## Confirmation Checker

After navigating with the left menu bar to the Confirmation Checker of the Subnet, this will be shown.

![Confirmation Checker 1](../img/confirm_1.png)

The input box accepts Block height, Block hash, and even TX hash. 

After your input, the search engine will traverse the chain and display the info accodingly. Below is an example of Block height search.

![Confirmation Checker 2](../img/confirm_2.png)

1. Confirmation status of the block (or the block that TX belongs to)
2. The block detailed information 
3. The Parentchain block where the Subnet block was recorded


Next is another example of a Block hash search.

![Confirmation Checker 3](../img/confirm_3.png)

1. Confirmation status of the block (or the block that TX belongs to)
2. The block detailed information 
3. As the Subnet block has not been checkpointed in the Parentchain, the UI is displaying height 0.


## Subnet Management

Subnet management is used for adding and removing Masternodes in the Subnet. To manage the subnet, you need to use the Grandmaster Account, as only the Grandmaster has the right to manage the Subnet.

You can find the Grandmaster Key in the `keys.json` file.

After making a modification with Subnet management, the change will take effect in the next epoch (900 blocks).

When adding a Masternode address in the management, the new Masternode server should also be started up and added to the network.

### 1. Log in to the Wallet and Connect to the Subnet

To manage the subnet, you need to use your **Grandmaster Account**. Find the **Grandmaster Key** in the `keys.json` file and import this account into your wallet.

![import_account](../img/import_account.png)

1. Go to the correct tab and switch to the **Grandmaster Account**.
2. Click the `Connect Wallet` button.
   ![connect_wallet](../img/connect_wallet.png)

3. Choose your wallet and allow the subnet network to be added. The wallet will automatically switch to this network, as shown below:
   ![switch_to_subnet](../img/switch_subnet.png)

   If the wallet doesn’t switch to the subnet automatically, follow the instructions on the page to fill in the network details manually and connect to the subnet.

4. Connect the account and network.
   ![account_connection](../img/account_connect.png)

You will see a confirmation page like this:

![successful_connection_confirmation](../img/successful_connection_confirmation.png)

### 2. Node Operations
#### 2.1 Add Nodes in a Subnet  
Subnet nodes are managed by two files. To add a node, create the corresponding `subnetX.env` file and add an entry in `docker-compose.yml`. Apply the changes to add the node to the subnet. (To remove a node, delete the related configuration file)  

To **add a node**, follow these steps:  

1. Go to the `generated` directory and run the `add-node.sh` script. Enter the key when prompted:  
   ```bash
   cd .scripts/add-node.sh
   ```  

2. Update the subnet settings with the following commands:  
   ```bash
   docker-compose --env-file docker-compose.env --profile machine1 up -d
   docker-compose --env-file docker-compose.env --profile services up -d
   ```
#### 2.2 Add candidate

1. Switch to the **Master List** Tab
2. Click the `Add a new master candidate` button to add the node as a master node. **Delegation amount** must be at least `10,000,000` Subnet tokens.
   ![add_master_node_candidate](../img/add_master_node_candidate.png)

#### 2.3 Change node delegation

- In the list, select the node you want to change the delegation for, then click the `Promote` / `Demote` button and enter the new delegation amount.

  - If increasing the delegation, ensure the total delegation amount is over `10,000,000` Subnet tokens; otherwise, the transaction will fail.There is no extra benefit in delegating more than 10,000,000 tokens to an address
  - If decreasing the delegation, ensure the remaining amount is still at least `10,000,000` Subnet tokens; otherwise, the transaction will fail.

    ![promote_node_delegate](../img/promote_node_delegate.png)

#### 2.4 Remove a node

1. In the **Master List** Tab, select the node you want to remove, and click the `Remove` button.
2. After removal, the node’s delegated XDC will be reset to zero, and the node information will be removed from the list after one epoch.
   ![remove_master_node](../img/remove_master_node.png)





