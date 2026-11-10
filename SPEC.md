# Protocol Specification — draft v0.1

> Draft. Nothing here is adopted law. Governance parts take effect only when members adopt them.
> **Proposed default** marks the founder's current starting position — open to challenge in an issue. **[ARCHITECT]** marks technical decisions left to the builder.

## 1. Actors

| Actor | Who | How they get in |
|---|---|---|
| **Seeker** | Outer Ring. Reads, questions, tests the Order. | Holds a Temple NFT |
| **Member** | The Planet. Contributes in one or more signs. | Holds at least one Seal |
| **Hexastorm seat** | One per sign, six total. Coordinates. | Chosen by the holders of that sign — *process TBD* |
| **Patron / client** | Brings capital or commissions work. | Anyone; becomes Mage via Patron's Letter |

Roles are functions, not ranks. One person may hold several Seals; one sign may be held by many people.

## 2. Temple (live)

- Chain: **Base**. Open mint, ~0.0015 ETH.
- Purpose: mark of a Seeker's choice; gives access to the Seekers' Hall (Season I).
- Contract: [`0xe7922d3Ed1EA62466da8589cc7Fe2a111f66CaEF`](https://basescan.org/address/0xe7922d3Ed1EA62466da8589cc7Fe2a111f66CaEF) — token *Cirqus Heresy: Temples* (CIRQUSH). Collection on [OpenSea](https://opensea.io/collection/cirqus-heresy-temples).
- Source verification and a list of privileged functions: see issue #1.

Requirements for future contracts: the protocol reads Temple ownership but never depends on Temple for voting power. A Temple is a door, not a vote.

## 3. Seals

Six Seals: Trickster, Inquisitor, Oracle, Alchemist, Architect, Mage.

- **Non-transferable** (soulbound, e.g. ERC-5192 or ERC-1155 with transfers disabled). *Granted for contribution, never sold.*
- **Granting — proposed default:** during the founding period, the founder grants Seals. Once a sign has at least three holders, a new Seal of that sign requires **two existing holders** of the same sign to co-sign. Every grant links to the contribution it recognises.
- **Revocation — proposed default:** allowed, but only by a decision of the holder's chamber, never by one person. The reason is published and its hash logged on-chain. Grounds: fraud, impersonation, or a serious Code of Conduct breach — not disagreement.
- **Exit:** a holder can burn their own Seal at any time (*Keep the exit real*).
- **Metadata:** sign, grant date, granter, link to the contribution (PR, article, case).

The Mage Seal is the only Seal in the Leverage Chamber. It may be granted for capital or access, but never confers more than one seat's weight in coordination.

## 4. Escrow

Goal: a creator and a patron/client can agree on work and payment without trusting each other or a platform.

Proposed flow:

```
Patron creates deal (creator, amount, token, deadline, milestones)
   → Patron deposits funds
   → Creator accepts
   → Creator delivers (hash/link of work)
   → Patron releases   ──or──  deadline passes → auto-release to creator
                       ──or──  dispute → arbitration
```

Rules:
- Funds never sit in an account the Order controls; only in the deal contract.
- Creator keeps authorship of the work in every outcome.
- Either party can cancel **before** acceptance and get funds back.
- **Order fee — proposed default: 0%** at launch, to earn the first users' trust. Any future fee is a `both`-scope decision and goes to the treasury.

**Disputes — proposed default:** a panel of **three Inquisitors** not connected to either party, decision by majority within 14 days, reasoning published. As volume grows, move to an external arbitration protocol (e.g. Kleros) so the Order is not judge in its own house.

## 5. Chambers and decisions

From the [structure](https://cirqusheresy.com/structure):

- Each chamber decides its internal matters by its own rules.
- A decision that affects one chamber requires that chamber's consent.
- A decision that affects both chambers or the whole Order requires the consent of both.
- Neither chamber is subordinate to the other.

Proposed mechanics:
- **Creative Chamber vote:** one Seal holder = one vote (not one Seal = one vote — holding five Seals does not multiply your voice). **[ARCHITECT]** how to enforce one-person-one-vote without doxxing.
- **Leverage Chamber vote — proposed default:** one Mage = one vote. Capital does **not** weight votes, even inside the Leverage Chamber — *capital strengthens the Order, it does not buy command of it.*
- **Scope tag** on every proposal: `creative`, `leverage`, `both`. Wrong scope can be challenged by either chamber.
- Start **off-chain** (Snapshot with Seal-based strategy), move on-chain once stable.

## 6. Hexastorm

Six seats, one per sign. The Hexastorm coordinates, frames proposals and helps resolve tensions; it **holds no automatic power** over the chambers.

On-chain footprint (minimal): a 6-seat registry and the ability to *publish* proposals to both chambers. No treasury keys by default.

## 7. Treasury

- **Proposed default:** Safe multisig on Base, **2-of-3** at start (founder + two members from different signs), growing to 3-of-5 as the Hexastorm fills.
- Spending from the treasury is a `both`-scope decision.
- All addresses and movements are published in [`governance/treasury`](https://github.com/CirqusHeresy/governance/tree/main/treasury).

## Open questions

1. Seal granting threshold and revocation — proposed default in §3; open to challenge.
2. Escrow fee and dispute arbitration — proposed default in §4; open to challenge.
3. Capital weighting in the Leverage Chamber — proposed default: no (§5).
4. One-person-one-vote: proof-of-personhood option (Gitcoin Passport, World ID, social vouching) vs. accepting Sybil risk while the Order is small.
5. Stack: Solidity/Foundry on Base assumed — any reason to choose otherwise?
6. Upgradeability: immutable contracts with migration, or upgradeable proxies with a timelock?

Each question has (or will have) its own issue labelled `spec`.
