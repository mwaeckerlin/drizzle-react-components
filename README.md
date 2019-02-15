# drizzle-react-components
A set of useful components for common UI elements.

## Components

We provide components that support the React 16.3+ context and also the legacy context . The legacy context components will be deprecated in 2.0 with breaking changes in the `drizzle-react-components` API.

Currently this is how you import them:

### React 16.3+ Context Components

```
import { newContextComponents } from "drizzle-react-components";
const { AccountData, ContractData, ContractForm } = newContextComponents;
```

Note that `LoadingContainer` is not provided with the new context components.

### Legacy Context Components

```
import {
  AccountData,
  ContractData,
  ContractForm,
  LoadingContainer
} from "drizzle-react-components";
```

Refer to the included [test apps](#test-apps) for usage examples.

### LoadingContainer (Legacy only)

This component wraps your entire app (but within the DrizzleProvider) and will show a loading screen until Drizzle, and therefore web3 and your contracts, are initialized.

`loadingComp` (component) The component displayed while Drizzle initializes.

`errorComp` (component) The component displayed if Drizzle initialization fails.

### ContractData

`contract` (string, required) Name of the contract to call.

`method` (string, required) Method of the contract to call.

`methodArgs` (array) Arguments for the contract method call. EX: The address for an ERC20 balanceOf() function. The last argument can optionally be an options object with the typical form, `gas` and `gasPrice` keys.

`hideIndicator` (boolean) If true, hides the loading indicator during contract state updates. Useful for things like ERC20 token symbols which do not change.

`toUtf8` (boolean) Converts the return value to a UTF-8 string before display.

`toAscii` (boolean) Converts the return value to an Ascii string before display.

### ContractForm

`contract` (string, required) Name of the contract whose method will be the basis the form.

`method` (string, required) Method whose inputs will be used to create corresponding form fields.

`sendArgs` (object) An object specifying options for the transaction to be sent; namely: `from`, `gasPrice`, `gas` and `value`. Further explanataion of these parameters can be found [here in the web3 documentation](https://web3js.readthedocs.io/en/1.0/web3-eth-contract.html#id19).

`labels` (array) Custom labels; will follow ABI input ordering. Useful for friendlier names. For example "_to" becoming "Recipient Address".

## Test Apps

A test app targeting the React 16.3+ context API has been included at `./test-app`. And one targeting the legacy context API can be found at `test-app-legacy-context`.

### Installation

1. `cd ./test-app`
1. Install dependencies: `npm install`
1. Start your development blockchain: `truffle develop`
1. (In Truffle develop console) Compile contracts: `compile` 
1. (In Truffle develop console) Migrate contracts: `migrate`
1. In another terminal window: `cd ./app`
1. Install dependencies: `npm install`
1. Start dev server: `npm start`

NOTE: Make sure to `migrate --reset` your contracts and reset your Metamask account when switching between test apps, otherwise errors may occur.

