---
title: Setup XDC Masternode using Docker
---

# Setup XDC Masternode using Docker

## Setting up XDC Network Masternode Docker version

The server or VPS used for the masternode should be directly facing the internet with a public IP and without NAT. 


**Operating System**: Ubuntu 20.04 64-bit or higher

Should be facing internet directly with **public IP** & **without NAT**

**Tools**: Docker, Docker Compose(1.27.4+)

Setup (For Ubuntu 20.04 64-bit or higher Operating System)

Follow the written steps starting from step 1, or you can watch the video tutorials:

<iframe width="768" height="432" src="https://www.youtube.com/embed/1A20eVTJYvs" title="Deploying an XDC Network Masternode via Docker" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Step 1: Clone repository
```bash
git clone https://github.com/XinFinOrg/XinFin-Node.git

```

## Step 2: Change directory
Then we change the directory to XinFin-Node
```bash
cd XinFin-Node
```

## Step 3: Install docker
We need to install Docker and Docker-Compose by running the following command:
```bash
sudo ./setup/install_docker.sh
```

## Step 4: 
Create a new .env file and copy the env.example file that exist in the mainnet directory. We will ensure we are in the "mainnet" directory by typing these commands. Once in edit mode for the .env file, name your masternode and use an email address in the respective fields
```bash
cd mainnet
cp env.example .env
nano .env 

```
**For Testnet**
```bash
cd testnet
cp env.example .env
nano .env
```

## Step 5: Start your Node
**For Mainnet run the following commands:**
```bash
cd mainnet
sudo docker-compose -f docker-compose.yml up -d
```
At this point you should be able to see your masternode on the list of nodes here or as shown below:

![node-sync](../../img/node_sync.png)

For Testnet run the following commands:
```bash
cd testnet
sudo docker-compose -f docker-compose.yml up -d
```
You should be able to see your node listed on the [Apothem Network] page. Select **"Switch to LiveNet"** to check **LiveNetwork** Stats and Select **"Switch to TestNet"** for **TestNetwork**.

Your coinbase address can be found in xdcchain/coinbase.txt file.

For troubleshooting purposes, you can stop the node by using the following command on either Mainnet or Testnet:
```bash
sudo docker-compose -f docker-compose.yml down
```

**Downloading a Network Snapshot (Mainnet or Apothem)**

The following steps are to expedite the syncing process of your node with the XDC Network.  If you followed the steps above, your node will take 3-4 days to sync up with the network fully.  You can reduce that time by downloading a network snapshot and bringing your node back up after the chain has been downloaded and unpacked. 

<iframe width="768" height="432" src="https://www.youtube.com/embed/ZQF3f0Zd6-k" title="Downloading an XDC Network Snapshot to Expedite Node Syncing to" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

# Mainnet Snapshot

**Bring down your node:**
```bash
sudo docker-compose -f docker-compose.yml down
```
**Remove the old xdchain file from the server**
```bash
rm -rf xdcchain.tar
```
**Download the snapshot** 
```bash
wget https://download.xinfin.network/xdcchain.tar
```
**Unpack the xdcchain.tar file**
```bash
tar -xvzf xdcchain.tar
```
**The unpacking will take some time, and it will look like this:**

![unpacking](../../img/unpacking.png)

**The following command will move the xdcchain/XDC to xdcchain/XDC_backup**
```bash
mv  xdcchain/XDC xdcchain/XDC_backup
mv XDC xdcchain
```

**Then we are going to remove the old "nodekey" file**
```bash
rm -rf xdcchain/XDC/nodekey
```

**The last step is to run the bash upgrade.sh command**
```bash
bash upgrade.sh
```

This command will bring your node up and it will start syncing to the network. Once up and running, your node will be synced to the network in just a few minutes. 

![node_upgrade](../../img/node_upgrade.png)

# Apothem Snapshot

**Bring down your node:** 
```bash
sudo docker-compose -f docker-compose.yml down
```

**Remove the old xdchain file from the server**
```bash
rm -rf apothem.tar
```

**Download the snapshot**

Full Node snapshot: 
```bash
wget http://downloads.apothem.network/xdcchain.tar
```

Archive Node snapshot: 
```bash
wget http://downloads.apothem.network/xdcchain_archive.tar
```

**Unpack the apothem.tar  file**
```bash
tar -xvzf apothem.tar
```

**Move the xdcchain-testnet**
```bash
mv XDC xdcchain-testnet
```

**Bring up the node**
```bash
sudo docker-compose -f docker-compose.yml up -d
```










