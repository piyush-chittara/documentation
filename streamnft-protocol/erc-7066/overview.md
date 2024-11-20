# Overview

[ERC-721](https://eips.ethereum.org/EIPS/eip-721) compliant contracts MAY implement this EIP to provide standard methods of locking and unlocking the token at its current owner address.

Token owner MAY `lock` the token and assign `locker` to some `address` using `lock(uint256 tokenId, address _locker)` function, this MUST set `locker` to `_locker`. Token owner or approved MAY `lock` the token using `lock(uint256 tokenId)` function, this MUST set `locker` to `msg.sender`. Token MAY be `unlocked` by `locker` using `unlock` function. `unlock` function MUST delete `locker` mapping and default to `address(0)`.

If the token is `locked`, the `lockerOf` function MUST return an address that is `locker` and can `unlock` the token. For tokens that are not `locked`, the `lockerOf` function MUST return `address(0)`.

`lock` function MUST revert if token is not already locked. `unlock` function MUST revert if token is not locked. ERC-721 `approve` function MUST revert if token is locked. ERC-721 `_tansfer` function MUST revert if token is locked. ERC-721 `_transfer` function MUST pass if token is locked and `msg.sender` is `approved` and `locker` both. After ERC-721 `_transfer`, values of `locker` and `approved` MUST be purged.

Token MAY be transferred and `locked`, and OPTIONAL setup `approval` to `locker` using `transferAndLock` function. This is RECOMMENDED for use-cases where Token transfer and subsequent revocation is REQUIRED.

#### INTERFACE

```
// SPDX-License-Identifier: CC0-1.0

pragma solidity >=0.7.0 <0.9.0;

/// @title Lockable Extension for ERC721
/// @dev Interface for the Lockable extension
/// @author StreamNFT 

interface IERC7066{

    /**
     * @dev Emitted when tokenId is locked
     */
    event Lock (uint256 indexed tokenId, address _locker);

    /**
     * @dev Emitted when tokenId is unlocked
     */
    event Unlock (uint256 indexed tokenId);

    /**
     * @dev Lock the tokenId if msg.sender is owner or approved and set locker to msg.sender
     */
    function lock(uint256 tokenId) external;

    /**
     * @dev Lock the tokenId if msg.sender is owner and set locker to _locker
     */
    function lock(uint256 tokenId, address _locker) external;

    /**
     * @dev Unlocks the tokenId if msg.sender is locker
     */
    function unlock(uint256 tokenId) external;

    /**
     * @dev Tranfer and lock the token if the msg.sender is owner or approved. 
     *      Lock the token and set locker to caller
     *      Optionally approve caller if bool setApprove flag is true
     */
    function transferAndLock(uint256 tokenId, address from, address to, bool setApprove) external;

    /**
     * @dev Returns the wallet, that is stated as unlocking wallet for the tokenId.
     *      If address(0) returned, that means token is not locked. Any other result means token is locked.
     */
    function lockerOf(uint256 tokenId) external view returns (address);
}
```
