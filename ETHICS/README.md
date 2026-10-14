# Ethics — OLDP

**Project:** OLDP  
**Category:** LEGAL_TECH  
**Upstream:** see BENCH.json  
**Pinned commit:** `c4b739616bf8a3780206e3c009b5550c9e7cbe8c`  
**Assurance:** 16/16 checks passing  
**Ledger head:** `9f49a828b3138dae5e23258a3e0fd8f56267c3ce65a7d37db13f3ba4b89db5e1`  
**Date:** October 2026

## Position

OLDP is packaged for offline deployment with a verifiable audit trail. The
ethical questions this raises are answered by making the system's behaviour
checkable rather than by policy statements.

## The four commitments

1. **No hidden egress.** The deployment has no external API dependency; this is
   testable by running it with the network disconnected.
2. **Attributable output.** Every artifact is recorded in a hash chain, so what
   the system produced can be reconstructed.
3. **Operator control.** The institution owns the hardware and the keys.
4. **Refusal to overclaim.** Where a certification is not held, the project says
   so rather than implying it.

## Dual use

This project is packaged for civilian and public-sector deployment. Where an
upstream has dual-use characteristics, the licence gate and the reference-only
marking in `BENCH.json` record that.
