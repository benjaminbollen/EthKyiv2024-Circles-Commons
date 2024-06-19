[Return to overview](/README.md)

## Getting Started

Circles has already been live in the world for several years. We'll refer to this as Circles v1
and you can find details for Circles v1 below.

Since last year, we've been working hard on improvements
to the core protocol, and the [first testnet contracts](https://github.com/aboutcircles/circles-contracts-v2/releases/tag/v0.3.4-alpha)
are accessible on [Chiado testnet](https://docs.gnosischain.com/about/networks/chiado), aka Circles v2.

## Circles v2 (for groups and testnet)

For building against Circles v2 we recommend using preferred wallets (eg. Metamask) - we don't need to complicate with smart contract wallets (but welcome if you so desire).

Circles v2 is more developer friendly (we hope):
- some historical bugs are addressed,
- all Circles are also governed by a single ERC1155 contract (rather than each person's Circles as a separate ERC20 contract)
- Group Circles are native to the protocol (ie. a group can trust existing Circles and they can be collaterlized into a new Circles identifier in ERC1155). Groups make it easier to accept the Circles of a (specific) Community in your dapp; or even to interact with different community currencies in a single dApp.
- any Circles (of any person or any group) can also be lifted out 

**To hack on ideas for "Governing the Commons" we recommend to focus on the crux of your idea during the hackathon
and treat Circles as a black box. Simply start by mocking Circles from a set of [ERC20 contracts, or an ERC1155 contract](https://github.com/OpenZeppelin/openzeppelin-contracts/tree/master/contracts/token) to represent the Group Circles of different communities.**

Circles v2 contracts:
- Contract code is at [github.com/aboutcircles/circles-contracts-v2](https://github.com/aboutcircles/circles-contracts-v2/tree/v0.3.4-alpha)
- Hub is ERC1155 [0x2066CDA98F98397185483aaB26A89445addD6740](https://gnosis-chiado.blockscout.com/address/0x2066CDA98F98397185483aaB26A89445addD6740?tab=read_contract)
- ERC20Lift is a factory to create ERC20 contracts for any of the ERC1155 (personal or group) Circles
    - important if you need/want an ERC20 interface to develop against
    - [0x84319f1168Cc2383b8b366d4ab7E20baBda03687](https://gnosis-chiado.blockscout.com/address/0x84319f1168Cc2383b8b366d4ab7E20baBda03687?tab=read_contract)
- Circles v2 is backwards compatible with Circles v1, so on testnet Circles v1 Hub contract is at [0xdbf22d4e8962db3b2f1d9ff55be728a887e47710](https://gnosis-chiado.blockscout.com/address/0xdbf22d4e8962db3b2f1d9ff55be728a887e47710?tab=read_contract)
- optionally Nameregistry is at [0x64703664BBc8A3BaeD014171e86Dfc2dF2E07A08](https://gnosis-chiado.blockscout.com/address/0x64703664BBc8A3BaeD014171e86Dfc2dF2E07A08?tab=read_contract)
- full list of contract addresses, see [release v0.3.4-alpha](https://github.com/aboutcircles/circles-contracts-v2/releases/tag/v0.3.4-alpha)
- the generated *reference* code documentation is hosted at https://dev.zirkles.org; there is no overview documentation yet :-/

## Circles v1 (mainnet)

Once Circles v2 launches, you will be able to migrate your Circles v1 balance to v2.

If you choose to build against Circles v1 then you can use
- [circles SDK NPM v0.0.44](https://www.npmjs.com/package/@circles-sdk/sdk/v/0.0.44) for Circles v1
- [Dappcon 2024 wallet workshop](https://github.com/aboutcircles/circles-code-quest)
- for reference [circles-sdk github](https://github.com/aboutcircles/circles-sdk/tree/dev)

Runs on Gnosis Chain, since 2020. You can register your personal account with [Circles Garden](https://circles.garden).
- legacy wallet https://circles.garden (preferred, manages SAFE contract and you can export your keys)
    - supports creating an "organizational shared account" (is shared SAFE contract which doesn't mint CRC)
- (optional) alpha-release of Metri wallet also supports Circles https://app.metri.xyz (mobile only)
    - uses passkeys,
    - atm doesn't allow to export self-custody keys, unless you first register in circles.garden, and then import the seed phrase in Metri

Contract addresses:
- Hub Contract [0x29b9a7fbb8995b2423a71cc17cf9810798f6c543](https://gnosisscan.io/address/0x29b9a7fbb8995b2423a71cc17cf9810798f6c543/advanced#readContract)
- legacy Circles v1 documentation https://handbook.joincircles.net/docs/developers/

## More helpful links

- Add Chaido chain to Metamask https://chaidochain.net
- Chaido faucet https://faucet.chiadochain.net/
- Block explorer for Chiado Chain https://gnosis-chiado.blockscout.com/
- public RPC endpoints:
    - https://gnosis-chiado-rpc.publicnode.com/