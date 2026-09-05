# 05 — Named Cryptography, Not Implied

**Every chain names its own primitives, and each one is checkable separately.**

There are three hash chains in this system. They are different structures with
different threat models, they make different choices, and each is stated here
rather than summarised into a single claim that would be accurate about only
one of them.

| Chain | Where it runs | What it computes | How you check it |
| --- | --- | --- | --- |
| **EA-11 evidence** | control plane | SHA-512 at every layer, at schema version `EA11_EVIDENCE_STATE_V2_2`. BLAKE2b-512 is declared in the state metadata and is not computed. | Recompute the five component hashes and the Merkle root from a live record: [`/v1/public/proof-ledger`](https://control.11aiblockchain.com/v1/public/proof-ledger) |
| **RFC-EG-0010 lineage** | reference verifier | SHA3-512 **and** BLAKE2b-512, genuinely dual: every event carries both chain hashes and each is verified independently. | Run the verifier against the published example and tampered documents: [11-11-lineage-verifier](https://github.com/11-11AI/11-11-lineage-verifier) |
| **SDK receipts** | `@11ai/execution-governance`, on your machine | SHA3-512 over canonical JSON, Ed25519 signed, chained. | `eg-verify`, or the offline browser verifier: [hosted](https://11-11ai.github.io/execution-governance/verify/) |

Authorization artifacts are Ed25519 throughout. A hybrid post-quantum signature
envelope (**ML-DSA-87** / FIPS 204 and **SLH-DSA-SHA2-128f** / FIPS 205
SPHINCS+) covers the EA-11 evidence root.

Reviewers do not have to guess, and the parameter sets are stated exactly as
deployed. Where a chain does not do something — BLAKE2b-512 on the EA-11
chain — that is stated too, because a primitive named in metadata and not
computed is worse than one never mentioned.

**Verify:** the Ed25519 signature can be checked on your own machine from the
public JWKS and the evidence record —
[verify-11ai-proof](https://github.com/11-11AI/verify-11ai-proof).

Keys are published on a channel separate from the artifacts they authenticate.
Ed25519 is served from the standard JWKS location, and the post-quantum public
keys from [`/v1/public/keys`](https://control.11aiblockchain.com/v1/public/keys).
Pin from those endpoints. The same post-quantum keys also travel inside the
evidence record for convenience, but a key taken from the document it signs
proves only internal consistency, never authenticity — so verify against the
published endpoint, not the embedded copy.

The post-quantum keys are not yet in JWKS. RFC 9964 (May 2026) registers
`kty: "AKP"` and `alg: "ML-DSA-87"` for JOSE, so ML-DSA can now be served there
in standard form; SLH-DSA has no JOSE registration yet.

**Corpus:** DOI — [10.5281/zenodo.20277892](https://doi.org/10.5281/zenodo.20277892) (RFC-EG-0300); [10.5281/zenodo.20836771](https://doi.org/10.5281/zenodo.20836771) (RFC-EG-0301).
