# Graham–Alspach sequenceability certificates

The complete computational certificate bank behind the Graham–Alspach sequenceability results for nine primes, together with independent verification and deliberately corrupted controls.

Author: Jared Wilder. First public timestamp: 2026-09-10. Work dated 2026-07.

## The statement being certified

For the finite cyclic groups covered here, every subset `A ⊂ Z_p \ {0}` in the stated cardinality range admits an ordering `a_1,…,a_m` whose partial sums are pairwise distinct and whose proper partial sums are nonzero.

Published general results cover every subset of size at most 20. These certificates exhaustively cover:

- **sizes 21–28 in `Z_29`**;
- **sizes 21–30 in `Z_31`**;
- further upper-size ranges in `Z_37`, `Z_41`, `Z_43`, `Z_47`, `Z_59`, `Z_61`, and `Z_73`.

`Z_29` alone contains **60,134 certificate rows**.

## Certificate structure

The computation uses multiplicative symmetry:

1. multiplication by a nonzero residue preserves sequenceability;
2. the generator chooses one canonical representative from each multiplicative orbit in every target cardinality;
3. each representative stores its exact subset, total sum, and an explicit sequencing witness.

So the key correctness question is not the raw row count but whether the representatives cover every orbit exactly as claimed.

## Independent verification

Two independently written verifiers check the certificates.

The **Go verifier** validates every representative witness, every scaled witness, reconstructs coverage in a `2^28`-bit universe, rejects duplicate coverage, and checks exact binomial totals.

The **Python verifier** independently recomputes canonical representatives and stabilizers, validates each witness, and checks disjoint orbit coverage by exact orbit-size accounting.

Both verifiers reject four classes of deliberately corrupted certificate. Those controls live in `certificates/graham-z29/adversarial-certificate-tests.json` and its v2 companion.

Regeneration at 48 threads and at 16 threads produces the same certificate hash.

## Lean verification boundary

The companion Lean files use Mathlib's three standard classical axioms plus one `native_decide` evaluation per witness. That means the finite witness computation is compiler-evaluated rather than reduced entirely by the kernel.

The Lean sources are in `jaredwilder/graham-alspach-sequenceability`; the mathematical writeup and compiled PDF are in `jaredwilder/unpublished-math-papers`.

## License

Apache-2.0.