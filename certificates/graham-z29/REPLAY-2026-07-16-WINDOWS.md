# Windows independent replay receipt — 2026-07-16

## Scope

This is a fresh provenance-confirming replay of the existing finite `Z_29` Graham/Alspach certificate. It is **not** a novelty claim, a universal theorem, or a terminal MATH_WIN.

## Exact command

```powershell
$env:Path = 'C:\Users\jared\.codex\toolchains\go1.26.5\go\bin;C:\msys64\ucrt64\bin;' + $env:Path
bun oracle/server/scripts/frontier-math-round4.ts full --threads 8
```

Run from `oracle/erdosfire` on 2026-07-16.

## Result

- Status: `PASS`; provenance confirmed.
- Deterministic C++20 regeneration SHA-256: `4dd6b2b21f75ffdd1ff472d1bf9a70757ccea0b31f147d49c6b1ff675c5ef961` — exactly matches committed `witnesses.tsv`.
- Scope: all subsets of `Z_29 \ {0}` of sizes 21 through 28.
- Certificate: 60,134 orbit representatives; 1,683,218 covered subsets.
- Independent Go full-expansion verifier: `VERIFIED`.
- Independent Python canonical-orbit verifier: `VERIFIED`; same certificate SHA-256 and coverage.
- Adversarial gate: all 14 generated corruptions were rejected by both verifiers.

## Defects closed during this replay

1. C++ generator JSON-escaped Windows certificate paths.
2. Go verifier derives its source sidecar independently of the `.exe` suffix.
3. Adversarial runner selects `verify_witnesses.exe` on Windows.

## Remaining terminal gap

The certificate is an internally existing finite classification. It does not provide cross-family novelty, a universal proof, statement-to-Lean closure, broad external novelty clearance, or a clean-room release package. Those remain open in the Master IOU.
