# SPOCRA Ballot Question Specification
This object is included as part of a [Ballot Proposal](ballot_proposal.md).

**NOTE:** There is a 64-character limit for all string entries.

## Ballot Question Format

```json
{
  "type": "object",
  "properties": {
    "Question": {
      "type": "array",
      "required": true,
      "purpose": "Describe what is being voted on",
      "items": {
        "type": "string",
        "required": true,
        "purpose": "Long-format ballot question broken into an array of 64-character strings"
      },
      "example": "Who do you choose to elect for the Creation Committee?"
    },
    "Description": {
      "type": "array",
      "required": false,
      "purpose": "Provide more in-depth description of the ballot proposal",
      "items": {
        "type": "string",
        "required": false,
        "purpose": "Describe the question in more detail"
      },
      "example": "The top seven (7) individuals will be selected to the initial Creation Committee with the two (2) runners-up serving as 'alternates' in the case of a Committee vacancy. You may vote for up to 3 nominees"
    },
    "ProposalURL": {
      "type": "url",
      "required": false,
      "purpose": "Provide a URL where more information about the proposal may live (maybe a forum for discussing pros and cons, etc)",
      "example": "https://wearecardano.io/proposals/abc001ef"
    },
    "VoteType": {
      "type": "string",
      "required": true,
      "purpose": "Define the type of vote (boolean [true/false], choice [one or more choices])",
      "example": "<boolean|choice>"
    },
    "VoteLimit": {
      "type": "integer",
      "required": false,
      "purpose": "Define the number of votes an individual may cast in a multiple-choice vote",
      "example": 3
    },
    "VoteMultiple": {
      "type": "integer",
      "required": false,
      "purpose": "Define whether or not a voter may vote for the same candidate more than once in a multiple-choice vote",
      "example": "<0|1>"
    },
    "VoteRanked": {
      "type": "integer",
      "required": false,
      "purpose": "Define whether or not voters should rank their votes in order of preference",
      "example": "<0|1>"
    },
    "VoteOptions": {
      "type": "array",
      "required": false,
      "purpose": "Provide the list of voting options for choice votes",
      "items": {
        "type": "object",
        "properties": {
          "CandidateId": {
            "type": "string",
            "required": true,
            "purpose": "A unique identifier to identify this vote option during vote casting.",
            "example": "abc012de"
          },
          "Name": {
            "type": "string",
            "required": true,
            "purpose": "Provide the name of the vote option",
            "example": "Joe Q. Public"
          },
          "Description": {
            "type": "array",
            "required": false,
            "purpose": "Maybe provide a short paragraph here of the candidate's stump speech and/or an explanation of what a vote for this option means",
            "items": {
                "type": "string",
                "required": false,
                "purpose": "Describe the question option in more detail"
            },
            "example": "Vote for Joe Q. Public because I am the most awesomest dude in the world!"
          },
          "URL": {
            "type": "url",
            "required": false,
            "purpose": "Provide an 'option-specific' URL that may contain more information about the choice/candidate",
            "example": "https://joeqpublic.me"
          }
        }
      }
    }
  }
}
```
