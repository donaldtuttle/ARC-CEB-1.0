# ARC-CEB-1.0 Agent Skill

The portable Agent Skill is located at
[`skills/arc-ceb/SKILL.md`](../skills/arc-ceb/SKILL.md).

It packages the R1–R8 firewall, enumerator/scorer separation, conformance
gates, and repo hygiene for ARC-CEB-1.0. Canonical weight remains none.
The skill does not execute the locked suite and is not `Enum_CEB_1`.

## Authority boundary

The repository root `SKILL.md` is the public 1.0 contract. The portable pack
adds references and host chrome. They describe the same protocol. Neither
file amends the tagged release `v1.0-LOCKED_NOT_EXECUTED`, `LOCK.json`, or
the published ZIP hashes.

This packaging record does not itself constitute a `FINAL_PASS` or a QOFT
canon adoption.

Core boundary:

```
CandidateSet_ARC = Enum_CEB_1(B_ARC)
terminal action ∈ { NEXT_PROMPT, CHAIN_COMPLETE }
classes         ∈ { R1 … R8 }
```

License: MIT under the repository root [`LICENSE`](../LICENSE).
