# Bitcoin and Security
Presentation on Bitcoin and security for Kharagpur Open Source Society.

- Note: It is recommended to use MS powerpoint for compatability and to run integrated videos.

## Content of the presentation
- Cryptography
- How Cryptography works
- Symmetric Key Cryptography
- Symmetric Key Cryptography in action
- Asymmetric Key Cryptography
- Asymmetric Key Cryptography in action
- Asymmetric Key algorithms
- RSA  Encryption Algorithm  and its mechanism
- Symmetric and Asymmetric unison
- Digital signatures
- Bitcoin wallets
- Types of Bitcoin wallets
- Pros and Cons of Hot and Cold wallets
- Bitcoin Transactions and UTXO model
- Bitcoin wallet Balance
- How a Transaction is done: Application of Digital signatures on Bitcoin transactions
- Hierarchical Deterministic Wallets
- Best ways to secure Crypto wallets

## How to run a full node on your Laptop
#### Note: make sure the you have free disk space of atleast 600GB to run as a full node.


- Clone the source code of the bitcoin repository from github
```
$ git clone https://github.com/bitcoin/bitcoin.git
```
- Move into the cloned directory
```
$ cd ./bitcoin/
```
- Check for the latest version of the repository. the version with 'rc' as their suffix are made for testing purposes
```
$ git tag
```
- Move into the version branch you intended to go
```
$ git checkout v24.1
```
Now we are at the intended version to setup bitcoin-core

- Run the `autogen.sh` executable file to start the setup
```
$ ./autogen.sh
```

- Run the `./configure` file [you can add a prefix flag to install it on your intented destination] otherwise the default install installation location will be `/usr/local/bin/` directory

```
$ ./configure --prefix=/home/swaraj/Download/bitcoin/
```
- Look for a configuration file which is probably present in `~/.bitcoin/` directory. If you donot find the directory create one and create the file bitcoin.conf.
```
$ mkdir ~/.bitcoin
$ cd ~/.bitcoin && touch bitcoin.conf
```
- Add this content to the file and save it
```
datadir=/lotsofspace/bitcoin
txindex=1
```
here the line `/lotsofspace/bitcoin` represents represents the path to the directory where you want to store the whole bitcoin data.

- Now we are done with the configuration now to run our node to start syncing with the mainnet.

```
$ bitcoind -printtoconsole
```
Note: remember the syncing will take a lot of time. You can stop and resume anytime you want to.

You can perform any task you want after running the syncing process to using bitcoin-cli. Run
```
$ bitcoin-cli --help
```

## How to run Bitcoin regtest
This tutorial is completely independent from `How to run a full node on your laptop` and goes through fresh installation and setup.
- Download [bitcoin-core](https://bitcoincore.org/en/download/)
- Extract it into a suitable directory
- Move into the project directory `(bitcoin-$version)`
- Open the directory on terminal
- Run the following. and the save the output to any backup. we will need it in future.
```
$ python ./share/rpcauth/rpcauth.py <YOURUSERNAME>
```
- Create a `.bitcoin` directory on `$HOME`.
```
$ mkdir ~/.bitcoin
```
- Create a data directory where blockchain data needs to be stored
```
$ mkdir ~/.bitcoin/data
```
- Create a configuration file `bitcoin.conf` on `.bitcoin` directory
```
$ touch ~/.bitcoin/bitcoin.conf
```
- Add these lines to the file and add the `rpcuser`, `rpcpassword` and `rpcauth` from the backup you created and save it.
```
# Run Bitcoin as in daemon mode without an interactive shell
daemon=1
# Tell Bitcoin where to put blockchain data
datadir=/path/to/my/blockchain/data/.bitcoin/data
# Tell Bitcoin to run on a regtest network
regtest=1
# Set the RPC from the output generated
rpcauth=<USERNAME>:...
rpcuser=<YOURUSERNAME>
rpcpassword=<PASSWORD>
# Turn on the RPC server
server=1
```
- now run the `bitcoind` executable which is present on the downloaded bitcoin core directory
```
$ bitcoin-$version/bin/bitcoind
```
Our blockchain is started running on background

- create a new wallet where you will manage all your transactions
```
$ bitcoin-$version/bin/bitcoin-cli createwallet "WALLETNAME"
```

- Generate a new address and some blocks to add some balance to your account
```
$ bitcoin-$version/bin/bitcoin-cli -generate 101
```
Now we have a functioning blockchain and a member, here we can add multiple nodes and transfer transactions.

Note: Below link is not for setup as it seems outdated to me but you can follow it after setting up by following my tutorial.
- [Know More on what to do after setup](https://gist.github.com/System-Glitch/cb4e87bf1ae3fec9925725bb3ebe223a)


## Author
 - Swaraj Kumar Biswal (22BT10033)

## References
- [RSA encryption](https://link-url-here.org)
- [Digital Signatures](https://www.youtube.com/watch?v=JR4_RBb8A9Q)
- [Bitcoin Wallets](https://101blockchains.com/crypto-wallets/)
- [Hot wallets and Cold wallets](https://www.investopedia.com/hot-wallet-vs-cold-wallet-7098461#:~:text=Hot%20and%20cold%20wallets%20are%20the%20primary%20means%20of%20storing,such%20as%20a%20USB%20stick.)
- [Blockchain course](https://www.youtube.com/watch?v=6aF6p2VUORE&t=18915s)
- [How to run Bitcoin regtest](https://gist.github.com/System-Glitch/cb4e87bf1ae3fec9925725bb3ebe223a)
- [Blockchain full node tutorial](https://www.youtube.com/watch?v=rsicnI86QqE&t=272s)
- [Running a full node](https://github.com/bitcoinbook/bitcoinbook/blob/develop/ch03.asciidoc)
- [Regtest tutorial](https://gist.github.com/System-Glitch/cb4e87bf1ae3fec9925725bb3ebe223a)
- [Setting up your own wallet](https://github.com/BlockchainCommons/Learning-Bitcoin-from-the-Command-Line/blob/master/03_3_Setting_Up_Your_Wallet.md)
