# Graham–Alspach sequenceability certificates

The computational certificate bank for verified Graham–Alspach sequenceability ranges in nine prime cyclic groups.

A subset `A⊂Z_p\setminus\{0\}` is sequenceable when its elements admit an ordering whose partial sums are pairwise distinct and whose proper partial sums are nonzero.

## Certified ranges

The bank exhaustively covers:

- `Z_29`: subset sizes **21–28**;
- `Z_31`: subset sizes **21–30**;
- upper-cardinality ranges in `Z_37`, `Z_41`, `Z_43`, `Z_47`, `Z_59`, `Z_61`, and `Z_73`.

`Z_29` alone contains **60,134 certificate rows**.

Published general results cover all subset sizes at most 20; these certificates address finite ranges beyond that threshold.

## Certificate construction

Multiplication by a nonzero residue preserves sequenceability. The generator therefore works orbit-by-orbit:

1. choose one canonical representative from each multiplicative orbit;
2. store the exact subset and an explicit sequencing witness;
3. recover the remaining orbit by scaling;
4. verify that the orbit sizes sum to the full binomial count for the cardinality.

This reduces a complete finite classification to a certificate for every orbit representative plus exact coverage accounting.

## Independent verification

Two separate verifiers check the bank.

The Go verifier:

- validates every sequencing witness;
- validates scaled witnesses;
- reconstructs coverage in a `2^28`-bit universe;
- rejects duplicate coverage;
- checks the exact binomial totals.

The Python verifier independently recomputes canonical representatives and stabilizers, validates every witness, and verifies disjoint orbit coverage by exact orbit-size accounting.

Both implementations reject deliberately corrupted certificates included with the test data. Regeneration with different thread counts produces the same certificate hash.

## Lean companion

The corresponding Lean witness files are in [`graham-alspach-sequenceability`](https://github.com/jaredwilder/graham-alspach-sequenceability). They use the standard Mathlib classical axioms together with `native_decide` for the finite witness evaluations.

Larger verified ranges and explicit high-cardinality witnesses are in [`graham-alspach-z53-z71`](https://github.com/jaredwilder/graham-alspach-z53-z71) and [`graham-alspach-extended`](https://github.com/jaredwilder/graham-alspach-extended).

Author: Jared Wilder. License: Apache-2.0.
