# What are xAccounts?

xAccounts are an implementation standard for setting up accounts on chain A that are controlled by an account on chain B. Built using the Wormhole messaging bridge, xAccounts form the 4th building block of Wormhole followed by xAssets, xApps, and xData.&#x20;

xAccounts share many similarities with Cosmos's [Interchain Accounts (ICA)](https://ibc.cosmos.network/main/apps/interchain-accounts/overview.html):&#x20;

* Ability to establish account controls xChain.&#x20;
* Account hierarchies can be defined.&#x20;
* Generic messages and contract calls can be relayed

but also offer certain differences:&#x20;



v1 xAccount operations are all assumed to be asynchronous and non-atomic. Future iterations could utilize Wormhole's [batch VAAs](https://book.wormhole.com/wormhole/4\_vaa.html#batch-vaas) to achieve atomic execution.
