[Return to overview](/README.md)

# Getting Started

Circles has already been live in the world for several years. We'll refer to this as Circles v1
and you can find details for Circles v1 below.

Since last year, we've been working hard on improvements
to the core protocol, and the [first testnet contracts](https://github.com/aboutcircles/circles-contracts-v2/releases/tag/v0.3.4-alpha)
are accessible on [Chiado testnet](https://docs.gnosischain.com/about/networks/chiado), aka Circles v2.

# Circles v2 (for groups and testnet)

For building against Circles v2 we recommend using preferred wallets (eg. Metamask) - we don't need to complicate with smart contract wallets (but welcome if you so desire).

Circles v2 is more developer friendly (we hope):
- some historical bugs are addressed,
- all Circles are also governed by a single ERC1155 contract (rather than each person's Circles as a separate ERC20 contract)
- Group Circles are native to the protocol (ie. a group can trust existing Circles and they can be collaterlized into a new Circles identifier in ERC1155). Groups make it easier to accept the Circles of a (specific) Community in your dapp; or even to interact with different community currencies in a single dApp.
- any Circles (of any person or any group) can also be lifted out 

**To hack on ideas for "Governing the Commons" we recommend to focus on the crux of your idea during the hackathon
and treat Circles as a black box. Simply start by mocking Circles from a set of [ERC20 contracts, or an ERC1155 contract](https://github.com/OpenZeppelin/openzeppelin-contracts/tree/master/contracts/token) to represent the Group Circles of different communities.** If you have time later in your project to integrate it with Circles v2, all the better.

## Building against Circles v2 on testnet

You can directly call contract functions over standard RPCs;
complementary we have a very early preview of an SDK to help
manage interactions from the perspective of a user (a human avatar).

### Circles v2 contracts:
- Contract code is at [github.com/aboutcircles/circles-contracts-v2](https://github.com/aboutcircles/circles-contracts-v2/tree/v0.3.4-alpha)
- Hub is Circles is ERC1155 [0x2066CDA98F98397185483aaB26A89445addD6740](https://gnosis-chiado.blockscout.com/address/0x2066CDA98F98397185483aaB26A89445addD6740?tab=read_contract)
- ERC20Lift is a factory to create ERC20 contracts for any of the ERC1155 (personal or group) Circles
    - important if you need/want an ERC20 interface to develop against
    - [0x84319f1168Cc2383b8b366d4ab7E20baBda03687](https://gnosis-chiado.blockscout.com/address/0x84319f1168Cc2383b8b366d4ab7E20baBda03687?tab=read_contract)
- Circles v2 is backwards compatible with Circles v1, so on testnet Circles v1 Hub contract is at [0xdbf22d4e8962db3b2f1d9ff55be728a887e47710](https://gnosis-chiado.blockscout.com/address/0xdbf22d4e8962db3b2f1d9ff55be728a887e47710?tab=read_contract)
- optionally Nameregistry is at [0x64703664BBc8A3BaeD014171e86Dfc2dF2E07A08](https://gnosis-chiado.blockscout.com/address/0x64703664BBc8A3BaeD014171e86Dfc2dF2E07A08?tab=read_contract)
- full list of contract addresses, see [release v0.3.4-alpha](https://github.com/aboutcircles/circles-contracts-v2/releases/tag/v0.3.4-alpha)
- the generated *reference* code documentation is hosted at https://dev.zirkles.org; there is no overview documentation yet :-/

### RPC access to Chiado and Circles contracts

To access Chiado there are several (public) RPC (ethereum) endpoints, for example 

    https://gnosis-chiado-rpc.publicnode.com/.

In principle all functionality is directly accessable from
standard RPC calls to any Chiado node. However, for example
to accumulate the balances a person has across the different
Circles tokens, this would involve complicated polling.

**Therefore we also host an RPC endpoint that, in addition to
standard Ethereum RPC, also indexes the Circles events of the testnet (contracts v0.3.4) at:**

    https://chiado-rpc.aboutcircles.com/

You can find the documentation for the RPC in [Circles-Nethermind-Plugin](https://github.com/CirclesUBI/circles-nethermind-plugin?tab=readme-ov-file#circles-rpc-methods)
In essence you might want to look at this is you want to know
the total balances of a user across the graph, but you can also
query any of the other events, effectively the methods of interest might be:
```
    circles_getTotalBalance (v1 on testnet)
    circlesV2_getTotalBalance
    circles_getTokenBalance (v1 on testnet)
    circlesV2_getTokenBalances
    circles_query
    circles_events (* only for v1 mainnet)
    eth_subscribe("circles")
```

Note: for mainnet v1 the indexer of Circles events can be accessed at

    https://rpc.falkenstein.aboutcircles.com/
    https://rpc.helsinki.aboutcircles.com/

and SDK v0.0.44 is a stable alpha release.

### Circles SDK (early preview)

For contracts on Circles v2, there is an early preview SDK release which you can use
to get started with interacting with Circles v2:

[v0.0.45-preview-29](https://www.npmjs.com/package/@circles-sdk/sdk/v/0.0.45-preview-29) covers Circles v2; use [v0.0.44](https://www.npmjs.com/package/@circles-sdk/sdk/v/0.0.44) if you want to cover Circles v1 on mainnet only.  
Check the [SDK releases on GitHub](https://github.com/CirclesUBI/circles-sdk/releases) for the code and docs.

An `avatar` is the main interaction point (it's effectively the address representing your user when using metamask) and it's registered in the Circles social graph and as such forms a vertex in the graph, and can forn trust edges with other avatars.

The SDK is only tested with avatars as humans right now (organizations and groups are experimental).

- The main avatar interactions are all defined here: https://github.com/CirclesUBI/circles-sdk/blob/dev/packages/sdk/src/AvatarInterface.ts
- All v1 actions are implemented here: https://github.com/CirclesUBI/circles-sdk/blob/dev/packages/sdk/src/v1/v1Person.ts
- All v2 actions are implemented here: https://github.com/CirclesUBI/circles-sdk/blob/dev/packages/sdk/src/v2/v2Person.ts
- The SDK can subscribe to events from the Circles RPC node. See [events.ts](https://github.com/CirclesUBI/circles-sdk/blob/dev/packages/data/src/events/events.ts) for a full list.

_There is a [SvelteKit demo application](https://github.com/aboutcircles/5ecret-garden) that showcases the use of the SDK. It originates from a workshop at DappCon 24 and uses [v0.0.45-preview-29](https://www.npmjs.com/package/@circles-sdk/sdk/v/0.0.45-preview-29) of the SDK._

# Circles v1 (mainnet)

For mainnet v1 the indexer of Circles events can be accessed at

    https://rpc.falkenstein.aboutcircles.com/
    https://rpc.helsinki.aboutcircles.com/

and SDK v0.0.44 is a stable alpha release. (see above for more links).

Once Circles v2 launches, you will be able to migrate your Circles v1 balance to v2.

If you choose to build against Circles v1 then you can use
- [circles SDK NPM v0.0.44](https://www.npmjs.com/package/@circles-sdk/sdk/v/0.0.44) for Circles v1
- [Dappcon 2024 wallet workshop](https://github.com/aboutcircles/circles-code-quest)
- for reference [circles-sdk github](https://github.com/aboutcircles/circles-sdk/tree/dev)
- [Circles v1 SDK documentation](https://docs.aboutcircles.com/developer-docs/getting-started-with-the-sdk)

Runs on Gnosis Chain, since 2020. You can register your personal account with [Circles Garden](https://circles.garden).
- legacy wallet https://circles.garden (preferred, manages SAFE contract and you can export your keys)
    - supports creating an "organizational shared account" (is shared SAFE contract which doesn't mint CRC)
- (optional) alpha-release of Metri wallet also supports Circles https://app.metri.xyz (mobile only)
    - uses passkeys,
    - atm doesn't allow to export self-custody keys, unless you first register in circles.garden, and then import the seed phrase in Metri

Contract addresses:
- Hub Contract [0x29b9a7fbb8995b2423a71cc17cf9810798f6c543](https://gnosisscan.io/address/0x29b9a7fbb8995b2423a71cc17cf9810798f6c543/advanced#readContract)
- legacy Circles v1 documentation https://handbook.joincircles.net/docs/developers/


# More helpful links

- Add Chaido chain to Metamask https://chaidochain.net
- Chaido faucet https://faucet.chiadochain.net/
- Block explorer for Chiado Chain https://gnosis-chiado.blockscout.com/
- public RPC endpoints:
    - https://gnosis-chiado-rpc.publicnode.com/
