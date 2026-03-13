A reusable Ubuntu-focused OpenClaw monitoring skill that combines **internal cron checks** with an external **systemd watchdog** fallback.

This skill helps detect:
- gateway health issues
- repeated `accepted and moved`
- `missing status.json`
- worker lock anomalies
- scheduler drift or partial automation failure

Includes:
- watchdog shell script
- systemd install script
- operational runbook
- validation guidance

Use this skill when you want post-fix stability monitoring that does not rely on a single scheduling layer.
