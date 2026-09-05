# 04 — Immutable Execution Lineage

**Every decision chained, hashed, permanently recorded.**

Each governance decision produces an EA-11 Evidence State: decision hash,
artifact hash, execution hash, audit hash, and lineage root, committed under a
Merkle evidence root. Tampering with any component breaks the chain and is
independently detectable against the public proof endpoint.

Records at schema version `EA11_EVIDENCE_STATE_V2_2` compute SHA-512 at every
layer. BLAKE2b-512 is declared in the state metadata and is not computed.

The RFC-EG-0010 execution lineage chain is a separate structure and is
genuinely dual-hashed: every event carries both a SHA3-512 and a BLAKE2b-512
chain hash, each verified independently. See
[the lineage verifier](https://github.com/11-11AI/11-11-lineage-verifier).

**Verify:** fetch a live evidence record and recompute the five component
hashes and the Merkle root yourself:
[`/v1/public/evidence`](https://control.11aiblockchain.com/v1/public/evidence).
Each component hash is SHA-512 over its canonical state; the Merkle root pairs
them as `SHA-512(left + ":" + right)`, duplicating the odd node. The evidence
root additionally commits a state hash that is not currently published, so it is
not recomputable by a third party today. That is stated here rather than left
for a reviewer to discover.

**Corpus:** DOI — [10.5281/zenodo.20264726](https://doi.org/10.5281/zenodo.20264726).
