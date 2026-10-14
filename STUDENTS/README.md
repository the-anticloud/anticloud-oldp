# Students — OLDP

**Project:** OLDP  
**Category:** LEGAL_TECH  
**Upstream:** see BENCH.json  
**Pinned commit:** `c4b739616bf8a3780206e3c009b5550c9e7cbe8c`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `9f49a828b3138dae5e23258a3e0fd8f56267c3ce65a7d37db13f3ba4b89db5e1`  
**Date:** October 2026

## What this project gives you

A complete worked example of offline-first packaging with a cryptographic audit
chain: source pinned at `c4b739616bf8a3780206e3c009b5550c9e7cbe8c`, a 16-check assurance suite, an evidence register
with per-check hashes, and an AIOSS ledger chain ending at `9f49a828b3138dae5e23258a3e0fd8f56267c3ce65a7d37db13f3ba4b89db5e1`.

## Learn by verifying

```
python tools/run_bench.py --out BENCH.json
```

Then take any row from `ISOLATED_LAB_RESULTS/03_Result_Register.md`, recompute
the SHA3-256 of its evidence file, and confirm it matches. If it does not match,
the record has been altered — that is the whole point of the chain.

## Licence

Apache 2.0 terms apply to study and teaching use.
