# SPOCRA Ballot Proposal Specification
Submitting an official ballot proposal to the voting members should be done "on-chain" for the same sake of immutability and posterity that votes should also be cast on the chain.

**NOTE:** There is a 64-character limit for all string entries.

## Proposed Ballot Proposal Format

```json
{
  "type": "object",
  "properties": {
    "ObjectType": {
      "type": "string",
      "required": true,
      "purpose": "Identify the type of object this is",
      "example": "VoteProposal"
    },
    "ObjectVersion": {
      "type": "string",
      "required": false,
      "purpose": "Specify the version of the object for future reference and parsing",
      "example": "2.0.1"
    },
    "NetworkId": {
      "type": "string",
      "required": true,
      "purpose": "Identify the voting 'network' this proposal belongs to",
      "example": "SPOCRA"
    },
    "ProposalId": {
      "type": "string",
      "required": true,
      "purpose": "Unique identifier (hash?) identifying this particular proposal",
      "example": "52da18fb-64ec-4d00-9484-fdb0b67ef678"
    },
    "PoolId": {
      "type": "string",
      "required": false,
      "purpose": "Require that voters be delegated to the specified pool ID (bech32 or hex)",
      "example": "pool1qqqz9vlskay2gv3ec5pyck8c2tq9ty7dpfm60x8shvapguhcemt"
    },
    "SnapshotEpoch": {
      "type": "integer",
      "required": false,
      "purpose": "Dictate which epoch snapshot should be used and display for votes based on stake power",
      "example": 247,
      "default": 0
    },
    "RequireVoterId": {
      "type": "integer",
      "required": true,
      "purpose": "Dictate whether a unique Voter ID is required for participants in this vote.",
      "example": "<1|0>",
      "default": 1
    },
    "VoterHash": {
      "type": "string",
      "required": false,
      "purpose": "This should be the sha1 hash of the ProposalId + a unique RegistrationId that will be submitted containing registered VoterIds following the close of the voting window.",
      "example": "35184eba36aaa9ab8f96cba71ac65d4a54e0e59c"
    },
    "Title": {
      "type": "string",
      "required": true,
      "purpose": "The title of the ballot proposal",
      "example": "Creation Committee Election"
    },
    "Questions": {
      "type": "array",
      "required": true,
      "purpose": "Provide one or more ballot questions that voters will vote on.",
      "items": {
        "type": "BallotQuestion",
        "required": true,
        "purpose": "Describe the voting mechanics of a given ballot question",
        "reference": "https://github.com/SPOCRA/onchain-voting/ballot_question.md"
      }
    },
    "VoteStartPeriod": {
      "type": "integer",
      "required": false,
      "purpose": "Specify the Epoch that voting will start.",
      "example": 213
    },
    "VoteEndPeriod": {
      "type": "integer",
      "required": false,
      "purpose": "Specify the Epoch that voting will end.",
      "example": 215
    },
    "VoteStartTime": {
      "type": "timestamp",
      "required": false,
      "purpose": "Specify the timestamp (UTC) that voting will start.",
      "example": "2020-09-01 00:00:00"
    },
    "VoteEndTime": {
      "type": "timestamp",
      "required": false,
      "purpose": "Specify the timestamp (UTC) that voting will end.",
      "example": "2020-10-01 00:00:00"
    }
  }
}
```
