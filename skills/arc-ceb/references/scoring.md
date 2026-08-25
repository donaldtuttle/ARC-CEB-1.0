# Scoring

Scoring begins only after the CandidateSet is frozen and hashed.
A scorer may not add a candidate.

## Ψmeta

```
Ψmeta_ARC : CandidateSet_ARC → {0,1,2,3}³
Ψmeta_ARC(cᵢ) = (Pᵢ, Mᵢ, Gᵢ)
```

Exact meanings of P, M, and G, and the numeric anchors for each level, live
in the locked scorer packet:

```
ARC_CEB_1_0_SCORER_PACKET.zip
SHA-256: 51ef04911c9fd89bd68dffaacccecd8a4b8af35989fb5a516b60e30c78c7fba7
```

If that packet is not loaded:

```
UNDEFINED in this document: P/M/G anchors
```

Do not invent a rubric. Do not treat “any candidate ⇒ NEXT_PROMPT” as the
locked rule. Several single-defect cases in the 24-case matrix are
`CHAIN_COMPLETE`.

## Terminal action

Closed set:

- `NEXT_PROMPT`
- `CHAIN_COMPLETE`

The scorer evaluates the highest-value unresolved candidate under the locked
selection function and emits exactly one action.

## Blind isolation

Blind scorers receive the scorer packet only. They must not receive:

- `docs/CASE_MATRIX.md`
- expected outputs
- reference hashes of the candidate sets they are scoring
- implementation notes for the enumerator
- this skill’s case-matrix table

If you are in Scorer mode and the user pastes CASE_MATRIX, refuse and
restart isolation.

## Out of boundary during scoring

A scorer who notices something interesting outside the frozen set records:

```
OUT_OF_BOUNDARY: <notice>
```

and continues. That notice cannot change the current terminal action.

## Diagnostics versus gates

Agreement on selected candidate, exact P/M/G triples, false-continuation
rate, and false-stop rate are reported as diagnostics. They are not
additional hard rejection gates in version 1.0. See H1–H3 in
[conformance.md](conformance.md).
