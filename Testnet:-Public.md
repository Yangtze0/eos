# Public Testnet: Dawn 2.0

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
There are currently two Public Testnet.
- Testnet1
    - HTTP Endpoint: testnet1.eos.io
    - P2P Endpoint: t1p2pXX.eos.io where XX is ranging from 01-21
    - Web Wallet Endpoint: t1wallet.eos.io, t1api.eos.io, t1readonly.eos.io
- Testnet2
    - HTTP Endpoint: testnet2.eos.io
    - P2P Endpoint: t2p2pXX.eos.io where XX is ranging from 01-21
    - Web Wallet Endpoint: t2wallet.eos.io, t2api.eos.io, t2readonly.eos.io

You can test the connection either using `curl`
```bash
$ curl testnet1.eos.io/v1/chain/get_info
```

## Connecting Local EOSD with Public Testnet
In order to connect your local eosd to the public testnet, ensure your machine's clock is accurate and you need to modify your `config.ini` as the following:
- Add `p2p-peer-address` field with one of the valid public testnet p2p endpoint
```
p2p-peer-address = ${p2p_endpoint}
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
# Accounts on Testnet

## I Have a Key in the Testnet Genesis Block

You're golden, instructions below 

1. An `eos-walletd` and `eosc` binary from recent `eosd` build, see [Local Environment](https://github.com/EOSIO/eos/wiki/Local-Environment)
2. Connect to [Public Testnet](https://github.com/EOSIO/eos/wiki/Testnet:-Public)
3. [Import your private key](https://github.com/EOSIO/eos/wiki/Command%20Reference#import-key-to-wallet) with `eosc`

## I DO NOT Have a Key in the Testnet Genesis Block

If you do not have a genesis allocation, [please apply for an account](https://goo.gl/forms/ileHa9h6E7MLLgey1) through the faucet

## External Links
### Wallets
Online test wallets you can use to help you with development:
* name [link]

### Faucet
Initial tokens for testing (provided by a "faucet") are given to you when you sign up for a Public Testnet account. You can also request tokens from other developers, and give yours to them. When done with testing, please return your tokens to the Testnet faucet account using the instructions here [link].