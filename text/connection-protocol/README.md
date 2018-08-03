- Name: connection-protocol
- Author: Daniel Bluhm <daniel.bluhm@sovrin.org>
- Start Date: 2018-08-03
- PR:
- Jira Issue:

# Summary
[summary]: #summary

A definition of a connection establishment protocol.

# Motivation
[motivation]: #motivation

Create a protocol that agent developers can use to establish connections between different agent implementations.

# Tutorial
[tutorial]: #tutorial

This HIPE will establish the exchange of messages needed to establish a pairwise connection between two agents.

## Assumptions

The step that has been referred to as a "connection trigger" or previously called a "connection offer" (this term
has been deemed inaccurate) will not be covered in this HIPE. We assume that some previous action has taken place to
enable two agents to communicate.

The details of transporting a message from one agent to the other will also not be covered in this HIPE. We assume the
message packaging and transport details are correctly executed when using phrases like "Agent 1 sends the message
to Agent 2."

## Message Family

We propose that the message family used for the messages in this protocol will be `connection`, with a version of `1.0`,
resulting in the message type string:

```
did:sov:BzCbsNYhMrjHiqZDTUASHg;spec/connection/1.0/<message_type>
```

in accordance with the [proposed HIPE on message types](https://github.com/hyperledger/indy-hipe/pull/19).


## Message Types

The types of this message family use terms similar to those that are described in the [negotiation
flow](https://github.com/sovrin-foundation/ssi-protocol/tree/master/flow/std/negotiate_msg).

### Connection Offer

We propose that the message type for a connection offer will be `offer`, resulting in the following message type string:

```
did:sov:BzCbsNYhMrjHiqZDTUASHg;spec/connection/1.0/offer
```

In a negotiation flow, offer and request messages are used to negotiate the terms of the negotiation's focus. In the
context of connection establishment, this would mean that connection offer and request messages are used to iteratively
negotiate the terms of the pairwise connection.

Typically, there is no need to negotiate the terms of a connection. It is not anticipated that the connection offer will
be commonly used but it is included here for completeness.

Connection offers contain essentially the same information as connection requests:

```json
{
    "@type": "did:sov:BzCbsNYhMrjHiqZDTUASHg;spec/connection/1.0/offer",
    "@thread": "threading object defined here",
    "did": "did:sov:123456..."
}
```

#### Attributes

- `"@thread"` - the threading "decorator" will be described in another HIPE

# Reference
[reference]: #reference

Provide guidance for implementers, procedures to inform testing,
interface definitions, formal function prototypes, error codes,
diagrams, and other technical details that might be looked up.
Strive to guarantee that:

- Interactions with other features are clear.
- Implementation trajectory is well defined.
- Corner cases are dissected by example.

# Drawbacks
[drawbacks]: #drawbacks

Why should we *not* do this?

# Rationale and alternatives
[alternatives]: #alternatives

- Why is this design the best in the space of possible designs?
- What other designs have been considered and what is the rationale for not
choosing them?
- What is the impact of not doing this?

# Prior art
[prior-art]: #prior-art

Discuss prior art, both the good and the bad, in relation to this proposal.
A few examples of what this can include are:

- Does this feature exist in other SSI ecosystems and what experience have
their community had?
- For other teams: What lessons can we learn from other attempts?
- Papers: Are there any published papers or great posts that discuss this?
If you have some relevant papers to refer to, this can serve as a more detailed
theoretical background.

This section is intended to encourage you as an author to think about the
lessons from other implementers, provide readers of your proposal with a
fuller picture. If there is no prior art, that is fine - your ideas are
interesting to us whether they are brand new or if they are an adaptation
from other communities.

Note that while precedent set by other communities is some motivation, it
does not on its own motivate an enhancement proposal here. Please also take
into consideration that Indy sometimes intentionally diverges from common
identity features.

# Unresolved questions
[unresolved]: #unresolved-questions

- What parts of the design do you expect to resolve through the
enhancement proposal process before this gets merged?
- What parts of the design do you expect to resolve through the
implementation of this feature before stabilization?
- What related issues do you consider out of scope for this
proposal that could be addressed in the future independently of the
solution that comes out of this doc?
