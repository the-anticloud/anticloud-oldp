# Educators — OLDP

**Project:** OLDP  
**Category:** LEGAL_TECH  
**Upstream:** see BENCH.json  
**Pinned commit:** `c4b739616bf8a3780206e3c009b5550c9e7cbe8c`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `9f49a828b3138dae5e23258a3e0fd8f56267c3ce65a7d37db13f3ba4b89db5e1`  
**Date:** October 2026

## Teaching with OLDP

The project is usable as a worked example of offline-first packaging with a
cryptographic audit chain. It ships with the assurance suite, the evidence
register and the ledger, so students can verify claims rather than take them on
faith.

## Suggested exercises

1. Run `python tools/run_bench.py --out BENCH.json` and read the 16 results.
2. Recompute the SHA3-256 of a row's evidence file and compare to the register.
3. Walk the AIOSS chain from genesis to head `9f49a828b3138dae5e23258a3e0fd8f56267c3ce65a7d37db13f3ba4b89db5e1` and confirm every link.
4. Break one artifact and observe the chain fail to verify.

## Licence for teaching

Apache 2.0 terms apply to academic and teaching use. See `24_ANTICOMMONS_LICENSE`.
