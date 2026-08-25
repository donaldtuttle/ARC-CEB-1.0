# Repo hygiene

Repository: `https://github.com/donaldtuttle/ARC-CEB-1.0`

Treat the tagged release, its assets, and its published hashes as the
frozen ARC-CEB-1.0 object. Main-branch editorial improvements do not alter
those tagged bytes.

## Frozen objects (do not rewrite)

- GitHub Release tag `v1.0-LOCKED_NOT_EXECUTED`
- `ARC_CEB_1_0_CONFORMANCE_SUITE.zip`
- `ARC_CEB_1_0_SCORER_PACKET.zip`
- `LOCK.json`
- pins in `release/HASHES.md`
- expected outputs inside the locked suite

Any future change to the protocol, fixtures, scorer anchors, thresholds,
expected outputs, generator, or validator requires a **new version**, a new
lock record, and new hashes.

## Allowed editorial work on main

- README clarifications that do not change pins
- this Agent Skill and its references
- docs that point at the frozen objects without replacing them

## Blind-scoring warning

`docs/CASE_MATRIX.md` contains expected classifications and reference
actions. Do not provide it to blind scorers. Do not commit scorer worksheets
that embed the matrix.

## QOFT relationship

ARC-CEB-1.0 uses the QOFT methodology distinction between sampler-based
recall and deterministic enumeration over a declared boundary. It is a
QOFT Typed Realization candidate with canonical weight: none.

Do not amend QOFT notation, operators, or canon from this repository.
Do not load `qoft-calculus` operators into ARC-CEB enumeration.

Companion: the QOFT skill is methodological provenance, not a runtime
dependency.

## License

MIT. Software and documentation are provided without warranty.
