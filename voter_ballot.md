# SPOCRA Voter Ballot Specification
Individual "Voters" casting a vote in the election should submit a "ballot" JSON file in compliance with the parameters of the "ballot proposal" in order for their vote to be counted.

```json
{
  "type": "object",
  "properties": {
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
      "type": "boolean",
      "required": false,
      "purpose": "For simple boolean votes this field should represent the voter's selection of Yes/No|True/False",
      "example": "<true|false>"
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
          }
        }
      }
    }
  }
}
```
