# symbol-sdk-browserify
This is nemtech/symbol-sdk-typescript-javascript - but browserified!  The latest sdk will always be in the root of the repo. Previous versions are held in `sdk/`. 

## Usage

```
<script src="symbol-sdk-<whatever version in the root of repo>.js"></script>
```

```js
const nem = require("/node_modules/nem2-sdk");
const rxjs = require("/node_modules/rxjs/operators");
const sha3_256 = require("/node_modules/sha3_256").sha3_256;
```

then, you can use like this.

```js
//nem sample
const alice = nem.Account.generateNewAccount(nem.NetworkType.MIJIN_TEST);

//rxjs sample
listener
.confirmed(alice.address)
.pipe(
    rxjs.filter((tx) => tx.transactionInfo !== undefined && tx.transactionInfo.hash === lockSignedTx.hash),
    rxjs.mergeMap(ignored => transactionHttp.announceAggregateBonded(signedTx))
)
.subscribe(_ => console.log(_), err => console.error(err)
);

//sha3_256 sample
const hash = sha3_256.create();

```

## Generating Bundle File Yourself

If you want to create bundle file yourself,

```
cd generator/
npm install
npm run generate-bundle
```

If you wish to compile a different version, be sure to replace the version of `symbol-sdk`, then run the above commands once more: 

```
"symbol-sdk": "Your version here"
```
