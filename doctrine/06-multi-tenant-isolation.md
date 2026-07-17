# 06 — Multi-Tenant Isolation by Construction

**No cross-tenant leakage, no replay.**

Every request binds to a tenant at issuance. Policy set, authorization
artifact, audit chain, and decision hash are all tenant-scoped. An artifact
issued for one tenant cannot authorize execution for another, and a decision
cannot be replayed — the binding is cryptographic, not administrative.

**Corpus:** DOI — *add Zenodo DOI here*.
