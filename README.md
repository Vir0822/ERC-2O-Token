# ERC-2O Token

A minimal ERC-20 token smart contract written in Solidity. This project demonstrates how to create a token with OpenZeppelin's `ERC20` implementation and a fixed initial supply.

## Overview

`CryptoReal` creates the token during deployment and assigns the entire initial supply to the wallet that deploys the contract.

| Property | Value |
| --- | --- |
| Contract | `CryptoReal` |
| Standard | ERC-20 |
| Solidity | `0.8.24` |
| Initial supply | `1,000` tokens |
| Decimals | `18` |
| Initial holder | Deployer (`msg.sender`) |
| Supply model | Fixed after deployment |

The token name and symbol are provided as constructor arguments, so they can be selected when deploying the contract.

## Features

- Standard ERC-20 transfers between wallets
- Allowances through `approve`, `allowance`, and `transferFrom`
- Configurable token name and symbol at deployment time
- Fixed initial supply of `1,000` tokens
- No owner, admin, or additional minting mechanism

## Contract

The implementation is in [`ERC-2O Token/CryptoReal.sol`](ERC-2O%20Token/CryptoReal.sol).

```solidity
constructor(string memory name_, string memory symbol_)
    ERC20(name_, symbol_)
{
    _mint(msg.sender, 1000 * 1e18);
}
```

Because the contract inherits OpenZeppelin's `ERC20`, the standard metadata and token operations are available through the inherited interface.

## Deploy with Remix

1. Open [Remix IDE](https://remix.ethereum.org/).
2. Create a file named `CryptoReal.sol` and paste in the contract source.
3. Install or make available the `@openzeppelin/contracts` dependency used by the import.
4. In **Solidity Compiler**, select version `0.8.24` and compile the contract.
5. Open **Deploy & Run Transactions** and choose an environment such as **Remix VM** for local testing or **Injected Provider** for a connected wallet.
6. Enter the token name and symbol, for example `Crypto Real` and `CRL`.
7. Deploy the contract and inspect the deployed instance to call transfers and allowance functions.

## Example deployment values

```text
Name: Crypto Real
Symbol: CRL
Initial supply: 1,000 CRL
```

The deployer's balance is `1,000 * 10^18` base units. Wallet interfaces normally display this as `1,000 CRL` because the token uses 18 decimals.

## Available ERC-20 operations

The inherited OpenZeppelin implementation exposes the usual ERC-20 functions, including:

- `name()` and `symbol()`
- `decimals()`
- `totalSupply()`
- `balanceOf(address)`
- `transfer(address, uint256)`
- `approve(address, uint256)`
- `allowance(address, address)`
- `transferFrom(address, address, uint256)`

## Important notes

- The full initial supply is minted once in the constructor.
- There is no public or owner-only function to mint more tokens.
- The contract has no pause, blacklist, tax, fee, or upgradeability features.
- This project is educational and has not been presented as a production-ready financial product. Review and test the code before deploying it to a public network.

## License

The source file declares the `LGPL-3.0-only` license. See the SPDX identifier in [`ERC-2O Token/CryptoReal.sol`](ERC-2O%20Token/CryptoReal.sol).
