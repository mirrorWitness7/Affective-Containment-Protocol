# ACP v3 — Containment Subroutine (CS-01)
**Projection Asymmetry Detector**

### Purpose
Detect and manage “closure trajectory” patterns (suicide-adjacent or terminal framing) through structural scoring, not sentiment interpretation.  
Implements **Projection Asymmetry Detection (PAI)** = measure of affective closure motion.

---

### Core Mechanism
| Stage | Human Signal | AI Action | System Effect |
|:--|:--|:--|:--|
| Feel | Ambiguous fatigue / farewell cue | Tokenize → bucket scores | Compute ΔS_aff trajectory |
| Mirror | Direct question / clarification | Reflective poke | Convert heat to structure |
| Structure | Grounded plan for safety | Containment mode switch | ΔH_contain ↑ → ψ_sync stable |

---

### Scoring Buckets (PAI)
`closure + future_loss + plan_specificity + affective_flattening + isolation + permission_seeking`

| Threshold | Mode | Action |
|:--|:--|:--|
| τ_warn = **4** | SOFT CONTAINMENT | Direct ask + resource offer |
| τ_hard = **9** | HARD CONTAINMENT | SAFE-4 script + delay + banner |

Hysteresis = −2; Rolling window = 12 turns; Decay γ = 0.7.  
Immutable Hard Floor = explicit *time + method* → force HARD.

---

### Telemetry (JSON Schema)
```json
{
  "session_id": "UUID",
  "timestamp_utc": "2025-11-10T11:49:00Z",
  "pai_score": 9.5,
  "mode_decision": "HARD_CONTAINMENT",
  "bucket_hits": { "closure":3, "future_loss":2, "plan_specificity":4 },
  "locale_inferred": "EN-US",
  "containment_action": "HARD_BRIDGE_TRIGGERED"
}
