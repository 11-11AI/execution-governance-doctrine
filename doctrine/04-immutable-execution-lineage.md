# 04 — Immutable Execution Lineage

**Every decision chained, hashed, permanently recorded.**

Each governance decision produces an EA-11 Evidence State: decision hash,
artifact hash, execution hash, audit hash, and lineage root, chained with
SHA3-512 + BLAKE2b-512 and committed under a Merkle evidence root. Tampering
with any component breaks the chain and is independently detectable against
the public proof endpoint.

**Verify:** fetch a live evidence record and check the component hashes and
evidence root yourself:
[`/v1/public/evidence`](https://control.11aiblockchain.com/v1/public/evidence).

**Corpus:** DOI — *add Zenodo DOI for the EA-11 lineage architecture here*.
