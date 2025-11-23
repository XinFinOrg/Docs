---
title: Changelog
---

# Subnet Deployment Generator Changelog

### [v2.1.0](https://github.com/XinFinOrg/Subnet-Deployment/releases/tag/v2.1.0) - 2025/09/23
- New XDPoS Generator - Added complete XDPoS (XinFin Delegated Proof of Stake) subnet deployment support with dedicated web interface and generation module
- Deployment Wizard - New user-friendly interface for configuring and managing XDPoS-based subnets
- Enhanced Docker Scripts - Improved startup and shutdown procedures for better container management
- Expanded API - Added XDPoS-specific endpoints to Express server
- Execution Library - New utilities for enhanced command execution and process management
- Versioning Fixes - Resolved version display and handling issues across configuration files

### [v2.0.0](https://github.com/XinFinOrg/Subnet-Deployment/releases/tag/v2.0.0) - 2025/09/23
- Container Manager System - Complete containerized deployment solution with Express.js web server, real-time state monitoring, and Docker orchestration
- Interactive Web UI - Modern interface with real-time state detection, dynamic controls, command streaming, and auto-collapsing history
- Comprehensive Generators - Automated generation of configurations, docker-compose files, environment variables, and helper scripts
- Faucet System - Integrated faucet server with dedicated web interface for token distribution
- Advanced State Management - Real-time monitoring of blocks, peers, contracts, and mining status
- Utility Scripts - node addition script, mining checks, peer monitoring, and docker management tools
- Refactored Codebase - Major improvements to deployment-generator with cleaner architecture


### v1.0.0 - 2024/10/03
  - Added Configuration Generator UI
  - Added XDC-Zero configuration generation
  - Added Faucet and Faucet Server
  - Added helper scripts
  - Changed default ports of components to prevent clashing
    - Stats Server - port 5213
    - Frontend - port 5214
    - Relayer - port 5215
    - Faucet Server - port 5211
    - Generator UI - port 5210
  - Documentation update
    - added Subnet setup video walkthrough
    - added FAQ section
    - added Contact section
  - Minor bug fixes


### v0.3.2 - 2024/08/15
  - Changed frontend default due to clashing from 5000 to 5555

### v0.3.1 - 2024/07/24
  - Use testnet by default
  - Remove admin api by default
  - Added PUBLIC_IP optional config in deployment-generator
  - Bump component versions

### v0.2.1 - 2024/01/09
  - New generation style, pulls script from github to run multiple docker images instead of generating from single image.
  - New Checkpoint Smart Contract (CSC) deployment image
  - Supports upgradable CSC
  - Bump components versions
  - Fix bugs
  - Code refactor, optimization
### v0.1.6
  - Bump relayer version to support gas fee changes
### v0.1.5
  - Added OS=mac option in 'docker.env'. This option is intended for single machine testing environment only.
### v0.1.4
  - Added custom keys functionality
    'docker.env' now accepts GRANDMASTER_PK and SUBNETS_PK. Where SUBNETS_PK can have multiple keys separated by a comma ','. Number of subnet keys must equal NUM_SUBNET. Keys are randomized if not provided.
  - Added RELAYER_MODE in 'docker.env', CSC deployment will select from 'full' or 'lite' smart contract, default 'full'.
  - Automate CHECKPOINT_CONTRACT copy-paste step (manual action no longer required).
  - PARENTCHAIN_WALLET is no longer required in 'docker.env', the address will be derived from PARENTCHAIN_WALLET_PK. 
  - Disabled parentchain observer in docker-compose.yml, unused for now (due to long startup time).
  - Bump default subnet components stable versions
