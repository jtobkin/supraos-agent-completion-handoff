# SupraOS Agent Completion Documents

These project documents are public and readable without signing in. Application source, engineering receipts and operational access remain private.

- [Detailed handoff](SupraOS-Universal-Agent-Completion-Handoff.md): goals, current status, code map, remaining work, fresh-account setup and definition of finished.
- [Plan and task checklist](SupraOS-Agent-Plan-Checklist.md): all 62 acceptance tasks and the 32-package dependency graph.
- [Execution procedure](Faster-Verified-SupraOS-Delivery.md): coordinated implementation, qualification and independent review.

Current checkpoint: 2026-10-05T03:21:51.758209+00:00. resumed 2026-10-05 under Claude (owner handoff from Codex); shipping the frozen candidate through the platform's normal release path (box-ci merge-if-green → AWS deploy-main cron; migrations by hand with scripts/apply-migration.mjs), Agent Run flags off; the isolated native-VM/operator rehearsal is skipped. Full Agent Run: unshipped; inactive; global attention cutover: 0; restoreVerified: false. 5 of 62 tasks accepted (8.1%); 56 pending (90.3%); 1 deliberately dropped (1.6%).
