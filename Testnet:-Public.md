* [Overview](#overview)
* [Differences between Testnet and Mainnet](#differences-between-testnet-and-mainnet)
* [Nodes](#nodes)
* [Public Testnet Endpoints](#public-testnet-endpoints)
* [Connecting Local EOSD with Public Testnet](#connecting-local-eosd-with-public-testnet)
* [Connecting Local EOSC with Public Testnet](#connecting-local-eosc-with-public-testnet)
* [Testnet Accounts](#accounts-on-testnet)
* [External Links](#external-links)

## Overview
The Public Testnet exists to support developers and testers who are already working with their own standalone (private) testnet and who want to test their code on a public net, but without the issues and restrictions of working on a public production net ("mainnet").

The Public Testnet allows developers to work with free test tokens, provided during signup. Access the signup page [here](https://docs.google.com/forms/d/e/1FAIpQLSel3HVFb22zYaAJfUtu_IzFgIJ4OATb0jQ3H2FV-HbwnJ090g/viewform).

## Differences between Testnet and Mainnet
There are several differences between the Public Testnet and the public Mainnet. As of this writing, they include:
* **Existence**. The public mainnet doesn't exist yet, and the public testnet does.
* **Genesis block**. The mainnet genesis block is different from the testnet genesis block. The Testnet genesis block includes a faucet account and several "initx" accounts (inita - initu) used by the core development team during testing. At least some of these `initx` accounts are also present in the provided genesis block of standalone private testnets.
* **Resets**. The Testnet is subject to resets as needed to support testing.
* **Versions**. The Testnet can actually include multiple testnets with different addresses and different reset cycles, depending on the needs and desires of the development community.
* **Hosting**. The Testnet is currently configured such that block-producing nodes will only be run on hosts set up and operated by the core developers. The Mainnet's block producing nodes will run on hosts selected by a vote of the token holders. 

## Nodes
The Testnet consists of block-producing nodes and non-producing nodes. 

## Public Testnet Endpoints
The following is the list of currently available Public Testnets:
- Testnet1
    - HTTP Endpoint: testnet1.eos.io
    - P2P Endpoint:  p2p-testnet1.eos.io:9876
    - Web Wallet Endpoint: t1wallet.eos.io, t1api.eos.io, t1readonly.eos.io

You can test the connection using `curl`
```bash
$ curl testnet1.eos.io/v1/chain/get_info
```

## Connecting Local EOSD with Public Testnet

In order to connect your local eosd to the public testnet, ensure your machine's clock is accurate and you need to modify your `config.ini` as the following:
- Add `p2p-peer-address` field with one of the valid public testnet p2p endpoint
```
p2p-peer-address = p2p-testnet1.eos.io
```
- Modify `block-interval-seconds` to match the testnet, which is 2. Otherwise, your local eosd node won't be able to sync with the public testnet.
```
block-interval-seconds = 2
```

## Connecting Local EOSC with Public Testnet

You can connect your local eosc with public testnet by using the http endpoint as the hostname and port 80:
```bash
$ eosc -H ${http_endpoint} -p 80 ${options} ${subcommand}
```
Furthermore, public testnet does not provide any wallet functionality. In order to be able to sign transaction/ push transaction/ wallet operation, you will need to connect your local wallet with eosc when you are connecting to public testnet.
To do so, ensure that you have your local wallet running.
```
$ eos-walletd
# this will create a data-dir folder inside your current working directory, this data-dir folder will contain your private keys encrypted with the wallet password
```
Then specify your local wallet endpoint and port when using eosc, unless you override it, wallet_endpoint will be `localhost` and wallet_port will be `8888`.
```
$ eosc -H ${http_endpoint} -p 80 ${options} --wallet-host ${wallet_endpoint} --wallet-port ${wallet_port} ${subcommand}
```

# Accounts on Testnet

Before you begin first you'll need your account name and EOS public key handy.

- Discover your account name
    - Find your account name(s) assigned in genesis by entering the ETH address or EOS Public Key you believe is included in the snapshot into the [Account Name Lookup](https://eosio.github.io/genesis/tools/account-name/index.html) tool
    - If your address is not included in the snapshot, [apply for a faucet account](https://goo.gl/forms/ileHa9h6E7MLLgey1)
- Get your EOS public key ready
    - _If you're in the snapshot,_ your EOS Public Key is the key you registered with the EOSCrowdsale contract
    - _If you applied for an account through the faucet,_ your EOS public key is the key you submitted in the faucet account application

Once you have your account name, you can choose how you would like to interact with EOS. 

## Web Wallet (End Users)

- Visit the [Testnet Web Wallet](https://t1wallet.eos.io/)
- Create an account
- Login
- Click on 'Accounts' in the sidebar
- In the _Account_ input enter the account you acquired in the previous steps.
- In the EOS _Active Key_ and _Owner Key_ fields enter your EOS public key(s)
- Click "Add Account" 

## Command Line (Developers)

1. You'll need the `eos-walletd` and `eosc` binary from recent `eosd` build, see [Local Environment](https://github.com/EOSIO/eos/wiki/Local-Environment)
2. Connect to [Public Testnet](https://github.com/EOSIO/eos/wiki/Testnet:-Public)
3. [Import your private key to the wallet](https://github.com/EOSIO/eos/wiki/Command%20Reference#import-key-to-wallet) with `eosc` 
4. Learn how to use `eosc` by either figuring it out yourself with the [command reference](https://github.com/EOSIO/eos/wiki/Command-Reference) or be guided through the process with a [tutorial](https://github.com/EOSIO/eos/wiki/Tutorials#1-accounts--wallets). The choice is yours. 

