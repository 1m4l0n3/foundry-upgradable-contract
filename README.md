# Foundry Upgradable Contract Project

## Overview

This project demonstrates the implementation of upgradable smart contracts using the Foundry framework. The project focuses on deploying an initial version of a contract (`BoxV1`) and upgrading it to a new version (`BoxV2`) while maintaining state continuity. This approach ensures that contract functionalities can evolve without disrupting existing deployments or requiring redeployment.

## Key Features

- **Upgradable Smart Contracts**: Implements proxy-based upgradability to allow seamless upgrades of contract logic.
- **Versioned Contracts**: Two versions of the `Box` contract, each introducing specific features and functionalities.
- **Deployment and Upgrade Automation**: Scripts for deploying the initial version and upgrading to the new version of the contract.
- **State Preservation**: Ensures that data stored in the contract remains intact during upgrades.

## Contracts and Scripts

### BoxV1.sol

The initial version of the `Box` contract. Key functionalities include:

- **`store(uint256 newValue)`**: Stores a new value in the contract.
- **`retrieve()`**: Retrieves the stored value, allowing users to access the current state.

### BoxV2.sol

The upgraded version of the `Box` contract, extending `BoxV1` with additional functionality:

- **`increment()`**: Increments the stored value by 1, adding more utility to the contract while retaining the existing state and methods.

### DeployBox.s.sol

A deployment script that automates the process of:

1. Deploying the proxy contract.
2. Deploying the initial implementation (`BoxV1`).
3. Setting up the proxy to delegate calls to `BoxV1`.

This script ensures the initial deployment is ready for use and upgradable.

### UpgradeBox.s.sol

A script that automates the upgrade process. It performs the following:

1. Deploys the upgraded implementation (`BoxV2`).
2. Updates the proxy to point to the new implementation.
3. Ensures the state from `BoxV1` is preserved and accessible in `BoxV2`.


## Usage

### Build

```shell
$ forge build
```

### Test

```shell
$ forge test
```

### Format

```shell
$ forge fmt
```

### Deploy

```shell
$ forge script script/DeployBox.s.sol --rpc-url <RPC_URL> --private-key <PRIVATE_KEY> --broadcast
$ forge script script/UpgradeBox.s.sol --rpc-url <RPC_URL> --private-key <PRIVATE_KEY> --broadcast
```

### Summery :
This project showcases the benefits of contract upgradability, enabling flexibility and scalability while preserving data integrity. For additional insights into implementing and managing upgradable contracts, consider exploring proxy patterns like Transparent Proxy and UUPS Proxy.