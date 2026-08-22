# ERC-2O Token

![Solidity](https://img.shields.io/badge/Solidity-0.8.24-363636?logo=solidity)
![Standard](https://img.shields.io/badge/Standard-ERC--20-627eea?logo=ethereum)
![License](https://img.shields.io/badge/License-LGPL--3.0--only-blue)

A compact ERC-20 token implementation built with Solidity and OpenZeppelin. The project focuses on the core mechanics of token creation, standard wallet transfers, and allowance-based spending through a deliberately small and easy-to-review contract.

## Project Highlights

- Implements the ERC-20 standard by extending OpenZeppelin's battle-tested `ERC20` contract.
- Accepts the token name and symbol as deployment parameters.
- Mints a fixed supply of 1,000 tokens to the deployer's address during construction.
- Keeps the permission model intentionally minimal: there is no owner, admin role, or post-deployment minting function.

## Technical Summary

| Item | Details |
| --- | --- |
| Contract | `CryptoReal` |
| Token standard | ERC-20 |
| Solidity | `^0.8.24` |
| Initial supply | `1,000` tokens |
| Decimals | `18` (provided by OpenZeppelin) |
| Initial recipient | `msg.sender` |
| Dependency | `@openzeppelin/contracts` |
| Development tool | [Remix IDE](https://remix.ethereum.org/) |

## How It Works

At deployment, the constructor forwards the chosen name and symbol to OpenZeppelin's ERC-20 implementation and mints the initial supply to the deployer:

```solidity
constructor(string memory name_, string memory symbol_)
    ERC20(name_, symbol_)
{
    _mint(msg.sender, 1000 * 1e18);
}
```

The value `1e18` represents the contract's 18 decimal places. As a result, the deployer receives `1,000` display tokens, represented internally as `1,000 * 10^18` base units.

## ERC-20 Interface

The contract inherits the standard metadata, balance, transfer, and allowance functionality from OpenZeppelin:

- `name()` and `symbol()`
- `decimals()` and `totalSupply()`
- `balanceOf(address)`
- `transfer(address, uint256)`
- `approve(address, uint256)`
- `allowance(address, address)`
- `transferFrom(address, address, uint256)`

## Deployment With Remix

1. Open [Remix IDE](https://remix.ethereum.org/).
2. Create `CryptoReal.sol` and copy the source from [`ERC-2O Token/CryptoReal.sol`](ERC-2O%20Token/CryptoReal.sol).
3. Make the `@openzeppelin/contracts` dependency available in the Remix workspace.
4. Compile with a compatible Solidity compiler version, such as `0.8.24`.
5. Open **Deploy & Run Transactions** and select **Remix VM** for local testing or **Injected Provider** for a connected wallet.
6. Provide a token name and symbol, for example `Crypto Real` and `CRL`.
7. Deploy the contract and interact with the inherited ERC-20 functions.

### Example Parameters

```text
Name: Crypto Real
Symbol: CRL
Initial supply: 1,000 CRL
```

## Scope and Limitations

This is a focused educational project and is not presented as a production-ready financial product. The contract does not include:

- Additional minting or burning controls
- Ownership or administrative roles
- Pausing, blacklisting, fees, or transfer taxes
- Upgradeability

The repository currently contains the contract source and does not include an automated test suite or deployment script. Review and test the code independently before deploying it to a public network.

## License

The contract is released under the `LGPL-3.0-only` license, as declared by its SPDX identifier.
