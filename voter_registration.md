# SPOCRA Voter Registration Specification
In situations where votes allowed in a proposal be limited to a specific number of votes per entity, the
voting authority should generate and define a unique VoterId for each eligible vote or voter and issue these
securely and discreetly to the voting entities.

Following the close of the voting window, a separate JSON file containing a simple list of "eligible Voter IDs"
should be submitted to the chain so that voting validators can confirm the eligibility of votes cast during the
voting window.

For additional security, the list of eligible voters shoud be submitted from the same address used to submit the
ballot proposal to the chain.

**NOTE:** There is a 64-character limit for all string entries.

```json
{
  "type": "object",
  "properties": {
    "ObjectType": {
      "type": "string",
      "required": true,
      "purpose": "Identify the type of object this is",
      "example": "VoteRegistration"
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
      "example": "52da18fb-64ec-4d00-9484-fdb0b67ef678"
    },
    "RegistrationId": {
      "type": "string",
      "required": true,
      "purpose": "The sha1 hash of the ProposalId + RegistrationId should equal the value of the VoterHash submitted in the proposal",
      "example": "a489201d-48a2-4775-a41d-4fbf5670a141"
    },
    "Voters": {
      "type": "array",
      "required": true,
      "purpose": "List of eligible voter IDs in this ballot proposal.",
      "items": {
        "type": "string",
        "required": true,
        "purpose": "Unique VoterIds. For the sake of privacy, voter IDs should never contain sensitive or identifying information",
        "example": "f493b4a1-8658-4e72-b317-37793a199ab3"
      }
    }
  }
}
```