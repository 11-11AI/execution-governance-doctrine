# 03 — Fail-Closed Operational Semantics

**Default is deny when policy, identity, or proof is absent.**

If the control plane is unreachable, the action does not proceed. Absence of
authorization is a denial, not a default-allow. Downtime degrades to "nothing
executes," never to "everything executes." Both ALLOW and DENY paths are
signed and persisted — a denial is as provable as an approval.

**Verify:** [system status](https://control.11aiblockchain.com/health) and
denial events in the [briefings](https://www.11aiblockchain.com/executionbriefings).

**Corpus:** DOI — [10.5281/zenodo.20252295](https://doi.org/10.5281/zenodo.20252295).
