# Celestia Node Setup Guide (v0.20.4)

## Install Dependencies
Run the following command to install the required dependencies:
```bash
sudo apt install curl tar wget aria2 clang pkg-config libssl-dev jq build-essential git make ncdu -y
```

## Install Go
Download and install Go:
```bash
wget "https://golang.org/dl/go1.23.0.linux-amd64.tar.gz"
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf "go1.23.0.linux-amd64.tar.gz"
rm "go1.23.0.linux-amd64.tar.gz"
```

## Update the PATH
Add Go binaries to your PATH:
```bash
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile
source $HOME/.bash_profile
```

## Verify Go Installation
Check if Go is installed correctly:
```bash
go version
```

## Clone the Celestia-Node Repository
Clone the Celestia-Node repository:
```bash
cd $HOME
rm -rf celestia-node
screen -S CELESTIA
git clone https://github.com/celestiaorg/celestia-node.git
cd celestia-node/
```

## Check Out the Correct Version
Switch to the latest version (v0.20.4):
```bash
git fetch --tags
git checkout tags/v0.20.4
```

## Build and Install Celestia-Node
Build and install Celestia Node:
```bash
make build-jemalloc
make install
make cel-key
celestia version
```

## Initialize the Light Node
Initialize the Celestia light node:
```bash
celestia light init --p2p.network celestia
```

## Create a Key for the Light Node
Generate a key for the light node:
```bash
./cel-key add CHOOSE_A_NAME --keyring-backend test --node.type light --p2p.network celestia
```

## Start the Light Node with the Key
Start the light node using the created key:
```bash
celestia light start --keyring-backend test --p2p.network celestia
```

This completes the setup of a Celestia light node with version v0.20.4. Ensure your node is running correctly and syncing with the network.

