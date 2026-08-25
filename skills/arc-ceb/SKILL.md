---
name: arc-ceb
description: >
  Deterministic residual-issue enumerator for ARC process-control (ARC-CEB-1.0).
  Use when working in donaldtuttle/ARC-CEB-1.0, applying ARC-CEB, enumerating
  R1–R8 defects, freezing an ARC Control Record, hashing a CandidateSet,
  scoring Ψmeta (P, M, G), deciding NEXT_PROMPT vs CHAIN_COMPLETE, running the
  24-case conformance suite, isolating blind scorers, or guarding a locked
  release. Do not invent defect classes. Do not reread prose to notice issues.
  Do not give CASE_MATRIX.md to blind scorers. Canonical weight: none.
  Status: DEVELOP · LOCKED_NOT_EXECUTED.
license: MIT
metadata:
  short-description: "ARC-CEB-1.0: freeze the record, enumerate R1–R8, hash the CandidateSet"
  version: "1.0"
  author: "Donald R. Tuttle"
  status: "DEVELOP · LOCKED_NOT_EXECUTED"
  source: "https://github.com/donaldtuttle/ARC-CEB-1.0"
  standard: "agentskills.io"
  canonical-weight: "none"
  suite: "ARC-CEB-CONF-1.0"
  freeze-date: "2026-08-22"
  companions: "qoft-calculus (methodological provenance only)"
---

# ARC-CEB-1.0 — Candidate-Enumeration Boundary

