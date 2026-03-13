## `openclaw-pm-it-non-spawn-governance`

```markdown
A reusable OpenClaw governance skill for running a **non-spawn PM/IT collaboration model**.

This skill standardizes how `main` (PM) and `it` (IT) cooperate without using `sessions_spawn`. It keeps `shared_pool` as the formal task source of truth, uses agent-to-agent only as a controlled PM → IT communication enhancement, and constrains IT from uncontrolled horizontal session activity.

Includes:
- PM/IT operating model
- `AGENTS.md`
- `HEARTBEAT.md`
- non-spawn `openclaw.json` template
- topology validation helpers

Use this skill when you want reproducible, evidence-driven coordination between PM and IT agents.
