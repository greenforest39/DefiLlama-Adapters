## DeFi Pool Router Contract

**PoolRouter** contract allows users to interact with different DeFi liquidity pools.

Following protocols are supported:

- **GMX(v1)**: Buy GLP with single asset.
- **HMX**: Buy HLP.

## How to add new pools

You can create new `Adapter` contract for a new pool.

In the `interfaces` directory, there's `IAdapter` interface.

You should inherit the `IAdapter` interface and complete all the functions specified within the interface.

You can check how I implemented `GmxAdapter` and `HmxAdapter`.

After creating a new `Adapter` contract, you should register it on the `PoolRouter` contract by calling `addAdapter()` function.

**NOTES**: Adapter contracts are `delegatecall`-ed by our main cointract - `PoolRouter`, and thus you shouldn't define any storage variables. Use constants for protocol specific addresses/values.

## Project structure

```
├── src
│   ├── adapters
│   │   ├── GmxAdapter.sol
│   │   └── HmxAdapter.sol
│   └── PoolRouter.sol
└── test
    ├── PoolRouter.GMX.t.sol
    └── PoolRouter.HMX.t.sol
```

## Usage

### Build

```shell
$ forge build
```

### Test

```shell
$ forge test
```
