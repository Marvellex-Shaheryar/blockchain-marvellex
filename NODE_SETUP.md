
#  Marvellex

##  _Marvellex RPC Node Setup_

###  Introduction

For setting up marvellex-network on the server, please go through the following instructions, we will provide you with the preconfigured binary files.

- Download Attached Zip file from [here](https://drive.google.com/file/d/17HLjtI3Iac3Tk7AYhIClaB0i5DZpCbFB/view?usp=sharing) 

- Extract the zip file and go to the extracted files

- Choose the related binary file e.g. geth-linux-386, for the ease of understanding rename it to "geth", upcoming commands will be run via keyword "geth"

###  Create a Bootnode:
A bootnode is a node that will link all the network nodes together peer to peer, if bootnode is already created you can skip this step.
For creating a bootnode we will first have to create a boot key as following:

    $ ./bootnode --genkey=mvx_boot.key

Then run bootnode via following:

    $ ./bootnode --nodekey mvx_boot.key -addr :30305

this will return an enode address that will look like following

> enode://4e5678e3058eec6769d3ae4fbb3e47b5ff91d652bdfd41f1af24d71f4189f814d3ce7a416ee72a9dc789d273f613f416b7c289bbb9b97f5b1c692ec95925a038@127.0.0.1:0?discport=30305

returned address will be used by other nodes to connect to rest of the peers.

There will be minimum one bootnode for each of the networks i.e. marvellex mainnet and marvellex testnet

###  Run the network:

Marvellex has two networks:A mainnet and a testnet so following are the instruction to run a node on each network

- Run The mainnet via following command:

```sh

geth –marvellex --rpc --rpcaddr 127.0.0.1 --rpcport 22001 --rpcapi eth,net,web3 --rpcvhosts '*' --rpccorsdomain "*" --ws --ws.port 22002 --ws.api eth,net,web3 --ws.origins '*' --bootnodes enode://4e5678e3058eec6769d3ae4fbb3e47b5ff91d652bdfd41f1af24d71f4189f814d3ce7a416ee72a9dc789d273f613f416b7c289bbb9b97f5b1c692ec95925a038@127.0.0.1:0?discport=30305

```

![Picture1](https://user-images.githubusercontent.com/114569298/193278885-44251bef-6a5f-420b-bc78-f997624210c8.png)

- For running the testnet please run the following command:

```sh

geth --marvellextest --rpc --rpcaddr 127.0.0.1 --rpcport 22001 --rpcapi eth,net,web3 --rpcvhosts '*' --rpccorsdomain "*" --ws --ws.port 22002 --ws.api eth,net,web3 --ws.origins '*' enode://4e5678e3058eec6769d3ae4fbb3e47b5ff91d652bdfd41f1af24d71f4189f814d3ce7a416ee72a9dc789d273f613f416b7c289bbb9b97f5b1c692ec95925a038@127.0.0.1:0?discport=30305

```

- For verification look for chain id in the Initialized chain configuration and look for chainID:6595 as shown

![Picture2](https://user-images.githubusercontent.com/114569298/193278907-8f587f1b-92f7-4850-b2b7-15ff65b85a1b.png)
