---
title: Wallet Swap JSON RPC Method
description: A new JSON RPC method for dapps to request the wallet to perform a token swap.
author: Tomás Santos (@tommasini)
discussions-to: <URL>
status: Draft
type: Standards
category: Interface
created: 2023-10-27
---

<!--
  READ EIP-1 (https://eips.ethereum.org/EIPS/eip-1) BEFORE USING THIS TEMPLATE!

  This is the suggested template for new EIPs. After you have filled in the requisite fields, please delete these comments.

  Note that an EIP number will be assigned by an editor. When opening a pull request to submit your EIP, please use an abbreviated title in the filename, `eip-draft_title_abbrev.md`.

  The title should be 44 characters or less. It should not repeat the EIP number in title, irrespective of the category.

  TODO: Remove this comment before submitting
-->

## Abstract

This EIP proposes a new JSON RPC method wallet_swap that allows dapps to request the wallet to perform a token swap operation. The method takes in parameters for the source and destination tokens and initiates a token swap operation in the wallet.

## Motivation

The motivation behind this EIP is to provide a standardized way for dapps to request token swaps from wallets, improving interoperability and user experience.

## Specification

The new JSON RPC method wallet_swap should be implemented with the following parameters:

- from: An object containing details about the source token. It should include:

  - token_address: The address of the source token.
  - chainId: The chain ID in hexadecimal format where the source token resides.
  - amount: The amount on wei in hexadecimal format of source token to be swapped.

- to: An object containing details about the destination token. It should include:
  - token_address: The address of the destination token.
  - chainId: The chain ID in hexadecimal format where the destination token resides.

The wallet should interpret the method call and perform the necessary validations and operations to initiate the token swap.

## Rationale

This EIP provides a standardized way for dapps to request token swaps, which can improve user experience by allowing users to perform swaps without leaving the dapp. It also improves interoperability by providing a standard that different wallets can implement.

## Backwards Compatibility

No backward compatibility issues found.

## Test Cases

Test cases should be created to ensure the wallet_swap method correctly initiates a token swap when valid parameters are provided, and returns appropriate errors when invalid parameters are provided.

1. Valid parameters: The wallet_swap method should correctly initiate a token swap when valid from and to parameters are provided.

2. Invalid token address: The wallet_swap method should return an appropriate error when an invalid token address is provided in either the from or to parameters.

3. Invalid chainId: The wallet_swap method should return an appropriate error when an invalid chainId is provided in either the from or to parameters.

4. Mismatched chainId: The wallet_swap method should return an appropriate error when the chainId in the from and to parameters do not match.

5. Invalid amount: The wallet_swap method should return an appropriate error when an invalid amount is provided in the from parameter.

6. Unsupported chain: The wallet_swap method should return an appropriate error when a token swap is requested on an unsupported chain.

7. Swaps not allowed: The wallet_swap method should return an appropriate error when a token swap is requested but swaps are not allowed or not active on the specified chain.

## Reference Implementation

The implementation of this EIP requires changes to the wallet to support the new wallet_swap method. The wallet should validate the parameters, check the chain ID and token addresses, and initiate the token swap operation.

## Security Considerations

Security considerations include ensuring that the token addresses and chain IDs are valid, and that the requested swap operation does not lead to any unexpected behavior or loss of funds. The wallet should also handle any errors or exceptions gracefully and provide clear error messages.

## Copyright

Copyright and related rights waived via [CC0](../LICENSE.md).
