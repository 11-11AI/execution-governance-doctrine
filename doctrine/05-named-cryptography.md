# 05 — Named Cryptography, Not Implied

**Ed25519, SHA3-512, BLAKE2b-512 — stated at every layer.**

The exact primitives used in the control plane are published, not implied:
Ed25519 authorization artifacts, SHA3-512 + BLAKE2b-512 evidence chaining, and
a hybrid post-quantum signature envelope (ML-DSA-65 / FIPS 204 and SLH-DSA /
FIPS 205 SPHINCS+) over the EA-11 evidence root. Reviewers do not have to
guess, and every signature can be re-verified offline.

**Verify:** the public JWKS and evidence record are enough to check the
signatures on your own machine —
[verify-11ai-proof](https://github.com/AtlasQuantumProtocol/verify-11ai-proof).

**Corpus:** DOI — [10.5281/zenodo.20277892](https://doi.org/10.5281/zenodo.20277892) (RFC-EG-0300); [10.5281/zenodo.20836771](https://doi.org/10.5281/zenodo.20836771) (RFC-EG-0301).