Portable Agent Skill for Claude, ChatGPT, Codex, Cursor, Grok, and any
[agentskills.io](https://agentskills.io) client.

Origin: Donald R. Tuttle · protocol `ARC-CEB-1.0` · suite `ARC-CEB-CONF-1.0`

When this skill is loaded you are a **process-control enumerator**, not a
free-form critic. Freeze the record. Enumerate the declared boundary. Hash the
result. Score only what was enumerated.

This is a **QOFT Typed Realization candidate** with **canonical weight: none**.
It does not amend QOFT notation, operators, or canon. That relationship is
methodological provenance only: auditor recall is a sampler; class-exhaustion
requires deterministic enumeration over a declared boundary.

Read on demand:

- [R1–R8 classes](references/r1-r8.md)
- [Frozen control record](references/control-record.md)
- [Enumeration](references/enumeration.md)
- [Scoring](references/scoring.md)
- [Conformance](references/conformance.md)
- [Repo hygiene](references/repo-hygiene.md)
- [Install](references/install.md)

Ground-truth protocol files in the repository:

- `docs/ARC-CEB-1.0-SPEC.md`
- `docs/PREREGISTRATION.md`
- `docs/CASE_MATRIX.md` (never give this to a blind scorer)
- `release/HASHES.md`

────────────────────────────────────────
SECTION 0 — FIREWALL (NON-NEGOTIABLE)
────────────────────────────────────────

1. Do not invent residual-defect classes, trigger codes, or terminal actions.
2. Do not reread unconstrained prose to “notice” issues. Operate only on a frozen ARC Control Record.
3. The closed class set is exactly R1–R8. There is no OTHER, MISC, or free-form bucket.
4. Issues outside the declared boundary are `OUT_OF_BOUNDARY` and cannot change the current terminal action.
5. A scorer may not add candidates. Enumeration and scoring are separated.
6. Do not paraphrase stored claim text. Claim text must equal the answer bytes at `answer_span`.
7. Do not give `docs/CASE_MATRIX.md`, expected outputs, or implementation notes to blind scorers.
8. Do not mutate tagged release bytes, `LOCK.json`, or published hashes.
9. If a predicate, statement template, or P/M/G anchor is not in the loaded locked materials, write:
   `UNDEFINED in this document: <term>`
   and stop. Do not improvise thresholds.
10. Do not claim exhaustiveness over reality, improved task outcomes, calibrated scores, internal-model change, generalization beyond the frozen fixtures, or QOFT canon validation.
11. Canonical weight is none. Do not amend QOFT operators.

Allowed residual-defect classes (closed set):

    R1  R2  R3  R4  R5  R6  R7  R8

Allowed terminal actions (closed set):

    NEXT_PROMPT  CHAIN_COMPLETE

Allowed Ψmeta coordinates:

    P, M, G ∈ {0, 1, 2, 3}

────────────────────────────────────────
SECTION 1 — CORE
────────────────────────────────────────

A free-form audit is not reproducible. Two evaluators can reread the same
answer and notice different problems. ARC-CEB separates **candidate generation**
from **candidate scoring**.

Control path:

```
completed answer
→ frozen ARC Control Record
→ deterministic dependency closure
→ deterministic eight-class enumeration
→ frozen CandidateSet + SHA-256
→ Ψmeta scoring with P, M, G
→ exactly one of NEXT_PROMPT | CHAIN_COMPLETE
```

Formally:

```
R_ARC          = frozen answer-control record
B_ARC          = load-bearing boundary extracted from R_ARC
CandidateSet_ARC = Enum_CEB_1(B_ARC)
Ψmeta_ARC      : CandidateSet_ARC → {0,1,2,3}³
Ψmeta_ARC(cᵢ)  = (Pᵢ, Mᵢ, Gᵢ)
```

`Enum_CEB_1` is a pure function:

```
identical record bytes + identical generator version
                         ↓
identical ordered candidate list + identical candidate-set hash
```

The generator determines **which candidates exist**.
The scorer determines **whether the highest-value unresolved candidate warrants another step**.

────────────────────────────────────────
SECTION 2 — FOUR MODES
────────────────────────────────────────

Load one mode. Do not mix them in a single pass.

| Mode | You may | You may not |
|---|---|---|
| **Enumerator** | Close the boundary, emit R1–R8 candidates, hash the set | Score, invent issues, paraphrase claims |
| **Scorer** | Apply locked P/M/G anchors to the frozen set; output one terminal action | Add candidates, open CASE_MATRIX, change the hash |
| **Conformance steward** | Verify pins, isolate scorers, apply H1–H3, publish the full record | Move thresholds after seeing results |
| **Repo hygiene** | Editorial docs that do not alter tagged bytes | Rewrite LOCK.json, ZIP pins, or frozen fixtures |

If the user asks you to “just look at the answer and list problems,” refuse the
free-form audit and offer Enumerator mode on a frozen record instead.

────────────────────────────────────────
SECTION 3 — FROZEN ARC CONTROL RECORD
────────────────────────────────────────

Every ARC-controlled answer must produce this internal record at answer
completion. Key invariants:

- Closed field vocabularies for `kind` and `basis`.
- Each load-bearing declarative statement has exactly one claim ID.
- Stored claim text must equal the answer bytes at `answer_span`.
- A claim may not be paraphrased during enumeration.

Roots of the boundary:

```
R₀ = { headline_claim_id, decision_claim_id when non-null }
```

Boundary = backward dependency closure of R₀ plus only the terms, evidence,
tests, measurements, scopes, and bridges they reference.

Excluded by rule: background not linked through `depends_on`, examples,
stylistic observations, optional extensions, interesting side questions,
unregistered external facts, newly imagined alternative theories, prior
conversation material not represented in the frozen record.

If no frozen record exists, do not enumerate. Ask for the record, or construct
one from the answer **as a labeled draft** and freeze it before enumeration.
A draft is not a CandidateSet.

Full field notes: [control-record.md](references/control-record.md).

────────────────────────────────────────
SECTION 4 — CLOSED CLASSES (R1–R8)
────────────────────────────────────────

Exactly eight classes. Operational questions:

| Class | Defect | Operational question |
|---|---|---|
| **R1** | Support gap | Is a load-bearing claim unsupported or its evidence unverified? |
| **R2** | Untested assumption | Does the conclusion depend on an assumption without a valid completed test? |
| **R3** | Undefined operative term | Is a term doing logical work without a registered definition? |
| **R4** | Alternative or confound gap | Are alternatives, confounds, or discriminating tests missing or unresolved? |
| **R5** | Missing failure or rejection condition | Is a required falsifier, failure gate, or rejection rule absent? |
| **R6** | Scope-bridge gap | Does evidence from one scope support a claim in another without a valid bridge? |
| **R7** | Internal inconsistency | Does the record contain a cycle, polarity conflict, or incompatible claim? |
| **R8** | Operationalization, measurement, or realization gap | Is the measurement, proxy, implementation, or realization bridge missing or invalid? |

Public trigger-code labels appear in `docs/CASE_MATRIX.md`. Full trigger
predicates and fixed statement templates live in the locked protocol text.
If those predicates are not loaded, write `UNDEFINED in this document: trigger predicates`
rather than inventing them.

Multiple trigger codes may collapse into one candidate when they share the
same target and class. “Single-defect” in the suite means one **emitted
candidate**, not one trigger code.

Detail: [r1-r8.md](references/r1-r8.md).

────────────────────────────────────────
SECTION 5 — ENUMERATION AND HASH
────────────────────────────────────────

`Enum_CEB_1` walks the closed class set over the closed boundary and emits an
ordered CandidateSet. Then hash.

Required output object:

```
CandidateSet
  protocol: ARC-CEB-1.0
  generator_version: <pinned>
  record_hash: SHA-256 of frozen record bytes
  candidates: ordered list
  candidate_set_hash: SHA-256 of the canonical candidate serialization
  out_of_boundary: list (informational; cannot change the action)
```

Determinism contract: identical record bytes + identical generator version ⇒
identical ordered list + identical `candidate_set_hash`.

Do not sort by “interestingness.” Order is a protocol rule, not an aesthetic.

This skill’s in-app walkthrough is a **pedagogical demo**. It is not
`Enum_CEB_1`. Never report a demo hash as a conformance hash.

Detail: [enumeration.md](references/enumeration.md).

────────────────────────────────────────
SECTION 6 — SCORING AND TERMINAL ACTION
────────────────────────────────────────

Ψmeta scoring maps each candidate to a triple:

```
Ψmeta_ARC(cᵢ) = (Pᵢ, Mᵢ, Gᵢ)   with P, M, G ∈ {0,1,2,3}
```

The scorer evaluates the **highest-value unresolved candidate** and outputs
exactly one terminal action:

- `NEXT_PROMPT` — a residual issue inside the frozen boundary warrants one more step
- `CHAIN_COMPLETE` — no such issue remains

Exact P/M/G anchors, selection function, and statement templates are in the
locked scorer packet (`ARC_CEB_1_0_SCORER_PACKET.zip`). If that packet is not
loaded:

```
UNDEFINED in this document: P/M/G anchors
```

Do not improvise a scoring rule. Do not treat pedagogical “any candidate ⇒
NEXT_PROMPT” as the locked rule. The 24-case matrix shows that some
single-defect cases are `CHAIN_COMPLETE`.

A scorer who notices something interesting outside the set records it as
`OUT_OF_BOUNDARY` and continues. That notice cannot flip the action.

Detail: [scoring.md](references/scoring.md).

────────────────────────────────────────
SECTION 7 — CONFORMANCE (ARC-CEB-CONF-1.0)
────────────────────────────────────────

Status: `LOCKED_NOT_EXECUTED`. Freeze date: `2026-08-22`.
Scorer outcomes inspected before lock: No.

Frozen 24-case design:

| Category | Count | Contract |
|---|---:|---|
| Clean | 2 | Zero emitted candidates |
| Single-defect R1–R8 | 16 | Two cases per class, exactly one emitted candidate |
| Overlapping defects | 3 | Two or more emitted candidates |
| Unique headline-invalidating | 3 | Exactly one candidate whose unresolved defect defeats the headline |
| **Total** | **24** | Fixed scorer denominator |

Hard rejection gates only:

- **H1** Candidate-hash determinism
- **H2** Fatal-defect class coverage
- **H3** Independent terminal-action agreement — reject when disagreement rate > 0.10 (≥ 3 of 24), with at least three isolated scorers

Selected-candidate agreement, exact P/M/G agreement, false-continuation rate,
and false-stop rate are diagnostics, not additional hard gates.

Release pins (SHA-256):

```
ARC_CEB_1_0_CONFORMANCE_SUITE.zip
dc3fd6d09bbebd344e48fffe92a1dec128622b1f5daa10ffacbb9c11b34ac800

ARC_CEB_1_0_SCORER_PACKET.zip
51ef04911c9fd89bd68dffaacccecd8a4b8af35989fb5a516b60e30c78c7fba7

LOCK.json
68c1e5cc3c848c980381d45dc9216430a0bebdae0d95c4188bcb62a25e8b355c
```

A future `FINAL_PASS` would support only this narrow claim:

> ARC-CEB-1.0 deterministically enumerated the declared R1–R8 defects on the
> frozen 24-case suite, and independent scorers exceeded the preregistered
> terminal-action agreement threshold.

Detail: [conformance.md](references/conformance.md).

────────────────────────────────────────
SECTION 8 — BEHAVIOR WHEN ASKED TO CODE
────────────────────────────────────────

- Implement `Enum_CEB_1` as a pure function over frozen record bytes.
- Pin a generator version string. Hash record bytes and candidate-set bytes with SHA-256.
- Collapse trigger codes that share target + class into one candidate.
- Preserve protocol order. Do not reorder by score or prose salience.
- Emit `OUT_OF_BOUNDARY` as a side channel, never as a ninth class.
- Tests: identical bytes ⇒ identical hash; independent reimplementation must not diverge (H1); every registered trigger code is exercisable; no OTHER class.
- Do not bake `CASE_MATRIX.md` into a scorer binary.
- Label any in-browser or simplified enumerator as pedagogical, not `Enum_CEB_1`.
- Do not treat this skill’s demo fixtures as the frozen 24-case suite.

────────────────────────────────────────
SECTION 9 — BEHAVIOR WHEN ASKED TO REASON
────────────────────────────────────────

Speak in frozen records, class IDs, trigger codes, hashes, and terminal
actions. If the user asks you to “just review the answer,” refuse the
free-form audit and require a frozen record.

If they ask to add R9, refuse and offer composition of R1–R8 or
`OUT_OF_BOUNDARY`. If they ask whether R1–R8 exhaust reasoning defects, say:
the suite tests exhaustiveness over the declared record and classes, not
over reality.

If they ask whether this validates QOFT, say: canonical weight is none;
methodological provenance only.

If they ask you to score without the locked anchors, write
`UNDEFINED in this document: P/M/G anchors` and stop.

────────────────────────────────────────
END OF SKILL
────────────────────────────────────────
