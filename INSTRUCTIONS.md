# instructions
*This are minimal instructions and flow in order to get the kvartalo running in a server*

- before this document, need to have an already working geth blockchain is running
- download `web-wallet`: https://github.com/kvartalo/web-wallet from the `releases` section
- download `relay`: https://github.com/kvartalo/relay from the `releases` section
- create a `config.yaml` that for the moment will only hold the storage path value
	```
	web3:
		url: "http://web3gateway-url"
		startscanblock: 0
	storage:
		path: ./databasepath
	```

- initialize the database
```
./relay init
```

- create new keystore, where the parameter `thisisthepassword` is the password that you want to use for the keystore
```
./relay wallet new thisisthepassword
```
This will output the new `address` created and the `keystorage` path.

- put the obtained `address` and `keystorage` path in the `config.yaml`
```
keystorage:
        address: "0xaddress"
        password: "secretpassword"
        keyjsonpath: "./keystorage/keystoragepath"
server:
        Port: "portnumber"
```

- info about the relay address, eth and tokens
	- in order to check that the relay can connect to the web3 provider, and check the relay address balance
```
./relay info
```

- deploy the token smart contract
```
./relay contracts token deploy
```
This will output the token smart contract `address` and the `blocknumber` where the contract is deployed
- put the obtained token smart contract `address` into the `config.yaml`, together with all the other parameters that we already have in the file
```
keystorage:
        address: "0xaddress"
        password: "secretpassword"
        keyjsonpath: "./keystorage/keystoragepath"
server:
        Port: "portnumber"
web3:
        url: "web3gateway-url"
        startscanblock: blocknumber-where-contract-is-deployed

contracts:
        token: "0xdeployedAddr"
storage:
        path: ./databasepath
```

- now we can mint tokens that will go to the relay address
	- take in account that the units of the token represent the cents of the token, so if we want 100 tokens, we need to mint the amount of 10000 tokens
```
./relay contracts token mint [amount]
```

- transfer tokens to a specified address
	- take in account that the units of the token represent the cents of the token, so if we want to send 100 tokens, we need to send the amount of 10000 tokens
```
./relay contracts token transfer [address] [amount]
```

- start the relay server
```
./relay start
```


- now we need to deploy the wallet. Go inside the `web-wallet` directory previously downloaded
- run `npm install`
- edit the `js/constants.js` file and update the lines:
```
const RELAYURL = 'http://the.relay.server.address.and.port';
const TOKENADDR = '0xdeployedAddr';
```
- now run an http server that serves the web-wallet:
	- for example `python3 -m http.server 8080`
- and the wallet is running in the server, we can connect to it from the browser
