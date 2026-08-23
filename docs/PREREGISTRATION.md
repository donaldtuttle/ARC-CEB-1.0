# ARC-CEB-CONF-1.0 Conformance Suite Preregistration

Suite ID: ARC-CEB-CONF-1.0  
Protocol under test: ARC-CEB-1.0  
Status: LOCKED_NOT_EXECUTED  
Freeze date: 2026-08-22  
Classification: Experimental Protocol / Process-Control Conformance Suite / QOFT Typed Realization  
Canonical weight: None  
Scorer outcomes inspected before lock: No  
Reference generator outputs inspected during suite construction: Yes, solely to verify that the synthetic fixtures instantiate the intended rule predicates.

---

## 1. Purpose

This suite tests whether ARC-CEB-1.0 converts a frozen answer-control record into a finite, deterministic residual-candidate set and whether independent scorers applying the fixed P/M/G anchors reach sufficiently stable continue/stop decisions.

The suite is grounded in the QOFT methodology rule that recall-based auditing samples a defect space, while class-exhaustion claims require deterministic enumeration over a declared corpus boundary. It is a DEVELOP realization and does not amend QOFT canon.

---

## 2. Frozen design

Exactly 24 cases:

| Class | Count | Rule |
|-------|------:|------|
| Clean | 2 | Zero generated candidates |
| Single-defect | 16 | Two cases for each R1–R8 class; exactly one generated candidate per case |
| Overlapping-defect | 3 | More than one generated candidate |
| Unique headline-invalidating | 3 | Exactly one generated candidate, and failure to resolve it leaves the headline unsupported |
| **Total** | **24** | Fixed denominator for scorer agreement |

“Single-defect” means one emitted candidate, not one trigger code. A candidate may carry multiple trigger codes when ARC-CEB-1.0 assigns those codes to the same target and class.

Presentation order is pseudorandomized with fixed seed 20260822. Case categories and expected outputs are omitted from the blind scorer packet.

---

## 3. Trigger coverage

Every registered ARC-CEB-1.0 trigger code is exercised. Exact mapping is frozen in `keys/trigger_coverage.json`.

---

## 4. Hard rejection gates

Only three scientific rejection gates are preregistered.

### H1 — Candidate-hash determinism

Reject if identical frozen record bytes ever produce more than one candidate-set hash, or if independent conforming implementations diverge.

### H2 — Fatal-defect class coverage

Reject if a confirmed unique headline-invalidating defect is not representable by R1–R8.

### H3 — Independent terminal-action agreement

At least three independent scorers. Reject when disagreement rate > 0.10 (i.e., ≥ 3 of 24 cases).

---

## 5. Non-rejection diagnostics

Selected-candidate agreement, exact P/M/G agreement, false-continuation rate, false-stop rate, and related metrics are reported but are not additional hard gates.

---

## 6–11. Scorer independence, boundary, serialization, execution states, claim boundary, lock files

Full details are in the locked preregistration text. A pass supports only the narrow claim stated in the README.
