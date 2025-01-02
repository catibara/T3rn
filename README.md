# T3rn Executor Setup Guide
**This guide shows how to install and run the t3rn Executor on a Linux environment. It assumes a Debian- or Ubuntu-based operating system.**

## Table of Contents
1. [Installation Steps](#installation-steps)
2. [Configuration](#configuration)
3. [Launching the Node](#launching-the-node)
4. [Bridging Sepolia ETH](#bridging-sepolia-eth)
5. [Stay Updated](#stay-updated)

## Installation Steps

__1. Update and Upgrade__

```bash
sudo apt update
sudo apt upgrade

```
__2. Intall curl and tar__ (if not already installed)

```bash
sudo apt install curl tar
```

__3. Install Screen__ (if not already installed)

```bash
sudo apt install screen
```

__4. Create a Screen Session__ 

```bash
screen -S t3rn
```

__5. Install the t3rn Binary__

```bash
LATEST_VERSION=$(curl -s https://api.github.com/repos/t3rn/executor-release/releases/latest | grep 'tag_name' | cut -d\" -f4)
EXECUTOR_URL="https://github.com/t3rn/executor-release/releases/download/${LATEST_VERSION}/executor-linux-${LATEST_VERSION}.tar.gz"
curl -L -o executor-linux-${LATEST_VERSION}.tar.gz $EXECUTOR_URL

tar -xzvf executor-linux-${LATEST_VERSION}.tar.gz
rm -rf executor-linux-${LATEST_VERSION}.tar.gz
cd executor/executor/bin
```

## Configuration
__1. Set Environment Variables__

```bash
export NODE_ENV=testnet
export LOG_LEVEL=debug
export LOG_PRETTY=false
export EXECUTOR_PROCESS_ORDERS=true
export EXECUTOR_PROCESS_CLAIMS=true
```

__2. Set Your Private Key__

Replace __Private_key_from_EVM_wallet__ with your private key:

```bash
export PRIVATE_KEY_LOCAL=Private_key_from_EVM_wallet
```
__3. Select Networks to Enable__

```bash
export ENABLED_NETWORKS='base-sepolia,blast-sepolia,optimism-sepolia,l1rn'

```

__4. Set RPC Endpoints__

To get free private RPCs, check out the websites below:

1. [drpc.org](https://drpc.org/)
2. [ankr.com](https://www.ankr.com/)


Examples of setting custom RPC endpoints:

__* Arbitrum Sepolia__ (example URLs)
```bash
export RPC_ENDPOINTS_ARBT='https://url1.io,https://url2.io'
```

__* Base Sepolia__
```bash
export RPC_ENDPOINTS_BSSP='add your rpc here'
```

__* Blast Sepolia__
```bash
export RPC_ENDPOINTS_BLSS='add your rpc here'
```
__* Optimism Sepolia__
```bash
export RPC_ENDPOINTS_OPSP='add your rpc here'
```

__To use the private RPC, turn off processing pending orders from the API by running:__

```bash
export EXECUTOR_PROCESS_PENDING_ORDERS_FROM_API=false
```

**Important**: Before running the Executor, make sure you have:

- **Sufficient Sepolia ETH** across all enabled chains (at least 20 Sepolia ETH on each chain is recommended for a smooth experience).
- A **minimum of 1 BRN** on the BRN chain.

You can earn BRN by bridging assets via the [t1rn Bridge](https://bridge.t1rn.io/).  
Just make a transaction between any network on that page to get BRN.

## Launching the Node

```bash
./executor
```

- To detach from the screen:  Ctrl + A, then D
- To reattach to the screen session: 
```bash
screen -r t3rn
```


## Bridging Sepolia ETH

If you already have Sepolia ETH on the **Sepolia chain**, you can bridge it to other chains using the following links:

- **Sepolia → Arbitrum Sepolia**: [Arbitrum Bridge](https://bridge.arbitrum.io/?destinationChain=arbitrum-sepolia&sourceChain=sepolia)
- **Sepolia → Base Sepolia**: [Superbridge (Base Sepolia)](https://superbridge.app/base-sepolia)
- **Sepolia → Optimism Sepolia**: [Superbridge (OP Sepolia)](https://superbridge.app/op-sepolia)
- **Sepolia → Blast Sepolia**: Send ETH to **`0xc644cc19d2a9388b71dd1dede07cffc73237dca8`**


## Stay Updated

- Follow [t3rn_io on X (Twitter)](https://x.com/t3rn_io) and join the [t3rn Discord](https://discord.com/invite/S5kHFQTtp6) for the latest updates.

- If you found this guide helpful, you can follow me on [X (Twitter)](https://x.com/0xcatibara) for more guides!



