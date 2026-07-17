# 02 — Authorize Before Execute

**Governance is evaluated before the action runs.**

Today's AI stack executes first and inspects later; by the time misuse or drift
is detected, the action has already reached the real world. Execution
Governance reverses the order: identity and policy are evaluated pre-execution,
deterministically, typically in under 100 ms, and the decision is enforced at a
runtime boundary the action cannot bypass.

**Verify:** submit a request to the authenticated gateway and observe the
signed ALLOW/DENY decision precede any effect.
[Live demo](https://control.11aiblockchain.com/demo).

**Corpus:** DOI — *add Zenodo DOI here*.
