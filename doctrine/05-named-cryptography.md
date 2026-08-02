# 05 — Named Cryptography, Not Implied

**Ed25519, SHA3-512, BLAKE2b-512 — stated at every layer.**

The exact primitives used in the control plane are published, not implied:
Ed25519 authorization artifacts, SHA3-512 + BLAKE2b-512 evidence chaining, and
a hybrid post-quantum signature envelope (**ML-DSA-87** / FIPS 204 and
**SLH-DSA-SHA2-128f** / FIPS 205 SPHINCS+) over the EA-11 evidence root.
Reviewers do not have to guess, and the parameter sets are stated exactly as
deployed.

**Verify:** the Ed25519 signature can be checked on your own machine from the
public JWKS and the evidence record —
[verify-11ai-proof](https://github.com/AtlasQuantumProtocol/verify-11ai-proof).

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
