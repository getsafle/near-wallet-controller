# vault-aurora-controller

## Install

`npm install --save @getsafle/vault-aurora-controller`

## Initialize the Aurora Controller class

```
const { KeyringController, getBalance } = require('@getsafle/vault-aurora-controller');

const auroraController = new KeyringController({
  encryptor: {
    // An optional object for defining encryption schemes:
    // Defaults to Browser-native SubtleCrypto.
    encrypt(password, object) {
      return new Promise('encrypted!');
    },
    decrypt(password, encryptedString) {
      return new Promise({ foo: 'bar' });
    },
  },
});
```

## Methods

### Generate Keyring with 1 account and encrypt

```
const keyringState = await auroraController.createNewVaultAndKeychain(password);
```

### Restore a keyring with the first account using a mnemonic

```
const keyringState = await auroraController.createNewVaultAndRestore(password, mnemonic);
```

### Add a new account to the keyring object

```
const keyringState = await auroraController.addNewAccount(keyringObject);
```

### Export the private key of an address present in the keyring

```
const privateKey = await auroraController.exportAccount(address);
```

### Sign a transaction

```
const signedTx = await auroraController.signTransaction(auroraTx, _fromAddress);
```

### Sign a message

```
const signedMsg = await auroraController.signMessage(msgParams);
```

### Sign a message

```
const signedObj = await auroraController.sign(msgParams, pvtKey, web3Obj);
```

### Sign Typed Data (EIP-712)

```
const signedData = await auroraController.signTypedMessage(msgParams);
```

#### Raw transaction object

```
rawTx: {
  to, // receiver address
  from, // sender address
  value, // amount to send
  gas, // gas Limit of transaction
  gasPrice, // gasPrice
  data, // data in hex to send
  nonce, // transaction nonce
  chainId, // chainID | 1313161555 - TESTNET, 1313161554 - MAINNET
}
```

### Get balance

```
const balance = await getBalance(address, web3);
```
