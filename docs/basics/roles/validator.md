---
label: Validators
description: Validator role and responsibility
---

# Validator

A validator is an individual who is responsible for validating transactions and generating blocks within a blockchain. A node operator is a part of the validator entity who is responsible for setting up and running the node.

## Node recognition

The Ronin nodes must have a validator list so they can specify which validator generates the next block. There is a mechanism executed every 30 minutes to sync the validator list from a contract named `SidechainValidator`. When a validator needs to be added to removed, this contract is modified.

## Validator responsibilities

Validators are in charge of the following:

* Generating blocks during their turn.
* Helping other validators generate blocks when they miss their turn.
* Acknowledging deposit and withdrawal events to facilitate assets transfers.
* Updating validator events.
* Updating effective threshold events.

### Generating blocks

Whenever a block is generated, the next validator has to validate incoming transactions and generate a new block.

The block generated by the designated validator has a larger difficult weight. If the designated validator can not produce a block, the other validators generate a new block. In this case, that block has a smaller difficult weight. These difficult weights help nodes have additional facilities to reorganize in case the chain is forked.

### Acknowledging events

The validators have to acknowledge every event related to the transfer gateway and validator contract.

The validators acknowledge the deposit event and withdrawal event to facilitate asset transferring. In the `SidechainValidator` contract, there is a threshold setting indicating that an event needs to have at least that ratio of acknowledgment from validators, whether it is adding or removing validators, depositing or withdrawing assets, or also updating that defined threshold.

## Become a validator

Depending on the network, the ways to become a validator are different:

* Testnet: Follow the steps in [Become a validator](./../../validators/onboarding/become-validator.mdx).
* Mainnet: Contact us at hello@axieinfinity.com.

### RON requirements for validators
Each Ronin validator is required to stake 250,000 RON.

If a validator fails at producing the correct blocks, their RON stake is at risk of being slashed. RON staked by the public is also at risk of being slashed, so choose wisely.