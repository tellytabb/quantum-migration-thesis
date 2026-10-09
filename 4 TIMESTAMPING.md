# Timestamping runbook — Quantum Migration Thesis, v1.0-public-draft

**Goal:** produce three independent, checkable witnesses that `manifesto-public.md`
existed in October 2026: a GitHub commit, a Bitcoin-anchored OpenTimestamps
proof, and an ICP canister record. Run in this order. Do NOT announce until all
three verify.

**Prerequisites:** `git`, the `ots` CLI (`pip install opentimestamps-client`),
and `dfx` (for the ICP step). Work from the repo root.

## 1. Create the repository (no remotes until reviewed)

```bash
cd ~/workspace/quantum-flag/github
git init
git add README.md manifesto-public.md MANIFEST.json TIMESTAMPING.md .gitignore
git -c user.name="ROYALTY T.A.B.B Ent." commit -m "Quantum Migration Thesis v1.0-public-draft — flag planted"
git log --format='%H %ad' --date=iso  # record the commit hash
```

Create the remote repo (web UI or `gh`), then — only after partner approval:

```bash
git remote add origin <repo-url>
git branch -M main
git push -u origin main
```

Record the commit hash in `MANIFEST.json` under `witnesses.github` and set its
status to `done`.

## 2. Stamp with OpenTimestamps (Bitcoin-anchored)

```bash
cd ~/workspace/quantum-flag/github
ots stamp manifesto-public.md
# -> creates manifesto-public.md.ots (a pending timestamp; the Bitcoin
#    attestation completes when the next calendar-server batch confirms)
```

Wait for the attestation to confirm (the `ots` client will tell you; typically
within a day), then upgrade and verify:

```bash
ots upgrade manifesto-public.md.ots
ots verify manifesto-public.md.ots
# -> expected: "Success! Bitcoin block <height> attests existence as of <date>"
```

Commit the `.ots` file:

```bash
git add manifesto-public.md.ots
git commit -m "Add OpenTimestamps proof for v1.0-public-draft"
git push
```

Set `witnesses.opentimestamps.status` to `done` in `MANIFEST.json` and commit
that change too.

## 3. Anchor the hash in an ICP canister

Deploy (or reuse) a minimal canister holding a single record: the manifest
SHA-256, the GitHub commit hash, and the OTS proof reference.

```bash
# from your dfx project dir
dfx deploy thesis_anchor
dfx canister call thesis_anchor record \
  '(record { sha256 = "633fe28c1f8cc9cf74e2913c8035fc20712b54604e98ad6188bae8f651bfb5a2";
             version = "1.0-public-draft";
             github_commit = "<commit-hash>";
             ots_proof = "manifesto-public.md.ots" })'
dfx canister call thesis_anchor get  # confirm the record + chain timestamp
```

Record the canister ID in `MANIFEST.json` under `witnesses.icp_canister`,
set status to `done`, commit, push.

## 4. Final verification (before any announcement)

```bash
sha256sum manifesto-public.md   # must match MANIFEST.json sha256
ots verify manifesto-public.md.ots
dfx canister call thesis_anchor get
git log --oneline -3
```

All four green → announce. Every announcement links the repo, so skeptics can
re-run these exact commands themselves.
