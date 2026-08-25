# Enumeration

`Enum_CEB_1` is a pure function.

```
identical record bytes + identical generator version
                         ↓
identical ordered candidate list + identical candidate-set hash
```

## Procedure

1. Read the frozen ARC Control Record. Refuse to start if it is not frozen.
2. Extract R₀ and close the backward dependency boundary.
3. Walk R1–R8 over that boundary using the locked trigger predicates.
4. Collapse trigger codes that share target + class into one candidate.
5. Serialize the ordered CandidateSet canonically.
6. Hash with SHA-256.
7. Stop. Do not score in the same pass unless the user explicitly switches
   to Scorer mode on the frozen object.

## Candidate object (minimum)

```
id
class          ∈ {R1…R8}
target_id
trigger_codes  (one or more locked codes)
statement      (locked template; do not free-write)
```

If statement templates are not loaded: `UNDEFINED in this document: statement templates`.

## Hashing

Hash the canonical serialization of the CandidateSet, not a pretty-printed
JSON dump, not Markdown, not a summary. Record:

- `record_hash` — SHA-256 of frozen record bytes
- `candidate_set_hash` — SHA-256 of canonical candidate serialization
- `generator_version` — pinned string

Divergent hashes on identical bytes fail H1.

## Order

Order is a protocol rule. Do not sort by interestingness, severity, or
prose position unless the locked generator specifies that rule.

## Pedagogical demo

The studio walkthrough is labeled:

```
PEDAGOGICAL_DEMO_NOT_ENUM_CEB_1
```

Never report a demo hash as a conformance hash. Never substitute demo
fixtures for the frozen 24-case suite.
