# vault-near-controller

## Install

`npm install --save @getsafle/vault-near-controller`

## Initialize the Near Controller class

```
const controller = require('@getsafle/vault-near-controller');

const nearController = new controller({
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
const keyringState = await nearController.createNewVaultAndKeychain(password);
```

### Restore a keyring with the first account using a mnemonic

```
const keyringState = await nearController.createNewVaultAndRestore(password, mnemonic);
```

### Add a new account to the keyring object

```
const keyringState = await nearController.addNewAccount(keyringObject);
```

### Export the private key of an address present in the keyring

```
const privateKey = await nearController.exportAccount(address);
```

### Sign a transaction

```
const signedTx = await nearController.signTransaction(nearTx, _fromAddress);
```

### Sign a message

```
const signedMsg = await nearController.signMessage(msgParams);
```

### Sign Typed Data (EIP-712)

```
const signedData = await nearController.signTypedMessage (msgParams);
```
