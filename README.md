# graham-alspach-certificates

The full computational certificates behind the Graham / Alspach sequenceability results, for nine
primes, with the adversarial tests that try to break them.

Author: Jared Wilder. First public timestamp: 2026-09-10. Work dated 2026-07.

## The theorem certified

Every subset A of Z_p minus {0} admits an ordering a_1, ..., a_m whose partial sums are pairwise
distinct and whose proper partial sums are nonzero.

**Published general results cover every subset of size at most 20.** These certificates
exhaustively cover the remaining sizes: **21 through 28 for Z_29**, and **21 through 30 for Z_31**,
with further coverage for Z_37, Z_41, Z_43, Z_47, Z_59, Z_61 and Z_73.

Z_29 alone carries **60,134 certificate rows**.

## How the certificate is structured, and why that matters

1. Multiplication by a nonzero residue preserves sequencing: a witness for A scales to a witness
   for uA.
2. The generator emits **one canonical representative per multiplicative orbit** in every target
   cardinality.
3. Each row carries the exact set, its total, and an explicit ordering.

So the certificate is small relative to the space it covers, and the covering argument is the thing
a referee must check, not the row count.

## What checks it

**Two independent verifiers in different languages.**

The Go verifier validates every representative witness, validates every scaled witness for every
unit, reconstructs every covered subset in a 2^28-bit universe, rejects duplicate coverage, and
checks exact binomial totals.

The Python verifier independently recomputes canonical representatives and stabilizers, validates
every representative witness, and proves disjoint orbit coverage by exact orbit-size accounting.

**Four classes of deliberately corrupted certificate are rejected by both.** Those adversarial
tests are in `certificates/graham-z29/adversarial-certificate-tests.json` and the v2 file, and they
are the reason to believe the verifiers do anything.

**Regeneration at 48 threads and at 16 threads produces the identical certificate hash.**

## The trust assumption, again

The Lean side of this work carries the three standard axioms plus exactly one `native_decide` per
witness. `native_decide` asks the compiler to evaluate and trusts the result; it is weaker than a
kernel proof. The Lean files are at
github.com/jaredwilder/graham-alspach-sequenceability and the write-up with its compiled PDF is at
github.com/jaredwilder/unpublished-math-papers.

## License

Apache-2.0.
