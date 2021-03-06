# Reputation in P2P Lending

## Abstract

We proposes an outline of a p2p lending system which includes a reputation system designed to support lenders (including groups of individuals) in making good decisions about issuing loans on a P2P lending framework such as Kiva. The reputation system should avoid the pitfalls of a single, legible credit score. Designed for one-to-one, one-to-many, and many-to-many connections.

## Introduction

This paper proposes an outline of a p2p lending system. The lending system exists as a network of nodes, where a node can act in two roles, either as lender or borrower. The network is made up of an on chain contract layer and and an off chain [Social Graph](https://www.notion.so/7898d4c5-81c2-4469-b481-3f83835a0158) layer. The contract layer is used to record and execute loans in the form of note contracts. The social graph layer records connections between nodes in the network, it is used to connect borrowers to sources of credit, and to encourage good behaviour. 

**Social Graph**

There is no single "social graph" instead each node maintains their own view of their connections. It is expected that a nodes social graph is built up over time as the individual controlling the node makes connections to other individuals in their day to day lives. Hence it represents very local and personal relationships. Each node in a social graph can have two values associated with it: [Credit](https://www.notion.so/abc9a7bf-0908-40a4-a068-1575ca897af8) and [Credit Multiple](https://www.notion.so/6343dbfb-3f7b-4f7c-a335-620a519dd7e5). 

**Contract layer**

The contract layer records loan contracts called [Note Contract](https://www.notion.so/1166bbbe-5c16-4cf6-b750-47bbb41db451)s as smart contracts. A loan can be issued and re-payed in a publically verifiable manner. The social graph layer can respond to events that become visible in the contract layer such as missed repayments and loan defaults. This might result in reduced credit extended to the offending nodes.

## Components

### Actors

Lender

Borrower

### Note Contract

Principal

Interest

Repayment horizon

Repayment Schedule

Logic: describes how payments can be received by the contract and distributed to funders and what happens when a loan defaults. 

### Lending Model

min and max loan amount

min max loan %

max graph depth (i.e. 3 degrees)

prevent double-lending y/n

## Design Primitives

- Prior Art

    [ETHLend - Get a crypto loan without selling your cryptocurrencies](https://ethlend.io/)

    [Kiva - Loans that change lives](https://www.kiva.org/)

    [Zidisha: Help remarkable people achieve their goals](https://www.zidisha.org/)

    [WeChat red envelope](https://en.wikipedia.org/wiki/WeChat_red_envelope)

    [fairmint](https://founders.fairmint.co/)

    [Category:Peer-to-peer lending companies](https://en.wikipedia.org/wiki/Category:Peer-to-peer_lending_companies)

    [Sikoba](https://www.sikoba.network/)

    [Trustlines Network](https://trustlines.network/)

This section describes concepts that influence our design of a peer-to-peer Web-of-Trust-based lending system.

**Web of Trust** originated from [PGP](https://github.com/WebOfTrustInfo/rwot1-sf/blob/master/topics-and-advance-readings/PGP-Paradigm.pdf) as a method for p2p public key verification—direct trust relationships established between friends or at key-signing parties would digitally chain, interweave, and cumulate into larger "webs of trust", enabling well-informed trust paths among complete strangers.

Importantly, each participant's view of the PGP web of trust, their trust assignments to other participants, is local and independent. The local context that informs each participant's "social trust graph", allowably, and necessarily, differs among everyone. In PGP web of trust, there is no need for agreement on global trust values. We view this as a form of **logical decentralization**, which Vitalik Buterin defines in [The Meaning of Decentralization](https://medium.com/@VitalikButerin/the-meaning-of-decentralization-a0c92b76a274):

> Logical (de)centralization— does the interface and data structures that the system presents and maintains look more like a single monolithic object, or an amorphous swarm? One simple heuristic is: if you cut the system in half, including both providers and users, will both halves continue to fully operate as independent units?

According to this definition, blockchains are logically centralized, and the internet is not. This contrast, perhaps, highlights a missing link. By empowering hubs of local knowledge and verification, equipping the logical decentralization that has driven the internet’s success with innovations in cryptography and incentive design, the blockchain, crypto, and internet communities can enable and enhance a rich set of use cases, starting with decentralized reputation and credit systems, using Web of Trust a la PGP.

Webs of trust are logically decentralized but can piggyback on the global consensus of blockchains for a sound financial railing, data availability, proof of publication, dispute resolution, etc.

Webs of trust end and start with local context. They are bootstrapped by direct, local trust relationships. In a credit web of trust, for instance, trust between a local grocery store and its customers, between an accountant and her clients, between business partners, can cascade into large, highly connected credit networks. Information accuracy increases with localization, and this is the key to solving **the knowledge problem:** how do we achieve economic efficiency when knowledge is highly distributed? Economist-philosopher Friedrich Hayek waxes prophetic in his 1945 essay [The Use of Knowledge in Society](http://bev.berkeley.edu/ipe/readings/The%20use%20of%20knowledge%20in%20society.pdf):

> We cannot expect that this problem will be solved by first communicating all this knowledge to a central board which, after integrating all knowledge, issues its orders. We must solve it by some form of decentralization ...because only thus can we insure that the knowledge of the particular circumstances of time and place will be promptly used.

Locally bootstrapped webs of trust, leveraging real world social relationships, also allows social reputation to replace stake as collateral. This, moreover, eases possibilities for debt forgiveness and locally restricts prejudice and nepotism.

The connectivity of webs of trust enables complex trust relationships among participants. Particularly, participants can assign trust/lend according to how much **skin in the game** their trustees have, for instance, lending .75x what a highly trusted peer lends in a particular contract. This further exploits the social graph structure, distributes risk, and enhances users' trust metrics.

### Example Flow

1. The [Borrower](https://www.notion.so/cf062fcc-30d9-4c0c-9186-81fdc6539950) opens a [Note Contract](https://www.notion.so/1166bbbe-5c16-4cf6-b750-47bbb41db451), which includes the [Principal](https://www.notion.so/70a985d6-9a5f-4876-83e0-589433a9c3ca), [Interest](https://www.notion.so/873124d5-ad7b-4bed-a7c6-f4df1177baf9), [Repayment Horizon](https://www.notion.so/478f578d-2d04-4422-9242-e21ba520322f), and [Repayment Schedule](https://www.notion.so/dd702dca-b0e5-4562-9a97-9806f5c9ccc7).
2. The [Borrower](https://www.notion.so/cf062fcc-30d9-4c0c-9186-81fdc6539950) makes a "funds request", which is request to contribute funds to a [Note Contract](https://www.notion.so/1166bbbe-5c16-4cf6-b750-47bbb41db451), to nodes in their [Social Graph](https://www.notion.so/7898d4c5-81c2-4469-b481-3f83835a0158) 
3. The [Lender](https://www.notion.so/cc18e107-4f4a-41be-8560-d731a742d938)s in the [Borrower](https://www.notion.so/cf062fcc-30d9-4c0c-9186-81fdc6539950)'s [Social Graph](https://www.notion.so/7898d4c5-81c2-4469-b481-3f83835a0158) commit to supplying funds to the [Note Contract](https://www.notion.so/1166bbbe-5c16-4cf6-b750-47bbb41db451) based on the value of [Credit](https://www.notion.so/abc9a7bf-0908-40a4-a068-1575ca897af8) they extend to the fund requester, the terms of the note contract, and their personal [Lending Model](https://www.notion.so/b057482b-a71c-451b-b163-cafb612ca08a). The commitment is returned to the borrower.
4. A [Lender](https://www.notion.so/cc18e107-4f4a-41be-8560-d731a742d938) can optionally announce a "recommendation", which includes the [Note Contract](https://www.notion.so/1166bbbe-5c16-4cf6-b750-47bbb41db451) and their funds commitment, to to their [Social Graph](https://www.notion.so/7898d4c5-81c2-4469-b481-3f83835a0158).
5. [Lender](https://www.notion.so/cc18e107-4f4a-41be-8560-d731a742d938)s receiving a recommendation can commit funds to the note contract according to the [Credit Multiple](https://www.notion.so/6343dbfb-3f7b-4f7c-a335-620a519dd7e5) they extend to the recommending node and the funds committed by that node (multiply one by the other). The commitment is returned to the borrower.
6. Once the borrower has received enough commitments to fully fund a loan they can post a funded [Note Contract](https://www.notion.so/1166bbbe-5c16-4cf6-b750-47bbb41db451) to the contract layer. The borrower may receive commitments for more funds than is required, in which case they can decide which to use.
7. The fulfilment of the loan is carried out by interaction with the contract layer. The [Borrower](https://www.notion.so/cf062fcc-30d9-4c0c-9186-81fdc6539950) repays funds to the note contract according to the [Repayment Horizon](https://www.notion.so/478f578d-2d04-4422-9242-e21ba520322f) and [Repayment Schedule](https://www.notion.so/dd702dca-b0e5-4562-9a97-9806f5c9ccc7). The contract distributes payments to the lenders that funded the contract according to their contributions. 

## Areas for Exploration

social elasticity, protection against missed payments, negative feedback loops

one version of this is to make everyone culpable for their first degree, such that instead of C lending to B, C lends to B who then lends to A, so a default is entirely absorbed by the first degree (as well as the majority of the interest?)

risk exploration, such double-lending to the same loan contract

bootstrapping nodes using VCs, social graph, or existing credit system

set credit pathway, prevent prejudice for/against nodes, pure meritocracy

ritual of loan signing, QR codes

smart contract hubs for always-online lending

derive a credit score from the web-of-credit, potentially as a verified credential, for access to traditional credit or as a reputation score in another system

legal risk: securities and crowd funding regulation in US: [https://en.wikipedia.org/wiki/Consumer_Credit_Act_1974](https://en.wikipedia.org/wiki/Consumer_Credit_Act_1974)

vouchers/IOUs vs. actual payment flow

hyper undercollateralization vs. low liquidity

how is interest distributed?

tension between open information ideal and scarcity of information - how to incentivize sharing of local knowledge

TODO: **Funding model v2**

## Glossary

[Glossary](https://www.notion.so/4768ad9cec164bf78b74ced8594d7a23)
