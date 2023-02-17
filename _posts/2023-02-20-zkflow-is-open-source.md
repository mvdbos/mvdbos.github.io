---
layout: post
title:  "ZKFlow is open source!"
date:   2023-02-20 16:53 +0100
categories: zkflow privacy blockchain corda
---

ZKFlow is open source! ZKFlow is a consensus protocol for Corda that enables private transactions for any smart contract using Zero Knowledge Proofs. You can find it on [GitHub](https://github.com/ing-bank/zkflow).

From the project's inception, our small team inside ING's blockchain team worked on it intensively, and I am really proud of what we achieved. With working software, we proved that it is feasible to integrate Zero Knowledge transaction validation into an existing blockchain platform in a usable and performant way.

It was an amazing journey with an amazing team. We learned a lot about smart and efficient ways to achieve privacy, about protocol design, about applied cryptography and about privacy technology such as Zero Knowledge Proofs and Trusted Execution Environments.

And although we have recently moved on to new challenges, I really wanted to share what we did, so that others may inspect it, test it, and learn from it. It would be amazing if this way, it could contribute in a small way to addressing the privacy challenges so many (blockchain) platforms still have.


## A bit of history
It all started with my realization that [Corda](https://docs.r3.com/en/platform/corda/4.10/community/key-concepts.html) (like many other platforms), does not offer private transactions: while Corda does not broadcast transactions across the entire network, future owners of an on-chain asset *will* see all details of previous transactions for that asset. This is a problem when you want to do sensitive financial transactions on a network where your competition is also transacting and where they may be a future owner of one of your assets. They will know what you paid for it and what you sold it for. 

To solve that problem, we decided to do a proof of concept to see if it was feasible to adapt Corda's consensus protocol to incorporate zero knowledge proofs for transaction validity. We also wanted to know if we could validate a realistic Corda smart contract in zero knowledge at all and if that would be fast enough to be usable. It turned out that it was feasible, so we got the green light to turn it into working software, with the aim of making it available to all Corda users. 

And for now it is done. And it actually works too. You can create private transactions on Corda with ZKFlow with your own private smart contract logic.

Along the way we solved a lot of very hard problems and had to go back to the drawing board multiple times. A complicating factor was that we did not want to fork Corda, for maximum adoption. This meant working around a few limitations in Corda. This limited us in how far we could optimize performance. 

## Some details about ZKFlow
If you want all the nitty gritty, best check out the ZKFlow on [GitHub](https://github.com/ing-bank/zkflow). Otherwise, read on.

ZKFlow enables CorDapp builders to make some or all states in a transaction private. Private states will not be present in the backchain, nor will they be disclosed to the [notary](https://docs.r3.com/en/platform/corda/4.10/community/key-concepts-notaries.html). Instead, private states are replaced by a Zero Knowledge proof that guarantees validity of those hidden states according to the transaction's smart contract.

Direct participants to a transaction will always have access to all its private contents, so that they know what transaction they are signing. Future owners of a state or observers of the chain will never see the private contents of previous transactions, unless a direct participant actively discloses them.

To dive right in and get started, check the [Getting Started](https://github.com/ing-bank/zkflow#getting-started) section of the README.

For theoretical details about the ZKFlow protocol, check out the [ZKFlow white paper](https://github.com/ing-bank/zkflow/blob/master/docs/ZKFlow_whitepaper.pdf). A version of this whitepaper was presented by Gamze Tillem at CoDecFin in 2022. 

