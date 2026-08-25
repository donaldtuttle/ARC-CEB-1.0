# Frozen ARC Control Record

Exact candidate-set reproducibility cannot be guaranteed from unconstrained
prose. ARC-CEB therefore operates on a frozen typed control record produced
with the answer, not on a fresh semantic brainstorm after the answer.

## Invariants

- Closed field vocabularies for `kind` and `basis`.
- Each load-bearing declarative statement has exactly one claim ID.
- Stored claim text must equal the answer bytes at `answer_span`.
- A claim may not be paraphrased during enumeration.
- The record is frozen before `Enum_CEB_1` runs. Later edits are a new record
  and a new hash.

The complete schema is defined in the locked protocol document. If that
schema is not loaded, write `UNDEFINED in this document: control-record schema`
and do not invent fields.

## Boundary roots

```
R₀ = { headline_claim_id, decision_claim_id when non-null }
```

The load-bearing boundary is the backward dependency closure of R₀, plus
only the terms, evidence, tests, measurements, scopes, and bridges those
claims reference.

## Excluded by rule

- background not linked through `depends_on`
- examples
- stylistic observations
- optional extensions
- interesting side questions
- unregistered external facts
- newly imagined alternative theories
- prior conversation material not represented in the frozen record

## Draft versus frozen

If the user supplies only prose:

1. Do not enumerate yet.
2. You may construct a **labeled draft** record from the prose.
3. Show the draft. Freeze it (bytes stop changing).
4. Then enumerate.

A draft is not a CandidateSet. A CandidateSet without a frozen record is a
protocol violation.

## Pedagogical fields (demo only)

The in-app walkthrough uses a simplified record so agents can practice the
shape. It is not the locked schema. Do not treat demo fields as canon.

Draft-shaped objects used in the demo:

- `claims[]` with `id`, `text`, `kind`, `dependsOn`, `evidenceIds`, `termIds`, `scope`
- `evidence[]` with `verified`, `scope`, `scopeBridge`
- `terms[]` with `defined`, `definitionClaimId`
- `tests[]` with `kind`, `run`, `passed`
- `measurements[]` with `validated`, `proxyBridge`, `realizationBridge`

Label any implementation of this shape as pedagogical.
