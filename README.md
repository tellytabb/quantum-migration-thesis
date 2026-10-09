# Quantum Migration Thesis — public proof repository

This repository holds the public version of **The Quantum Migration Thesis** (ROYALTY T.A.B.B Ent., October 2026): an architecture and options paper for building quantum-era-ready products on the Internet Computer Protocol — with a timestamped proof plan and a Phase 2 revenue plan that does not depend on panic.

## The thesis in one paragraph

Harvest-now-decrypt-later attacks are already live. NIST finalized post-quantum standards (FIPS 203/204/205) in August 2024 and set a deprecate-after-2030 / disallow-after-2035 clock on RSA and ECDSA. The fault line is signatures — including the ECDSA guarding Bitcoin and Ethereum wallets. "Quantum-ready" means crypto-agility, hybrid-by-default, and conservative hash-based roots (SLH-DSA) — never "unhackable." We build on ICP because canister controller transfer makes ownership literal. We play the shovel game first: vaults, migration audits, and proof-of-ownership services that earn fees in quiet years. No token is launched, pre-sold, or promised.

## Verify the timestamp

The claim "we said this in October 2026" is checkable in under a minute:

1. `sha256sum manifesto-public.md` — compare against `sha256` in `MANIFEST.json`.
2. `ots verify manifesto-public.md.ots` — confirms the document existed no later than the Bitcoin block timestamp in the proof.
3. Query the ICP canister (ID in `MANIFEST.json` once deployed) for the same hash — a second, independent witness.

Two witnesses. One claim. Check it yourself — that's the whole point.

## Contents

- `manifesto-public.md` — the public thesis
- `MANIFEST.json` — SHA-256 hash, version, and witness status
- `manifesto-public.md.ots` — OpenTimestamps proof (added at stamp time)
- `TIMESTAMPING.md` — the exact runbook used to create this proof stack

## Boundaries

This repository is an architecture and options paper. It is not investment advice, not a token offering, and not legal advice. Nothing here is described as unhackable or quantum-proof.
