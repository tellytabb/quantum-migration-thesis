> **Publisher of record:** ROYALTY T.A.B.B Ent. · October 2026 · Version 1.0-public-draft
> *(Byline is provisional — change this line to update everywhere.)*

# The Quantum Migration Thesis

*Plant the flag now. Sell the shovels that pay today. Be standing when the panic arrives.*

## The attack has already started

You don't need to predict the year a cryptographically relevant quantum computer arrives. The most important move in this game already happened — quietly, years ago.

It's called **harvest now, decrypt later**. Adversaries capture encrypted traffic, files, and wallet backups today, store them cheaply, and wait. Any secret that must stay secret past the mid-2030s is already exposed if it travels under RSA or elliptic-curve protection right now.

Read that again. The quantum attack isn't waiting for quantum computers. It's already in progress.

## The clock is official

In August 2024, the U.S. National Institute of Standards and Technology (NIST) finalized its first three post-quantum cryptography standards: FIPS 203 (ML-KEM) for key establishment, FIPS 204 (ML-DSA) for signatures, and FIPS 205 (SLH-DSA) for hash-based signatures.

Then NIST IR 8547 set the retirement clock: RSA, ECDSA, EdDSA and related algorithms are **deprecated after 2030 and disallowed after 2035** in federal systems — and every vendor selling into those systems follows the same clock.

Migration across industry is a decade-long engineering program. Starting in 2026 isn't early speculation. It's starting on time, while everyone else waits for a headline.

## The fault line is signatures

Here's the precision that matters: this is not "quantum breaks everything." AES-256 file encryption remains the accepted post-quantum baseline — Grover's algorithm only halves symmetric strength. The break risk concentrates in **public-key signatures and key exchange**.

And that is exactly where the money sits. Bitcoin and Ethereum wallets rely on ECDSA. A sufficiently capable quantum computer running Shor's algorithm breaks that scheme. Wallets whose public keys are already exposed on-chain — for example, after spending from an address — carry the highest theoretical exposure. Coins at addresses that never spent, where only a hash of the public key is visible, keep an extra layer of protection until they move.

The thesis that overstates the threat gets ignored. The thesis that names the exact fault line gets cited.

## What "quantum-ready" actually means

Quantum-ready is not a single algorithm. It's three engineering properties — and anything we ship under that label has all three or says plainly which it lacks.

**1. Crypto-agility.** Every signature and key-exchange choice sits behind a configuration boundary, so an algorithm swaps without rebuilding the product. If swapping algorithms means rewriting the app, the app is not ready.

**2. Hybrid by default.** During transition, pair classical with post-quantum (X25519 + ML-KEM-768, for example) so the connection holds if either leg holds. Hybrid is the industry migration pattern — not an exotic choice.

**3. Conservative roots.** Where a signature must be trusted for decades — ownership records, vault root keys — prefer the most conservative option available. SLH-DSA signs using only hash functions, with no lattice assumptions. Slower, larger — and the right trade for root-of-trust material.

And the boundary we state once and apply everywhere: we describe systems as *post-quantum-aligned*, *crypto-agile*, or *migration-ready*. We never market anything as "quantum-proof," "unhackable," or "cannot be penetrated." Those words are how projects lose trust — and they are never true of any implemented system.

## Why we build on the Internet Computer

Everything we build lives on ICP. That's not brand loyalty — it solves the ownership problem at the protocol level.

**True controller ownership.** An ICP app lives in a canister, and a canister has controllers. Whoever holds controller keys can upgrade, stop, or delete it. Transfer controllers to the user's own principal, retain none, and the platform can't reach the app afterward. Downloadable source plus controller transfer plus no forced badge — a stronger ownership claim than any Web2 builder can make.

**Threshold custody substrate.** ICP's chain-key infrastructure lets a subnet hold key shares so no single node ever possesses the whole secret. vetKeys — live on mainnet since July 2025 — lets a canister derive keys delivered encrypted to the client, so secrets can be managed without any node, or the canister itself, seeing raw key material. That's the substrate for custody and vault designs.

**Honest porting.** A generated frontend lifts cleanly into an asset canister. A full-stack backend doesn't copy-paste — it's re-homed as a Motoko or Rust canister or bridged through HTTPS outcalls. We plan for re-homing, budget for it, and the ownership promise stays honest.

## Two games — we play the shovels first

