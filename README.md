# ⬡ Cirqus Heresy — Protocol

*Non Somniamus Mundos. Eos Codicamus.* — We do not dream worlds. We code them.

The on-chain mechanics of the Order of Choice: who is a member, how contribution is recognised, how creators and patrons exchange value safely, and how two chambers decide together.

> **Status: specification.** One piece is live (Temple NFT on Base). The rest is designed here, in the open, before a line of contract code is written. This is where the Architect starts.

## Components

| # | Component | What it does | Status |
|---|---|---|---|
| 1 | **Temple** | Outer Ring artifact for Seekers. Open mint. | 🟢 Live on Base |
| 2 | **Seals** | Non-transferable marks of a sign (Trickster … Mage), granted for contribution | 📐 Spec |
| 3 | **Escrow** | Holds funds between a creator and a patron/client until agreed work is delivered | 📐 Spec |
| 4 | **Chambers** | Two-chamber consent voting: Creative and Leverage | 📐 Spec |
| 5 | **Hexastorm** | Six-seat coordination council, no automatic power over chambers | 📐 Spec |

Full design: **[SPEC.md](SPEC.md)**. Unresolved decisions: **[open questions](SPEC.md#open-questions)** and the [`spec`](../../issues?q=is%3Aopen+label%3Aspec) issues.

## Design principles

Taken directly from the [Manifesto](https://cirqusheresy.com/manifesto) — every mechanism must pass them:

1. **Creator sovereignty** — the protocol never takes custody of a creator's work or authorship.
2. **Real exit** — leaving must always be possible. No lock-in, no hostage funds.
3. **Capital is not command** — the Leverage Chamber cannot outvote the Creative Chamber.
4. **Understandable mechanisms** — consequential logic must be readable by members, not only by auditors.
5. **Tested before trusted** — nothing ships without review by the Inquisition.

## How to contribute

- Read [SPEC.md](SPEC.md). Disagree with it — in an issue.
- Pick a [`help wanted`](../../issues?q=is%3Aopen+label%3A%22help+wanted%22) issue.
- Planned stack: Solidity + Foundry, Base (L2), OpenZeppelin libraries. Open to argument — see open questions.

See [CONTRIBUTING](https://github.com/CirqusHeresy/.github/blob/main/CONTRIBUTING.md) and [SECURITY](https://github.com/CirqusHeresy/.github/blob/main/SECURITY.md).

## Looking for an Architect

We are looking for a **technical co-founder** to own this repository. If you read the spec and already see how you'd build it — write via [cirqusheresy.com/enter](https://cirqusheresy.com/enter).

## License

[MIT](LICENSE). Paid services of the Order (e.g. Inquisition incident response, Arsenal assays) are built **on top of** this open protocol and are not part of this repository.
