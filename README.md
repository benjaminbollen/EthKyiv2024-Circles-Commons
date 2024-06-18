# EthKyiv - using Circles for Governing the Commons

This readme is written to give you minimal information about Circles to get you up to speed fast.

## Short Introduction

Circles is a social money. At its most basic it is a simple idea: every human should always have
some financial means to facilitate their (digital) life.

If we unpack that mission further though, then in order to fairly distribute such a social money
it reveals a much more challenging problem: how can we determine which accounts belong to
genuine human beings, and which accounts are sybil/bot accounts?

Several projects address such questions in a top-down manner, by creating a registry of which accounts
are authentic. For example, zk-proofs of passports is a great way to achieve this, national governments
already maintain such citizen registries, issue cryptographic documents, and with zk proofs we can assert
properties without revealing all information. Unfortunately not everyone has access to a passport,
and nor should we rely on passports for building identity on the web.

With Circles in contrast, we address this question by turning the global question of "which accounts are sybil",
into a local question of "do you know that the following accounts are *not* sybil?"

To make the money itself local, we have to consider the "fungibility" or "spendability" of Circles:
there isn't one (global) Circles where everyone has their balance.
Circles instead are defined on each node of a social graph, locally.

The social contract:
  - anyone (any address) can register in the contract - there is no KYC, 
