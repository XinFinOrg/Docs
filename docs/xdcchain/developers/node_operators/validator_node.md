---
title: Validator/Standby Node
---

## Validator Masternode
Validator Masternodes operate and participate in XDC Network’s DPoS consensus engine, validating transactions and block creation. 

## Standby Masternodes
Standby Masternodes (or “Standby Nodes”) are identical in form and function to Validators but do not participate in validating transactions and block creation. These nodes are on standby to fill the role of Validators that drop from network participation.

# Setup XDC Validator/Standby Node using Bootstrap Script

## For Mainnet

**Bootstrap Command XDC Validator/Standby Node Setup:**

```
sudo su -c "bash <(wget -qO- https://raw.githubusercontent.com/XinFinOrg/XinFin-Node/master/setup/bootstrap.sh)" root
```

**Examples:**
After running the bootstrap command, the system will prompt you to specify the network. To connect to the Mainnet, simply enter "mainnet". 
```
$ sudo su -c "bash <(wget -qO- https://raw.githubusercontent.com/XinFinOrg/XinFin-Node/master/setup/bootstrap.sh)" root
[sudo] password for user:
Please enter your XinFin Network (mainnet/testnet/devnet) :- mainnet
```
Next, you will be asked to input your XinFin Masternode name. Enter your desired Masternode name, such as "Demo_Server."
```
Your running network is mainnet
Please enter your XinFin MasterNode Name :- Demo_Server
Your Masternode Name is Demo_Server

```


## For Testnet
After running the bootstrap command, the system will prompt you to specify the network. To connect to the Mainnet, simply enter "testnet".
```
sudo su -c "bash <(wget -qO- https://raw.githubusercontent.com/XinFinOrg/XinFin-Node/master/setup/bootstrap.sh)" root
Please enter your XinFin Network (mainnet/testnet/devnet) :- testnet
```
Next, you will be asked to input your XinFin Masternode name. Enter your desired Masternode name, such as "test01"
```
Your running network is testnet
Please enter your XinFin MasterNode Name :- test01
Your Masternode Name is test01
```

## For Devnet
After running the bootstrap command, the system will prompt you to specify the network. To connect to the Mainnet, simply enter "devnet".
```
sudo su -c "bash <(wget -qO- https://raw.githubusercontent.com/XinFinOrg/XinFin-Node/master/setup/bootstrap.sh)" root
Please enter your XinFin Network (mainnet/testnet/devnet) :- devnet
Your running network is devnet
```
Next, you will be asked to input your XinFin Masternode name. Enter your desired Masternode name, such as "test01"
```
Please enter your XinFin MasterNode Name :- test01
Your Masternode Name is test01
Generate new private key and wallet address.
If you have your own key, you can change after this and restart the node
Type 'Y' or 'y' to continue:
```

# Setup XDC Masternode using One-Click Installer

To Setup XDC Masternode using One-Click Installer, [refer](./masternode.md/#setup-xdc-masternode-using-one-click-installer)