**Game A** is the quantum-born asset: a ledger with post-quantum signatures from its first block. Buildable as architecture today. But Bitcoin's lesson is that cryptography was only the entry ticket — Bitcoin won on fixed scarcity, a decade of uninterrupted operation, and network effect. A new asset has none of those on launch day.

**Game B** is the transition business: when value must move to quantum-safe rails — deadline compliance, institutional policy, or eventual public alarm — whoever operates the trusted vaults, migration tooling, and proof services captures fees from the movement itself, regardless of which asset wins. In a gold rush, the shovel seller gets paid by every miner, including the ones who find nothing.

So we blueprint and timestamp Game B now, and keep Game A as a researched option only. **No coin or token is launched, pre-sold, or promised by this thesis.** Any future asset design would require explicit authorization, independent legal review, and a transparent structure published before any public discussion of value. That boundary is a feature, not a gap.

## Phase 1a: plant the flag

Bitcoin's "I told you so" worked because priority was provable. So we make ours provable too:

1. Publish this thesis with a version number and date.
2. Open-source the reference work in a public repository.
3. Anchor the document hash with OpenTimestamps — aggregated into a Bitcoin transaction, so the block timestamp becomes third-party evidence these exact bytes existed on this date. Evidence no one, including us, can backdate.
4. Anchor the same hash inside an ICP canister we control — the on-chain receipt on our home chain. Two independent witnesses beat one.
5. Announce last — only after every step verifies, with every claim linking back to the timestamps.

Total cost: roughly $0–$2,000. The flag-plant is deliberately cheap. The expensive part — a production vault — comes later, funded by business revenue, with an independent security audit that is non-negotiable before it touches real funds.

## Phase 2: shovels that pay today

We don't need a panic for Phase 2. The NIST 2030/2035 clock is already forcing inventories and budgets inside enterprises and custodians. Four offers monetize that pressure now:

- **Quantum-safe custody and inheritance vaults** — non-custodial by design; we sell setup and recovery planning, never hold funds or keys.
- **Migration assessments and crypto-agility audits** — fixed-fee engagements inventorying RSA/ECDSA exposure and delivering sequenced roadmaps. Fastest to revenue.
- **Quantum-safe proof-of-ownership for creators** — timestamped, hash-anchored, PQC-signed records for books, music, art. Our home field.
- **Migration tooling for ICP builders** — crypto-agility wrappers and owner-key upgrade flows, licensed as developer tooling.

Fees for setup, assessment, and assurance. Never a percentage of assets. Never returns language. Fees arrive in quiet years — which is the entire point.

## What we will not claim or do

- No "unhackable," "quantum-proof," or "cannot be penetrated." Ever.
- No token launch, pre-sale, or promise.
- No custody of third-party funds before independent audit and legal review are complete in writing — and "non-custodial" must mean custody is technically impossible for us, not merely promised.
- No performance promises, no return projections, no urgency marketing. The thesis wins by being checkable, not by being loud.

## The chess read

They play checkers: react to the headline, scramble for the migration, pay panic prices. We play chess: timestamp the thesis while it's still quiet, sell the shovels the deadline already pays for, and let the boom arrive on its own schedule — to find us already standing on the other side.

Ten cars ahead isn't a slogan. It's a sequence: **proof, then community, then revenue, then — only when funded and audited — the vault.**

---

## Verify this document

This thesis is timestamped so that the claim "we said this in October 2026" is checkable by any skeptic in under a minute.

**1. Check the hash.** Compute the SHA-256 of this file:

```
sha256sum manifesto-public.md
```

Compare the output to the `sha256` field in `MANIFEST.json` (published alongside this document). If they match, you hold the exact bytes we timestamped.

**2. Check the Bitcoin anchor.** The manifest's hash is stamped with OpenTimestamps, which aggregates it into a Bitcoin transaction. To verify independently:

```
ots verify manifesto-public.md.ots
```

This confirms the document existed no later than the Bitcoin block timestamp in the proof — an anchor no one, including us, can backdate.

**3. Check the ICP anchor.** The same SHA-256 hash is stored in an ICP canister we control (canister ID published in the repository). Querying it returns the hash and the chain timestamp of the record — a second, independent witness on our home chain.

Two witnesses. One claim. Check it yourself — that's the whole point.

---

*ROYALTY T.A.B.B Ent. · October 2026 · Version 1.0-public-draft*
*This document is an architecture and options paper. It is not investment advice, not a token offering, and not legal advice.*
