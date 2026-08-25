# Conformance suite ARC-CEB-CONF-1.0

Status: `LOCKED_NOT_EXECUTED`
Freeze date: `2026-08-22`
Protocol under test: `ARC-CEB-1.0`
Scorer outcomes inspected before lock: No
Canonical weight: None

## Design

Exactly 24 cases. Presentation order is pseudorandomized with fixed seed
`20260822`. Categories and expected outputs are omitted from the blind
scorer packet.

| Category | Count | Rule |
|---|---:|---|
| Clean | 2 | Zero generated candidates |
| Single-defect | 16 | Two cases for each R1–R8 class; exactly one generated candidate |
| Overlapping-defect | 3 | More than one generated candidate |
| Unique headline-invalidating | 3 | Exactly one generated candidate, and failure to resolve it leaves the headline unsupported |

Every registered trigger code is exercised. Exact mapping is frozen in
`keys/trigger_coverage.json` inside the locked suite.

## Hard rejection gates

Only three scientific rejection gates are preregistered.

### H1 — Candidate-hash determinism

Reject if identical frozen record bytes ever produce more than one
candidate-set hash, or if independent conforming implementations diverge.

### H2 — Fatal-defect class coverage

Reject if a confirmed unique headline-invalidating defect is not
representable by R1–R8.

### H3 — Independent terminal-action agreement

At least three independent scorers. Reject when disagreement rate > 0.10
(i.e., ≥ 3 of 24 cases).

## Diagnostics (not gates)

Selected-candidate agreement, exact P/M/G agreement, false-continuation
rate, false-stop rate.

## Execution path

1. Download both release assets and verify SHA-256 against `release/HASHES.md`.
2. Keep the scorer packet isolated from the case matrix and implementation materials.
3. Run frozen records through the reference enumerator and at least one independently written conforming enumerator.
4. Confirm byte-identical ordered candidate sets and hashes.
5. Give the blind packet to at least three isolated scorers.
6. Apply H1–H3 exactly as preregistered. Do not move thresholds after observing results.
7. Publish the full result record, including failures and non-rejection diagnostics.

## Release pins

```
ARC_CEB_1_0_CONFORMANCE_SUITE.zip
SHA-256: dc3fd6d09bbebd344e48fffe92a1dec128622b1f5daa10ffacbb9c11b34ac800

ARC_CEB_1_0_SCORER_PACKET.zip
SHA-256: 51ef04911c9fd89bd68dffaacccecd8a4b8af35989fb5a516b60e30c78c7fba7

LOCK.json
SHA-256: 68c1e5cc3c848c980381d45dc9216430a0bebdae0d95c4188bcb62a25e8b355c
```

Tag: `v1.0-LOCKED_NOT_EXECUTED`

## Claim boundary

A future `FINAL_PASS` supports only the narrow claim in the README. It
does not establish that R1–R8 exhaust every reasoning defect, that ARC
improves task outcomes, that P/M/G scores are universally calibrated, that
internal model reasoning changed, that the protocol generalizes beyond the
frozen fixtures, or that QOFT canon is validated.
