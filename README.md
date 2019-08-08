# crytjs
Small collection of JavaScript functions for CRYT. Allows for local signing of transactions, token creation/validation and encryption/decryption of arbitrary messages.

### Usage    
##### Browser:

Use in HTML file:

    <script src="nxtjs.js"></script>
    <script>
        var acc = nxtjs.secretPhraseToAccountId('secret');
        console.log(acc);
    </script>

### Functions
#### secretPhraseToPublicKey(secretPhrase)
Returns public key of a given passphrase

#### publicKeyToAccountId(publicKey, numeric)
Returns account ID of a given public key. Set the second parameter to true to
get numeric account ID instead of RS format

#### secretPhraseToAccountId(secretPhrase, numeric)
Returns account ID of a given passphrase.  Set the second parameter to true to
get numeric account ID instead of RS format.

#### signTransactionBytes(unsignedTransactionBytes, secretPhrase)
Signs a hex string of unsigned transaction bytes (e.g. as received from CRYT API)
with the provided passphrase and returns it.

#### createToken(string, secretPhrase)
Generates a CRYT cryptographic token

#### parseToken(token, string)
Parses a CRYT cryptographic token. Returns an object with the keys `isValid`,
`timestamp`, `publicKey` and `accountRS`.

#### encryptMessage(plainText, recipientPublicKey, senderSecretPhrase)
Returns an object with the keys `nonce` and `message`

#### decryptMessage(cipherText, nonce, senderPublicKey, recipientSecretPhrase)
Returns the deciphered text as string

#### rsConvert(address)
Converts address in numeric format to Reed-Solomon format, or vice versa. Returns an object with the keys `account` and `accountRS`


### Credits
The purpose of this repo is to consolidate code from multiple sources into one easy to use package for node.js and the browser.
