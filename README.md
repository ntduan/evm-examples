## **Migration to https://github.com/AcalaNetwork/bodhi.js/tree/master/examples**

# Acala EVM Examples

ETHDenver Workshop Link: https://www.crowdcast.io/e/acala-ethdenver-2021

This workshop is for learning to use Acala EVM. It demonstrates how to deploy a simple ERC20 contract, a complex project like Uniswap, and use the on-chain scheduler function to build a recurring payment DApp.

Read more about Acala EVM [here](https://wiki.acala.network/learn/basics/acala-evm)
Developer Guide [here](https://wiki.acala.network/build/development-guide/smart-contracts/get-started-evm)

## Run
### Start a development chain
#### Build & Run from source code

Or you can build & run from the Acala repo.

Follow the setup instruction at https://github.com/AcalaNetwork/Acala

Start the chain:

```bash
$ make run
```

Start the chain with evm compatibility mode:

```bash
$ make run-eth
```

#### Use Docker (not recommended)
You can use docker to run a development Acala Mandala chain, not recommended since docker image is not always up-to-date.

```bash
$ docker run --rm -p 9944:9944 acala/mandala-node:latest --dev --ws-external --rpc-methods=unsafe --instant-sealing  -levm=trace
```

### Build and Run Examples
install rush if not already
```
npm install -g @microsoft/rush
```
or
```
yarn global add @microsoft/rush
```

install all dependencies
```
rush update
```

compile and build all contracts
```
rushx build    # only rebuild if source file changed
rushx rebuild  # force rebuild all
```

run all tests
```
rushx test
```

build and run together
```
rushx run
```

or we can run tests for a single example:
- cd into one of the example project
  - You can find your contract ABI in the build directory. You can upload these ABI files to [acala evm playground](https://evm.acala.network/#/upload) for testing.
  - Run the tests with `rushx test`.

## Development
update dep package version for all examples
```
rush add -p <package> --all
rush add -p @acala-network/bodhi@latest --all
```

update dep package version for a single example
```
cd <project>
rush add -p <package>
```

### Tips and Docs
- `rushx` is an alternative to `yarn`, so we can also use `yarn test` instead of `rushx test`.
- The test cases are written with with [ethers.js](https://docs.ethers.io/v5/) and [waffle](https://ethereum-waffle.readthedocs.io/en/latest/).
