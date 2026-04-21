# PABRS Evaluation Artifact

This artifact provides a reproducible benchmark scaffold for a **functional PABRS emulator**.
It is intended for reviewers and GitHub release.

## Scope

This artifact does **not** implement the full pairing-based cryptographic construction from the paper.
It implements:

- a deterministic workload generator for cross-domain ABAC requests
- a functional PABRS-style emulator with context binding, issuer checks, user-binding checks, policy checks, revocation checks, and nonce replay protection
- attack-oriented tests
- runtime and size benchmarks over configurable parameter sweeps
- CSV outputs, plots, and a Markdown summary

The measured times therefore reflect a **reproducible protocol emulator and workload harness**, not a production cryptographic implementation.

## Repository Layout

- `src/pabrs_eval/` core package
- `scripts/run_all.py` one-command benchmark runner
- `results/` generated CSV files, plots, and summary

## Quick Start

```bash
python -m pip install -r requirements.txt
python scripts/run_all.py --output results
```

## Reproducibility

- fixed RNG seed
- deterministic workload generation
- explicit configuration in `scripts/run_all.py`
- CSV files for all tables and figures

## Main Outputs

- `results/benchmark_results.csv`
- `results/attack_results.csv`
- `results/summary.md`
- `results/plots/*.png`

## Claims Supported by This Artifact

1. Valid proofs are accepted by the emulator.
2. Invalid proofs are rejected under replay, revocation, collusion, wrong-issuer, and malformed-proof attacks.
3. Signing and verification cost increase with policy size, issuer count, credential count, and revocation-set size.
4. Proof size increases with slot bound and credential use.

## Reviewer Notes

This artifact is suitable for:

- workload reproduction
- attack reproduction
- table and figure regeneration
- code inspection

This artifact is **not** a replacement for a cryptographic library implementation over bilinear pairings.


## Experimental discussion comparison

- `results/experimental_discussion_comparison.tex`
- `results/experimental_discussion_comparison.md`
