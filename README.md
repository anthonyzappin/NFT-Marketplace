## Overview

The Marketplace has a few dependencies for which you will need to setup an account and install software

* [Pinata](https://app.pinata.cloud/) -> Stores images uploaded by the users; store NFT metadata
    - Go to the website above and register an account.  You will need the account keys in order to setup the environment file discussed below

* [Ganache](https://trufflesuite.com/ganache/) - Ganache is a private blockchain made for testing; it allows us to run the marketplace locally
    - Go to website, download Ganache and install it

## To run the app
1. run `npm install` to install all dependencies

2. In the root folder of the application create a `.env.development` file with following content:

```
NEXT_PUBLIC_NETWORK_ID=5777
NEXT_PUBLIC_TARGET_CHAIN_ID=1337
NEXT_PUBLIC_PINATA_DOMAIN=https://gateway.pinata.cloud

SECRET_COOKIE_PASSWORD={must be 32 characters long password, can be anything}

PINATA_API_KEY={API key from pinata}
PINATA_SECRET_API_KEY={API secret key from pinata}
```
* (your api pinata key has to allow `pinFileToIPFS` and `pinJSONToIPFS` rules)

3. Migrate your contracts to Ganache, contract can be found in the `contracts` folder. It's called `NftMarket.sol`

* To migrate the contract run `truffle migrate` in the terminal while Ganache network is setup and running.

* Do not forget to link `trufle-config.js` with Ganache, just go to `config` and click `Add Project`

* `keys.json` must be created if you want to deploy to Ropsten, if not, just remove import of `keys.json` from `trufle-config.js` and also comment out `ropsten` configuration

4. Now everything is setup and you can test out the app.

* Run `npm run dev` in the terminal. App will run at `localhost:3000`

5. Download Metamask and setup

6. Once Metamask is setup, connect to Ganache

 * Connect to the Ganache Network.  
 * Click on Metamask in the browser, then click on `Add Network`
 * Enter the name of the Blockchain {Can be anything}
 * RPC URL should be grabbed from the `RPC Server` tab in Ganache
 * Chain ID is `1337`
 * Currency Symbol is `ETH`
 * Block Explorer URL is blank

 7. Add your ethereum wallet to Metamask

  * Click on Metamask
  * Click on `Import Account`
  * Copy one of the wallet addresses from Gacache into the field and click okay
  
