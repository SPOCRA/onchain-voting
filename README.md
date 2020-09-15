# SPOCRA On-Chain Voting
The purpose of this repository is to describe and outline the process of submitting ballot proposals and casting votes onto the Cardano blockchain.

While the initial intent of this outline is to allow voting for the SPOCRA organization, the functionality and packages described here should be easily adaptable to serve other purposes.

## High-Level Concept
The basic premise of this idea is that a group or entity can submit a "ballot proposal" to the blockchain and all eligible voters may similarly submit to cast their votes, storing them in the immutable ledger of the blockchain.

`cardano-cli` makes this possible via inclusion of the `--metadata-json-file FILE` command line argument.

By using this properly structured JSON format we can submit "meta" data to the chain and (at current) query it back out again via the `cardano-db-sync` PostgreSQL interface.

In this way we can easily query for all "votes" cast on the chain to arrive at a final result.

## SPOCRA Voting
Aside from just a simple poll, organizations such as SPOCRA will require some means of voter authentication as well as a limited time window to vote. This can be accomplished and queried from the chain using JSON metadata attributes.

The structure and format of this JSON specification will be an on-going development process as SPOCRA hones and refines its needs.

### Ballot Proposals
It's important, when voting on the chain, that the parameters of the vote in question should also be immutably stored on the chain as well.

To this end, we shall define a "Ballot Proposal" JSON specification.

The current SPOCRA Ballot Proposal can be found at [ballot_proposal.md](ballot_proposal.md)

### Voter Ballot
To view the details of the SPOCRA Voter Ballot you can view [voter_ballot.md](voter_ballot.md)

### Voter Registration
Currently, we do not have a reliable method of identity verification on-chain. This predicates the need for an assigned
"Voter ID" in the case of a vote where we want to limit vote casting to one or more votes per entity.

To this end, currently the onus is on the voting authority to generate and issue a unique "Voter ID" for every voter in
a given vote proposal. The valid IDs eligible to vote should be submitted to the chain following the close of the voting
window to enable vote validation tools to confirm a voter's eligibility in the vote.

To view the details of the SPOCRA Voter Registration you can view [voter_registration.md](voter_registration.md)

## Requirements

Currently, [cardano-node-db-sync](https://github.com/input-output-hk/cardano-db-sync) seems to be the only block exploration method that supports fetching transaction metadata.
