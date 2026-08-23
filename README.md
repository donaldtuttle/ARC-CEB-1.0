# ARC-CEB-1.0

**Candidate-Enumeration Boundary and Deterministic Residual-Issue Generator**  
Conformance Suite: `ARC-CEB-CONF-1.0`

**Status:** `LOCKED_NOT_EXECUTED`  
**Classification:** Experimental Protocol / Process-Control Extension / QOFT Typed Realization candidate  
**Canonical weight:** None  
**Freeze date:** 2026-08-22

---

## What this is

ARC-CEB-1.0 converts residual-issue discovery in the ARC process-control protocol from model-dependent sampling into a **pure, deterministic function** over a frozen typed control record.

It implements the QOFT methodology distinction:

> Auditor recall is a sampler.  
> Class-exhaustion claims require deterministic enumeration over a declared boundary.

ARC remains a conversation-level process controller. It does not amend QOFT notation or operators.

---

## Core control path

```
completed answer
→ frozen ARC Control Record
→ deterministic dependency closure
→ deterministic eight-class enumeration (R1–R8)
→ frozen CandidateSet
→ Ψmeta scoring with P, M, G
→ exactly one NEXT_PROMPT or CHAIN_COMPLETE
```

`Enum_CEB_1` is a pure function. Identical record bytes + same generator version → identical ordered candidate list and candidate-set hash.

---

## The eight residual-defect classes

| Class | Name |
|-------|------|
| R1 | Support gap |
| R2 | Untested assumption |
| R3 | Undefined operative term |
| R4 | Alternative or confound gap |
| R5 | Missing failure / rejection condition |
| R6 | Scope-bridge gap |
| R7 | Internal inconsistency |
| R8 | Operationalization / measurement / realization gap |

No free-form or “OTHER” class exists. Issues outside these classes are recorded as `OUT_OF_BOUNDARY` and cannot affect the current decision.

---

## Conformance Suite (ARC-CEB-CONF-1.0)

Exactly 24 frozen cases:

| Category | Count | Contract |
|----------|------:|----------|
| Clean | 2 | Zero candidates |
| Single-defect (R1–R8) | 16 | Two cases per class, exactly one emitted candidate |
| Overlapping defects | 3 | Two or more candidates |
| Unique headline-invalidating | 3 | Exactly one candidate whose unresolved defect defeats the headline |
| **Total** | **24** | Fixed scorer denominator |

### Hard rejection gates (preregistered)

- **H1 – Candidate-hash determinism**  
  Identical frozen records must produce identical candidate-set SHA-256. Requires the reference implementation + at least one independently written enumerator.

- **H2 – Fatal-defect class coverage**  
  Reject if a confirmed unique headline-invalidating defect cannot be represented by R1–R8.

- **H3 – Independent terminal-action agreement**  
  At least three isolated scorers. Reject if terminal actions (NEXT_PROMPT vs CHAIN_COMPLETE) disagree on ≥ 3 of the 24 cases (>10%).

### Current execution status

```
STATIC_PASS
PENDING_REPLICATION
PENDING_SCORERS
```

No final ARC conformance claim has been made.

---

## Release hashes (locked)

```
ARC_CEB_1_0_CONFORMANCE_SUITE.zip
SHA-256: dc3fd6d09bbebd344e48fffe92a1dec128622b1f5daa10ffacbb9c11b34ac800

ARC_CEB_1_0_SCORER_PACKET.zip
SHA-256: 51ef04911c9fd89bd68dffaacccecd8a4b8af35989fb5a516b60e30c78c7fba7

LOCK.json
SHA-256: 68c1e5cc3c848c980381d45dc9216430a0bebdae0d95c4188bcb62a25e8b355c
```

The binary packages should be attached as GitHub Release assets. This repository holds the locked textual specification, preregistration, case matrix, and supporting documentation.

---

## Claim boundary

A future `FINAL_PASS` supports only this claim:

> ARC-CEB-1.0 deterministically enumerated the declared R1–R8 defects on the frozen 24-case suite, and independent scorers exceeded the preregistered terminal-action agreement threshold.

It does **not** establish:

- that R1–R8 exhaust every possible reasoning defect
- that ARC improves task outcomes
- that P/M/G scores are universally calibrated
- that internal model reasoning changed
- that the protocol generalizes beyond the tested fixtures

---

## Directory layout

```
docs/           Protocol specification and preregistration
cases/          (placeholder for the 24 frozen case files)
keys/           Expected candidates, trigger coverage, reference scores
src/            Reference enumerator and validator (to be added)
scorer/         Blind packet materials and ballot templates
release/        Hash pins and lock metadata
```

---

## License

This experimental protocol and conformance suite are released for research and replication.  
No warranty of fitness for any particular purpose.

---

## Next required step

Give the blind scorer packet to at least three isolated scorers and the rule specification to one independently implementing auditor, then run the strict validator unchanged.

Reject ARC-CEB-1.0 if:

- any candidate hash diverges, or
- any adjudicated unique fatal defect lies outside R1–R8, or
- terminal actions disagree on three or more cases.
