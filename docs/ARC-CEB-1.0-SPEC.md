# ARC-CEB-1.0 Specification

**Candidate-Enumeration Boundary and Deterministic Residual-Issue Generator**

Classification: Experimental Protocol / Process-Control Extension / QOFT Typed Realization  
Canonical weight: None  
Status: DEVELOP  
Version: 1.0

The design follows the stamped QOFT methodology that auditor recall is a sampler, while class-exhaustion requires deterministic enumeration over a declared boundary.

---

## 1. Core requirement

Exact candidate-set reproducibility cannot be guaranteed from unconstrained prose alone. A model must not reread the answer and freely “notice” possible defects, because that recreates model-dependent sampling. ARC therefore operates on a frozen typed control record produced with the answer, not on a fresh semantic brainstorm after the answer.

Control path:

```
completed answer
→ frozen ARC Control Record
→ deterministic dependency closure
→ deterministic eight-class enumeration
→ frozen CandidateSet
→ Ψmeta scoring with P, M, G
→ one continuation or STOP
```

Formally:

```
R_ARC = frozen answer-control record
B_ARC = load-bearing boundary extracted from R_ARC
CandidateSet_ARC = Enum_CEB_1(B_ARC)
Ψmeta_ARC : CandidateSet_ARC → {0,1,2,3}³
Ψmeta_ARC(cᵢ) = (Pᵢ, Mᵢ, Gᵢ)
```

`Enum_CEB_1` is a pure function. Given identical record bytes and the same generator version, it must produce the same ordered candidate list and the same candidate-set hash.

---

## 2. Frozen ARC Control Record

Every ARC-controlled answer must produce this internal record at answer completion. The schema is defined in the full protocol document. Key invariants:

- Closed field vocabularies for `kind` and `basis`.
- Each load-bearing declarative statement has exactly one claim ID.
- Stored claim text must equal the answer bytes at `answer_span`.
- A claim may not be paraphrased during enumeration.

---

## 3. The finite enumeration boundary

Roots:

```
R₀ = { headline_claim_id, decision_claim_id when non-null }
```

Boundary = backward dependency closure of R₀ plus only the terms, evidence, tests, measurements, scopes, and bridges they reference.

Excluded by rule: background not linked through `depends_on`, examples, stylistic observations, optional extensions, interesting side questions, unregistered external facts, newly imagined alternative theories, prior conversation material not represented in the frozen record.

A scorer may not add a candidate merely because it notices something interesting. Any newly noticed issue is recorded as `OUT_OF_BOUNDARY` and cannot alter the current ARC decision.

This is exhaustive over the declared record and defect classes, not exhaustive over reality.

---

## 4. Closed residual-defect classes (R1–R8)

Exactly eight classes. There is no OTHER, MISC, or free-form candidate class.

- **R1 Support gap**  
- **R2 Untested assumption**  
- **R3 Undefined operative term**  
- **R4 Alternative or confound gap**  
- **R5 Missing failure or rejection condition**  
- **R6 Scope-bridge gap**  
- **R7 Internal inconsistency**  
- **R8 Operationalization, measurement, or realization gap**

Full trigger predicates and fixed statement templates are defined in the locked protocol text.

---

## 5–12. Generator, candidate object, templates, deduplication, finiteness proof, hashing, completion semantics, QOFT realization

See the complete locked specification in the source materials and the preregistration document.

The eight-class boundary is technically deterministic by construction. Whether those eight classes provide adequate practical coverage remains an empirical question until adversarially tested.
