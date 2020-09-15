# SPOCRA Voter Ballot Specification
Individual "Voters" casting a vote in the election should submit a "ballot" JSON file in compliance with the parameters of the "ballot proposal" in order for their vote to be counted.

**NOTE:** There is a 64-character limit for all string entries.

```json
{
  "type": "object",
  "properties": {
    "ObjectType": {
      "type": "string",
      "required": true,
      "purpose": "Identify the type of object this is",
      "example": "VoteBallot"
    },
    "ObjectVersion": {
      "type": "string",
      "required": false,
      "purpose": "Specify the specification version of the object for future reference and parsing",
      "example": "1.0.0"
    },
    "NetworkId": {
      "type": "string",
      "required": true,
      "purpose": "Identify the voting 'network' that this vote belongs to",
      "example": "SPOCRA"
    },
    "ProposalId": {
      "type": "string",
      "required": true,
      "purpose": "Unique identifier (hash?) identifying the particular proposal this vote is for",
      "example": "abc001ef"
    },
    "VoterId": {
      "type": "string",
      "required": true,
      "purpose": "This should be a unique hash identifier that is generated on a per-proposal basis to validate and confirm an individual voter and ensure only a single vote may be cast by a single voter",
      "example": "1af000e5"
    },
    "Vote": {
      "type": "integer",
      "required": false,
      "purpose": "For simple boolean votes this field should represent the voter's selection of Yes/No|True/False",
      "example": "<0|1>"
    },
    "Choices": {
      "type": "array",
      "required": false,
      "purpose": "For single or multiple-choice votes, this array should contain information about their selections",
      "items": {
        "type": "object",
        "properties": {
          "CandidateId": {
            "type": "string",
            "required": true,
            "purpose": "Unique identifier for the candidate in the VoteOptions of the proposal",
            "example": "abc012def"
          },
          "VoteWeight": {
            "type": "integer",
            "required": true,
            "purpose": "Assign a 'vote weight' to this candidate based on the voter's selection, should default to 0 or 1 unless VoteMultiple is true in the Ballot Proposal",
            "example": 1
          },
          "VoteRank": {
            "type": "integer",
            "required": false,
            "purpose": "Assign a 'vote rank' to this candidate. Each 'rank' should only appear once in a given voter ballot except for '0' if the voter is not voting for this candidate. Only required for VoteMultiple and VoteRanked is true in the Ballot Proposal",
            "example": 3
          }
        }
      }
    }
  }
}
```
