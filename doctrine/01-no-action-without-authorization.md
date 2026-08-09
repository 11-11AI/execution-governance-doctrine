# 01 — No Action Without Authorization

**Execution is impossible without an issued authorization.**

An action attempted by an AI system is not evaluated after the fact; it does not
occur at all unless a signed authorization artifact exists for that specific
request. The artifact binds identity, action, environment, and tenant. No
artifact, no execution — by construction, not by convention.

Logs are not authorization. Observation is not enforcement. Post-hoc review is
not control.

**Verify:** every decision issued by the live control plane carries an Ed25519
authorization artifact. [Run the verifier](https://github.com/11-11AI/verify-11ai-proof).

**Corpus:** DOI — [10.5281/zenodo.20252639](https://doi.org/10.5281/zenodo.20252639).
