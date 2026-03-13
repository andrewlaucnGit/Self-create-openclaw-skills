# OpenClaw Skills Collection

A reusable skill set for running a **non-spawn PM/IT multi-agent operating model** on OpenClaw, with supporting watchdog automation and shared-pool hygiene workflows.

This repository packages the operational practices distilled from real incident handling and stabilization work on an Ubuntu-based OpenClaw deployment.

## What is included

This repo currently contains 3 reusable skills:

### 1. `openclaw-pm-it-non-spawn-governance`
Defines a **non-spawn** PM/IT collaboration model:

- `main` = PM
- `it` = IT
- `shared_pool` remains the formal task source of truth
- agent-to-agent is used only as a **PM → IT communication enhancement**
- IT is restricted from uncontrolled horizontal session communication
- includes `AGENTS.md` and `HEARTBEAT.md` conventions

Use this skill when you want to standardize:
- PM/IT task routing
- evidence-driven reporting
- task acceptance / delivery / closure conventions
- heartbeat behavior
- non-spawn OpenClaw multi-agent topology

---

### 2. `openclaw-cron-watchdog-ubuntu`
Installs and documents a **dual-layer monitoring approach** for Ubuntu:

- internal OpenClaw cron for routine checks
- external `systemd` watchdog as fallback

Use this skill when you want to:
- monitor gateway health
- detect repeated `accepted and moved`
- detect `missing status.json`
- verify worker lock behavior
- avoid relying only on internal scheduler health

---

### 3. `shared-pool-hygiene-cleanup`
Implements a safe workflow for:
- identifying stale `.bak`, `.disable`, and similar residue
- quarantine-first cleanup
- staged final deletion
- rollback-aware validation

Use this skill when you want to:
- reduce filesystem clutter safely
- avoid accidental deletion of live files
- preserve rollback discipline
- validate cleanup results with evidence

---

## Design principles

These skills are built around a few operating principles:

1. **Do not use PM spawn IT**
   - PM does not create IT subagent sessions with `sessions_spawn`
   - `shared_pool` remains the formal task execution backbone

2. **Evidence over narration**
   - task state must be validated from real artifacts
   - delivery requires `status.json`, `delivery.md`, logs, and verification results

3. **Small, reversible changes**
   - quarantine before delete
   - backup before overwrite
   - verify after each change

4. **Separate workflow from runtime**
   - skills capture conventions, scripts, templates, and checks
   - server-specific secrets and local runtime state stay out of the repo

---

## Suggested repository structure

skills/
  openclaw-pm-it-non-spawn-governance/
  openclaw-cron-watchdog-ubuntu/
  shared-pool-hygiene-cleanup/
packaged/
  openclaw-pm-it-non-spawn-governance-skill.zip
  openclaw-cron-watchdog-ubuntu-skill.zip
  shared-pool-hygiene-cleanup-skill.zip


Recommended usage order

If you are setting up a fresh server, use the skills in this order:
	1.	Governance first
	•	import openclaw-pm-it-non-spawn-governance
	•	align PM/IT responsibilities and communication rules
	•	update openclaw.json for non-spawn A2A
	2.	Monitoring second
	•	import openclaw-cron-watchdog-ubuntu
	•	install watchdog scripts and systemd timer
	•	validate health checks and logging
	3.	Cleanup third
	•	import shared-pool-hygiene-cleanup
	•	inventory and quarantine stale files
	•	perform staged final deletion only after validation

⸻

Who this repo is for

This repository is intended for operators who:
	•	run OpenClaw on Ubuntu / systemd
	•	want a PM/IT multi-agent model without sessions_spawn
	•	need shared-pool task governance
	•	want reusable incident-response and stabilization practices
	•	prefer operationally conservative workflows over aggressive automation

⸻

Important notes
	•	Review all scripts and templates before use in production.
	•	Do not commit secrets, tokens, local keys, or private environment details.
	•	Adjust paths if your OpenClaw installation differs from /root/.openclaw.
	•	Treat packaged .zip files as release artifacts; keep source-of-truth in skills/.
