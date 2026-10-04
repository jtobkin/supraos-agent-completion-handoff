# SupraOS Universal Agent Completion Handoff

## Active execution checkpoint — 2026-10-04 09:47 UTC

**Owner extended this run for five hours from09:13:30UTC through14:13:30UTC.** This supersedes the old09:28 checkpoint. At14:13:30, pause new work and publish a detailed fresh-account handoff and updated public/private plan. Full scope remains unchanged. Root and three Codex Sol workers own integration, host/release prerequisites and independent verification. Additional Grok CLI workers receive bounded implementation/review tasks; counts vary as jobs finish. A cancelled or turn-limited review is never an approval.

**Current application candidate:** `458f6a11cadcee0804a93755acf67d6f739e9d6b`, tree `a8c3c2c987fde302eff363287f4d054fd9ec8b6b`, branch `codex/agent-run-release-composition-20261004`, [PR6168](https://github.com/jtobkin/suprafx-platform/pull/6168), unmerged and held for release. It adds only the two demonstrated CI blocker repairs to30875: a test-local server-only mock matching adjacent fixtures and the existing10240MiB changed-types heap override. Production runtime and assertions are unchanged.

**Current qualification:** the managed production build passed all7steps, independently verified on test merge1bb12f77 against main1d29ec. The full unit tree passed59,763tests with252skipped, and changed-file types passed. Security remains RED: the unchanged pending-plan amendment PostgreSQL integration test exceeded its180s limit, finishing its test window at212.6s. The prior identical fixture passed in139.1s. Contention remains a hypothesis. The unchanged isolated diagnostic passed2/2 in135.22s, independently checked against11Git blobs and exact worker/log; it is diagnostic only. The supported managed retry is queued in batch0000e, and both latest contexts are pending. Never promote the outer systemd success over the inner workflow failure. [Exact evidence](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/evidence/ci-458f6-20261004/README.md). No acceptance count, merge or deployment is implied.

**Native release path:** exact QA sourceee969/treec070 is independently verified: strict Git fsck, clean checkout, all33,534files/745,603,485bytes and34CODE pins. [Portable source evidence](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/evidence/native-source-closure-20261004/README.md). Preserve this checkout. Seed-r2, narrow test HBA, network helper, Traefik and probe contexts are staged with independent receipts; app/PG phase controllers are source-reviewed. Dynamic packets still require actual daemon/network/load/app receipts. Strategies context is independently sealed:77,962members/~2.23GB; no image built. It is not a prerequisite for starting the PG chain.

**Current host blocker:** r2 PATH failure was fully reconciled and archived. The reviewed r3 successor started its private daemon/containerd with zero images/containers, but refused before writing ready. Independent snapshots show only normal nft packet/byte counters changing; exact structural rules match, so raw firewall hashing is the strong inferred cause. Original predicate output was not retained. The exact own generation has now been stopped, with independent containment seal b80bd1d0 confirming stopped/PID0/absent runtime. Shared Docker/containerd remained unchanged. A coherent structural-digest repair across daemon, builder and packet producer is underway; tests must distinguish counter-only changes from actual rule drift. No dependent network/image/app/DB effects occurred.

**Already qualified within limited scope:** historical f74 full-unit59,466PASS; exact30875 Settings1/1 and stream264/264 real Chromium checks with controlled persistence/provider fixtures; schema-only aef5497 rehearsal17packets/51steps/ninebaselinechecks. These do not establish live providers, full production UI, faithful restored data or current broad release admission. Source-specific records remain linked below.

**Recovery still open:** expired809db848 was never run. Fresh read-only capturedfd40ff4/plan15756ae4 succeeded09:37:42UTC and expires13:37:42UTC, with exact private readback. It acquired no lock and ran no backup. Current AWS free space72.07GiB is below the unchanged85GiB start floor; safe capacity remediation is being investigated, with no cleanup or resize performed. Independent fresh-plan review and specific shared-lock approval remain required. Prior approvals were consumed; auto-migration does not bypass recovery or writer-exclusion qualification.

**Next delivery order:** diagnose and close the remaining exact-source security gate; qualify the corrected private daemon; load pinned images and build the probe; create the private network and actual app phases; execute PG/baseline/bootstrap/PostgREST; exercise actual seven-step/lost-ACK/continuous-drain behavior; close faithful recovery and release admission; merge/deploy/activate the qualified candidate and independently verify every supported live journey. Independent source preparation runs in parallel, but no helper without a real caller or isolated fixture is counted as a shipped capability.

## Historical pause checkpoint and document navigation

**Historical: paused at the owner-requested 90-minute deadline, 2026-10-03 19:43 UTC (03:43 HKT October 4).** New implementation and qualification launches stopped. Only safe evidence collection and documentation publication wrap-up remains. This report supersedes older next-action lists; historical evidence keeps its original scope.

Frozen f74 full-unit QA PASS: 59,466 passed, 0 failed, 231 skipped; 4,714 files passed and 21 skipped. Independent Sol verified all174 published members and source/tree/terminal exit0/gate0; receipt b58e2d0d207e67c4337e197c1f15549a671e654128dfbeaa2fbaaf35549a568a. Canonical Promotion browser passed under original30s. Skips remain unverified; generated screenshot changes mean the used test checkout is not a clean build donor. Production build, remaining security/native/schema/recovery, migration, deployment, activation and live acceptance remain open.

**The full Agent Run project remains unshipped and inactive. Accepted tasks:5/62(8.1%); pending:56/62(90.3%); deliberately dropped:1/62(1.6%).** These are accepted-task counts, not code-completion, effort or production-readiness estimates. Most rows already contain substantial code but remain blocked by integrated qualification, release prerequisites or live acceptance. No production application migration, deployment or activation occurred in this focus run. Global attention remains off; overall restoreVerified remains false.

- Public handoff, no login: https://github.com/jtobkin/supraos-agent-completion-handoff/blob/main/SupraOS-Universal-Agent-Completion-Handoff.md . Public task checklist: https://github.com/jtobkin/supraos-agent-completion-handoff/blob/main/SupraOS-Agent-Plan-Checklist.md . This separate repository contains sanitized documentation only. The older chatgpt.site page is historical.
- Private engineering repository: https://github.com/jtobkin/suprafx-platform . Canonical coordination branch: `codex/agent-run-execution-20260928`; draft project PR5862. **Application qualification uses a separate composed candidate branch; do not deploy the coordination branch by assumption.**
- Current execution checklist: [EXECUTION-PLAN-20261001.md](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/EXECUTION-PLAN-20261001.md); [32-package DAG, states and journal](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/execution-dashboard/progress.json); [interactive artifact](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/execution-dashboard/index.html).
- Original acceptance ledger: [62 tasks](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/plan.json), [rendered PLAN](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/PLAN.md), [16 baseline acceptance](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/evidence/BASELINE-16-RELEASE-ACCEPTANCE.md), [all-path acceptance matrix](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/EXECUTION-PATH-ACCEPTANCE.md).
- [Execution improvements](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/EXECUTION-IMPROVEMENTS-20261003.md) governs delivery-path planning and proof reuse. Original goals and acceptance criteria remain unchanged.
- Historical detail is preserved in Git, including the pre-consolidation handoff at `116c4b8b1970bf8dc4c55c146784e017eb7daefd`. Do not treat a past 'current', 'paused', host floor or next-action section as current authority.

## Goal and scope

Make deterministic orchestration the default behavior of every supported SupraOS agent execution path: chatbox, Telegram, background work, delegation and System Workflows. Telegram is a communication channel; it must not own a separate behavior contract. iMessage is deferred.

The exact contract is: “Deterministic orchestration loads current preferences and relevant memory, skills, and lessons; tool execution checks permissions and records its outcome. Preference changes must append their before/after history to the hash chain before updating active state, so the next turn sees the latest saved value.”

This requires bounded context and SCM recall without stalling the UX; explicit preference scope/precedence and truthful persistence; orchestration-initiated tool, skill and lesson discovery; fresh permission checks before side effects; durable truthful outcomes and original-attempt recovery; append-only meaningful state history; resumable per-user onboarding; capability-by-capability readiness; and main-admin authorization for initial Guide setup. A preference never grants permission. Simulated purchases, stored mailbox names and configured credentials never prove readiness.

## What actually shipped, and what did not

| Item | Verified state | Boundary |
|---|---|---|
| Friend-channel security repair | Historical shipped repair PR5891/main61937ca124 | Independent narrow repair, not full Agent Run |
| Other historical narrow repairs | PR6025 and PR6037 recorded merged | No fresh live qualification claimed in this handoff |
| QA disk-admission scheduler PR6153 | Merged d35bdcbd37641648da3f2b6891289153cdda1ff2; exact runtime4a015f9 installed on QA, independently read back | Build/check infrastructure only; not production application deployment |
| Universal Agent combined source | Current458f6 runtimePR6168; production build independently PASS | Security PG timeout, native/schema/recovery, deployment and live acceptance remain open |
| Global attention and new SQL | Cutover off; phased profile and installed ledger must be re-read | No implicit activation or migration from code presence |
| Backup/recovery | Coherent historical capture and many scoped checks | Overall restoreVerified=false; restored-copy/role/profile/writer-window qualification incomplete |

A fresh GitHub PR readback at 2026-10-03 19:31:16 UTC showed PR5862 **open, draft, unmerged and conflicted** (`mergeable:false`, `mergeable_state:dirty`), with coordination head `6f466ab8eaf6a346475b4dad44d1f978ae1e5bd1`. This PR does not point to the frozen f74 application candidate. Its API-reported base SHA is metadata for that PR, not a substitute for freshly reading `refs/heads/main`. A later merge/release proposal must use the actually composed, qualified application source; the coordination PR is not a deployable shortcut. No merge was attempted.

Latest retained public live-source observation names `8b6b3525a2d9db8b0b0409f5d0498aad4d76d523`, with response timestamp `2026-10-03T18:46:41.210Z`. The read-only public `/api/version` request through the QA host succeeded. This is a source stamp only, not authenticated behavior, running image/config equality or proof that the frozen Agent Run candidate is deployed. Main can advance independently.

The five accepted rows remain A2 workflow run-log helper, A3 structured result labels, A4 image validation, O0 scope grounding and M0 memory/latency trace. B2 standalone Thinking is deliberately dropped. iMessage is separately deferred. O1 onboarding's old audit does not apply to changed completion-route source.

The older handoff's 41/62 locally complete figure used a different milestone: local implementation and audit. It must not be compared directly with the current 5/62 accepted-task count or presented as a regression in code written. Track implementation, integration, tests, independent review, merge, deployment, activation and live verification separately; do not estimate remaining hours from either percentage.

## Recent qualification history

1. **Application failure diagnosis and bounded repairs:** retained the complete c44 Linux full-unit RED (59,436 passed/26failed/231skipped). Nine test/fixture repairs compose a9f9, without runtime/SQL permission changes. Exact repair run passed382/382 with25 Chromium launches and independently inspected held-state phone/desktop screenshots.
2. **Preserved and repaired qualification infrastructure:** first a9f9 attempt failed before full tests/unit on EXDEV while moving screenshots across filesystems. The corrected runner copies exclusively, verifies identity/size/hash and preserves originals. Real cross-filesystem Linux smoke passed. Second a9f9 full suite reached terminal RED:59,465 passed/1failed/231skipped across4,713 passing/1failing/21skipped files. Sole failure was shallow outer-HEAD^ history in a test fixture. Reviewed51db repair uses a real disposable two-commit repository and preserves rejection assertions;71 scoped tests pass. Complete terminal receipt and172 published member hashes were independently verified.
3. **Closed QA scheduler installation:** two pre-effect refusals were retained. Third bounded one-use installation succeeded after natural idle; exact three runtime files, normal service behavior, unchanged other inputs and no cancelled jobs were independently verified. Do not replay any of the three attempts.
4. **Recovered qualification disk safely:** seven archived non-Git exports removed once after content correspondence and terminal review. All Git worktrees and dependency donors preserved. No blanket pruning or shared-image cleanup. Capacity remains a concrete gate.
5. **Prepared clean build and checked production dependencies:** separate clean a9f9 source staged; build still held. Production lock-only npm audit reports zero vulnerabilities. Reviewed build evidence reader now hashes and parses the same bounded no-follow file bytes; six local refusal/success probes pass. This is launcher preparation, not a build pass.
6. **Advanced the real release boundary dependency:** isolated v5 old-web ingress cutoff is wired into the tested Coordinator composite, with generation-bound UNKNOWN and strict downstream refusal; durable no-reclaim and writer-exclusion authorities remain missing. There is still no full production CLI/operator assembly. Native namespace checks prove only their actual origins; a local subset cannot establish all-origin production cutoff.
7. **Repaired and exercised a genuine UI blocker:** whole-tree P3C found reset error/detail leakage on Memory Promotion. The narrow repair uses truthful generic guidance for both HTTP failure and malformed JSON. Diagnostic r4c exercised the actual page in Linux Chromium at390/1440:1/1 test passed in6.49seconds, zero skips,12 byte-verified screenshots independently reviewed by root and Sol. It changed logging only; application source, assertions and30-second limit were unchanged. The earlier clean r3 test stalled in desktop missing-run recovery; that unexplained reliability failure is retained, not declared fixed. The active frozen f74 full suite later reported the clean canonical browser file PASS (1 test, 3,586 ms at the 19:26 UTC log readback), without instrumentation or a changed budget. The later independently verified terminal seal confirms this canonical pass; the earlier r3 stall remains unexplained. Clean9a2 passes28 frozen static checks,12-file types, full ESLint(0errors/590warnings),427 coordination tests and3 type-output tests.

8. **Closed a concrete secret-scan blocker:**105 findings were SHA256 source-file commitments in one historical stage receipt. Root and independent Sol reviewers verified105/105 against the declared Git blobs. Exact immutable commit/path/rule/line exceptions, not a broad allowlist, were added in f74bb. Gitleaks8.28.0 passes the exact ef86349dbda78e1d1e046dcd477dbe06f80f7e8a..f74bb97818c755527154c8c1633024f525bd2cda range; a synthetic credential control still fails as expected.

9. **Started exact final-candidate verification:** the frozen f74 full-unit run launched once at18:54UTC, with independent source/tree and effective20GiB/200% resource readback. It uses the unchanged18GiB start/8GiB abort floors. The run subsequently reached exit0:59,466passed/0failed/231skipped. Independent Sol rehashed all174published members and separately read the final counts from that same tests.log. This closes the full-unit gate only; production build and release remain open.

## Historical 90-minute focus window

The historical owner-requested window began at 18:12:50 UTC on October 3 and ends at 19:42:50 UTC. Earlier suite runs, scheduler installation and disk cleanup above are retained qualification history, not work newly completed inside this window. This window froze f74, closed the exact historical-hash Gitleaks blocker, independently verified the diagnostic Promotion browser run, launched the immutable full-unit successor, reviewed future launcher defects, prepared a source-only held build successor and prepared the portable handoff. The final checkpoint records its independently verified terminal PASS. No original acceptance task or production capability was newly declared complete.

Dependency triage at 19:02:54 UTC found two affected development dependencies in the exact f74 root lock (`http-cache-semantics@4.2.0` and `braces@3.0.3`), with no patched version listed in the advisories. The existing G6 gate audits root production dependencies only, so these are retained development-tool risks rather than evidence of a G6 failure. The reported hedge-desk `fast-uri` alert is outside f74's resolved `3.1.8` vulnerable range. This is neither an all-dependency security clearance nor an installed-package inventory. Independent Sol review checked exact locks and policy. Read the [source-pinned triage](https://github.com/jtobkin/suprafx-platform/blob/9ec13958fd7c04486a3aa9ddee65e7b0b786fa25/docs/agent-run/evidence/f74-dependabot-lock-triage-20261004/README.md); do not mutate the frozen candidate or introduce speculative overrides.

## Current source and ownership map

| Purpose | Branch / checkpoint | Local location and remaining state |
|---|---|---|
| Canonical coordination, plans and release scripts | `codex/agent-run-main-reconciliation-20260930`, publication target `codex/agent-run-execution-20260928`; publication target shown here; final commit pin is recorded in the public publication receipt and session checkpoint | the original private worktree (see engineering handoff) |
| Base composed application source | `codex/agent-run-main-composition-20261003`; a9f9bdb50ee99878bdfdee67906492acdbc51157; tree df0a3d1fe40b3a1c499483ed56cf1a2815bd8d4d; composed main ef86349dbda78e1d1e046dcd477dbe06f80f7e8a | Separate base checkout; B-owned MeetingPage overlay is outside this application commit but preserved on browser evidence branch c6d1f240; keep it separate |
| Demonstrated fixture/reset repairs | `codex/agent-run-check-fixture-20261004`, rooted at a9f9 | Separate root-owned candidate checkout; frozen f74bb97818c755527154c8c1633024f525bd2cda; tree9cbec0b05d90f546029011e53d5b0f7a28b2a5da; fixture51db, UI9a2 and exact G11 receipts. Branch tip3d9520bb4575320dfda42a8d315a6b58da9ac830 adds only a later G11 evidence clarification; qualification remains pinned to f74. Final browser/whole-suite status below |
| Ingress-cutoff and future qualification drafts | `feat/agent-run-netns-ingress-cutoff-20261004`; d9d4d54f40da3f3f1f08b1ac784aec9f559b5fe3 | B-owned isolated worktree `agent-run-ingress-netns-20261004`; includes ingress prototype, browser reuse, reviewed advisory triage and hard-held future full-unit/build launchers. No production operator assembly or build result |
| Existing browser evidence lane | `codex/agent-run-main-browser-evidence-20261003` | Recoverability/gap-map commits already composed; c6d1f240eae35687bfe2923642b648678f19c465 preserves corrected MeetingPage overlay997a5784 plus diagnostic test overlaye0872cbf; separate from frozen candidate |
| Scheduler operational evidence | `codex/box-ci-disk-rollout-f2e5-20261003`, be72456853 | the original private worktree (see engineering handoff); PR6154 draft/unmerged; installed runtime comes from separate mergedPR6153 |
| Portable host qualification evidence | `codex/host-qualification-evidence-20261004`,f72f4860f21dc92c8fad6d5775bc375684533ce6 | the original private worktree (see engineering handoff); scripts, browser receipts/12synthetic screenshots and current full-run monitoring in `docs/agent-run/evidence/host-qualification-20261004/` |
| Money/SSE prior repair | `codex/agent-run-stream-money-fixtures-20261004`,99c185de56 | Integrated into a9f9; source lane unmerged, preserved |

Previous c44 is c44ce05089d7abd885d3b09c1ba27db9168be108. Candidate history contains duplicated dependencies from preserved lanes; compare actual ancestry and file hashes before cherry-picking. Main updates are not an instruction to restart every qualifying candidate. Only demonstrated blockers enter the next frozen candidate.

Historical branches remain indexed in SupraOS-Agent-Reliability-Release-Handoff.md, session-transfer-20260929/README.md and the older handoff. They include living-contract-provenance, agent-run-lc-source, Claude live-operator and CI-shell-parity/PR5893. Do not blindly merge them. The newer application composition may already contain their relevant commits.

## Code map and structure


| Area | Where to read | Responsibility / important boundary |
|---|---|---|
|Boot and architecture|`AGENTS.md`, `CONTEXT.md`, `docs/AI_BUILD_PROTOCOL.md`, `docs/PLATFORM_ARCHITECTURE.md`, `docs/DOC_MAINTENANCE.md`|Required orientation, reuse-first rules, flow map and same-change documentation.|
|Agent Run core|`lib/agent-run/`|Runtime orchestration, preference shelf/history, context capture, claims, readiness, provider recipes and activation.|
|Preference persistence|`lib/agent-run/shelf.ts`, `shelf-history.ts`, `owner-preferences.ts`, `owner-preference-scope.ts`, `learn.ts`|Scope/precedence, history before active state, truthful persistence/readback.|
|Context/provenance|`lib/agent-run/context-provenance.ts`, `turn-context-capture.ts`, `load-context-receipts.ts`, `model-boundary.ts`|Bounded prepared context and permitted evidence records.|
|System orchestration|`lib/vms/coordination/system-workflow-engine.ts`, `node-handlers.ts`, `factory-workflows.ts`, `workflow-model-preferences.ts`|Graph execution, handlers, saved factory definitions, bounded owner context.|
|System identity/context|`lib/vms/coordination/system-workflow-context-identity.ts`, `system-workflow-model-audit.ts`|Verified owner/run/session/node coordinates; null System actor.|
|System owner context|`lib/vms/coordination/system-workflow-owner-chat-scm.ts`, `system-workflow-owner-lessons.ts`, `workflow-model-preferences.ts`|Canonical owner-chat, skill pattern and lesson preparation; composed into the current candidate, with live qualification still required.|
|Node/editor registry|`lib/vms/workflows/node-registry.ts`|Available node metadata must agree with actual executor capabilities.|
|Canonical memory|`lib/vms/memory/` including `build-lesson-recall.ts`, `lesson-text.ts`, `task-vocabulary.ts`|Owner/global/domain filtering, decryption fallback, relevance, SCM budgets.|
|Chatbox entry|`app/api/agent-chat/stream/route.ts` and shared conversation components|Actual user turn orchestration and presentation; inspect acceptance matrix for other entry points.|
|Telegram/other paths|`docs/agent-run/EXECUTION-PATH-ACCEPTANCE.md`, `lib/integrations/telegram-agent-turn.ts`, `app/api/extensions/telegram/`, shared runtime|Map exact handlers before edits; Telegram is transport, not a second behavior engine.|
|Onboarding|`lib/onboarding-draft.ts`, owner draft hook/page/StepRouter, `app/api/onboarding/complete/route.ts`|Owner CAS/resume, optional AI-connect, bounded display-only plan data and completion persistence.|
|Saved run UI|`app/vms/memory/promotion/page.tsx`|Read back original run; retain hold on uncertainty; safe guidance.|
|Computer UI|`components/vms/conversation-dock/AgentComputerView.tsx`|Truthful wake/refusal/unsent action state.|
|Attention|`docs/agent-run/evidence/global-attention-plan/dag.json`, `docs/agent-run/evidence/global-attention-cutover-inventory/CHECKLIST.md`, relevant notification/readiness adapters|Six-source recovery, convergence and disabled cutover gates.|
|Tests|`tests/unit/`, `tests/fixtures/`, `tests/qa/`|Unit, actual component/transport, native PostgreSQL and browser receipts are different scopes.|
|Scratch database|`scripts/checks/scratch-postgres.mjs`|Disposable qualification only; final Docker server readiness.|
|Release/backup|`scripts/qa/agent-run-standalone-backup.py`, production backup/roles helpers and release evidence/runbooks|Source-pinned capture, separately approved lock/run, exact outcome reconciliation.|
|Migrations|`supabase/migrations/` and phased profile evidence|Follow current installed ledger/profile; never replay installed packets or include experimental SQL by inference.|

Use `rg` against the exact checkpoint to locate symbols; line numbers move. The execution plan includes source paths for all 32 work packages. Read branch-specific handoffs before composition; dependency commits can be duplicated.


Additional current paths:

- `app/api/agent-execute/route.ts`, `lib/private-ai-workspaces/agent-submission.ts`, `headless-result.ts`: accepted headless original and result recovery.
- `app/api/system-workflows/[id]/research-run/route.ts`: signed original Research readback; read-only builder is now conservatively cataloged as unresolved; E3 is not waived.
- `lib/vms/workflows/execution-engine.ts`, its checkpoint helpers and workspace tools: generic workflow immutable dispatch authority from main. Distinguish this from `lib/vms/coordination/system-workflow-engine.ts`.
- `docs/agent-run/evidence/headless-result-20261002/`: uninstalled candidate SQL on `codex/headless-result-20261002`, plus PRECONDITION/VERIFY/ROLLBACK on `codex/headless-formal-20261003`; not yet on the canonical coordination branch; relevant headless source is already composed into the application candidate. Compare ancestry before cherry-picking.
- `scripts/qa/agent-run-web-candidate-observation.py` (on isolated `codex/l12-web-candidate-observation-20261003`, not canonical yet) and backend/router observation helpers: bounded passive release observations; follow branch README before composition.
- `tests/integration/headless-result-postgres.test.ts`, `headless-result-formal-postgres.test.ts`: native SQL qualification in the composed application candidate; historical isolated branches remain available. The coordination branch alone is not the application source. Environment-gated skips are not passes.
- `tests/unit/workflow-dispatch-authority.test.ts` (isolated `codex/agent-run-main-refresh-20261003`, not canonical yet): real browser assertions at 1440/390 as well as source/behavior tests.

## Private evidence and access

The private engineering handoff contains the complete host/source/receipt inventory, safe monitoring commands and exact attempt identities. Historical workstation folders, private logs, screenshots, database archives and credentials are not replicated by cloning. Obtain authorized repository and host access through normal sign-in; never paste secrets into chat. Source branches and committed evidence are portable through Git.

## Release and external dependencies

**L00 — exact profile/schema.** Prior bounded read-only snapshots checked installed prerequisites and inactive before-schema state, but separate snapshots do not establish one atomic release boundary. Recheck actual migration role/ACL, installed ledger, numbering and phase transitions. Never replay installed migrations or add experimental packets merely because they exist. `docs/agent-run/evidence/research-release-order-20261002/README.md` covers required schema-before-application ordering: ordinary editor/activation paths can reach uninstalled CAS even with feature flags disabled.

**L10 — continuous writer exclusion.** Old direct database writers share the postgres role and can reconnect. A REST admission flag, NOLOGIN, one idle connection census or absence of recent effects does not prove exclusion for the full migration window. Actual network restrictions and process/ingress authority must be identified, then continuously verified. Owner reported restrictions enabled but current IPv4/IPv6 CIDRs and UTC readback are unknown. Claude was requested for this; a fresh read-only `claude auth status` at2026-10-03~18:25UTC still reports loggedIn:false in this session. Another Terminal/account login cannot be assumed accessible here. Do not claim Claude or Grok evidence that did not happen.

**L11 — restore fidelity.** The helper matched 826/826 tables, rows/ledger and role/data authority, but the wrapper rejected an expression-catalog fingerprint. That archive covers public and supabase_migrations, excluding managed auth/storage/vault schemas; it was coherent but taken while application writers remained active, not a drained release-window or whole-cluster backup. Overall restoreVerified remains false; old statements that role fidelity itself still failed are superseded by this narrower diagnosis. Reviewed lossless expression framing is composed in `scripts/qa/agent-run-production-backup.py` and staged with `scripts/qa/agent-run-standalone-backup.py`. Read [current capture preparation and exact helper hashes](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/evidence/l11-next-capture-readiness-20261002/README.md) before preparing a successor; it distinguishes expired plans from a fresh authorized attempt. The old 75455 plan expired and must not be replayed. Last retained AWS space61.248 GiB was below 85 GiB admission; recheck. A fresh bounded source-pinned capture/plan and its concrete shared-lock approval are required. Prior lock approval was consumed; sites stay online while deployments wait. Standalone restore alone does not close migration-role and writer-drain rehearsal.

**L12 — release coordination.** Retained reopen authority, journal ownership, lost ACK, contenders, schema transition, backend/cron/web observation and recovery must compose into one reviewed real operator. Current observers explicitly do not establish complete health or continuous writer exclusion. Qualify on restored-copy/native transport before production.

**Owner authorization.** Automatic migrations were expressly approved on 2026-10-02. Do not ask again merely for routine qualified migration. This does not bypass current technical gates or grant an unbounded shared cross-project deployment lock.

**Providers.** Link is settled; application and live Stripe account exist, but actual approved client configuration and Stripe-delivered credentials remain unverified. Partner-generated public `.asc` is not the provider secret. Callback `https://supraos.ai/api/vms/link-agent-wallet/callback`. Migadu/mail.supraos.ai is settled; subscription, securely installed credentials, authorized DNS and real delivery remain. Independent human browser-image publication reviewer/protected environment remains unresolved; initiating jtobkin self-review is insufficient. Never request secrets in chat, restart Privacy.com, make purchases, alter DNS or send consumer tests without their specific authorization.

## Immediate blockers by type and next owner

This table is a resume order, not a reduced definition of finished. The full 32-package graph and original 62-task acceptance ledger follow it.

| Delivery dependency | Type | Next owner | Proof that closes this dependency |
|---|---|---|---|
| Frozen f74 full-unit verdict | Evidence | Qualification worker, independent reviewer | Original unit terminal, exact report/log/member hashes and independent result review; retain all failures/skips |
| Exact f74 clean production build | Code/setup, capacity and evidence | Qualification worker, root integration | Fresh clean source with repaired launcher layout, current required admission/gates, successful terminal build and source-bound review; never launch the obsolete a9f9 draft |
| Remaining actual browser/native and 17-packet schema proof | Evidence and host capacity | Qualification worker | Real required paths and role-bound forward/rollback/reapply/invariants under unchanged resource floors; skipped environment gates do not pass |
| Continuous writer exclusion and old-web cutoff | Code, access and evidence | Implementation worker, authorized operator | Real production constructor/callers, actual network-policy readback, all-origin admission/drain proof through the complete migration interval |
| Faithful restored-copy rehearsal | Capacity approval and evidence | Release operator, independent reviewer | Fresh concrete source-pinned plan, sufficient disk, specific shared-lock authority, complete role/catalog/data fidelity and tested recovery; earlier consumed approvals never replay |
| Joined release operator | Code/integration and evidence | Root with implementation worker | Same original journal coordinates ingress, writer barrier, schema transition, backend/web observations and retained reopen/unknown recovery; qualify restored-copy transport before production |
| Provider readiness and browser publication | External configuration and specific authorization | Authorized provider/admin owners | Actual approved Link configuration, secure credentials and authorized qualification; Migadu subscription/DNS/delivery; eligible independent publication review |
| Deployment, activation, all paths and all 16 baseline behaviors | Integrated release/live evidence | Root, operator and independent verifier | Qualified phased release, actual configuration/source readback, authenticated live cases, monitoring and recovery; no task acceptance based on code presence |

QA and production capacity are separate dependencies. The QA readback near 19:00 UTC was 32,574,349,312 free bytes (about 30.34 GiB): the active full suite was admitted under its 18 GiB start floor, but a fresh build stage requires 31 GiB, a build launch 30 GiB, and the broad native/schema packets 35 GiB. Recheck before any new admission and never lower a floor. The last retained AWS production readback was about 61.25 GiB against an 85 GiB backup floor; the pending AWS volume proposal does not increase the Hetzner QA disk.

The existing [production capacity proposal](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/evidence/pending-production-capacity-20261004/README.md) is now preserved in the private repository with its exact source/receipt hashes, rather than only on the original Mac. It proposes AWS gp3 300→364 GiB plus a recovery snapshot; its specific owner approval remains pending. Do not send the request again or assume it approved. Copying this dormant packet did not execute it or authorize any infrastructure change. A default-branch dependency alert is not automatically a failed frozen-source gate; use the source-specific advisory note and the actual policy. Conversely a production-only audit does not certify all dependencies.

## Exact remaining packages

The 32 delivery packages below map to the original 62 acceptance tasks. This dependency overlay does not change the denominator. Each state describes its own evidence scope; a scoped pass does not close its parent capability.

### R00 — Maintain the execution and effect census

**Owner:** root coordination. **State:** in_progress. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Callback exception repaire7ef is locally composed with independent Sol review; unexpected pre-dispatch throws no longer dispatch. Existing intentional lesson-read fallback and broader extension/scheduled/non-REST effect census remain open.

**Acceptance:** Every supported caller is mapped with source locations and a named verification gate; gaps create explicit child tasks. Completed O0/M0 foundations remain credited.

**Source:** `docs/agent-run/EXECUTION-PATH-ACCEPTANCE.md`, `lib/agent-run/action-attempts.ts`, `lib/harness/tool-provenance.ts`.

**Evidence:** implemented partial; tested pending exact joined source; independently reviewed pending exact joined source; merged False; deployed False; live verified False.

### R01 — Finish truthful delegation status

**Owner:** root. **State:** in_progress. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Current delegation UI/ACK/CAS fixes are locally qualified. Original recovery, historical-writer exclusion, full release gates and live acceptance remain; not accepted/deployed.

**Acceptance:** Affected types, focused actual POST and real Chromium at 390/1440; no child text leak or automatic replay; exact Sol audit.

**Source:** `lib/vms/orchestrator/delegate-tool.ts:914`, `lib/conversations/use-agent-chat.ts:592`, `app/api/agent-chat/stream/route.ts:6679`.

**Evidence:** implemented audit repairs composed; final empty-activity wording under browser verification; tested da436: 5 focused actual POST/Chromium cases PASS at390/1440; 181 excluded by name filter;14 delta affected types PASS. Earlier8449:251 hosted/28 native/168types PASS.; independently reviewed Independent Sol narrow source review through74e and da436 empty-state text/assertion PASS; exact Chromium receipt retained.; merged False; deployed False; live verified False.

### R02 — Complete bounded specialist context

**Owner:** Sol implementation lane A. **State:** in_progress. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Current bounded context source is integrated and locally qualified. Complete cross-path context/latency receipts and live qualification within R06/V02/L04; no deployment claim.

**Acceptance:** Timeout/owner/oversize/second-round negatives; affected types; source audit; integrated context receipts and latency. 30 focused WIP tests alone are not qualification.

**Source:** `lib/vms/orchestrator/delegate-tool.ts`, `lib/vms/memory/agent-prompt-augmentation.ts`.

**Evidence:** implemented owned-target repair46d688 composed inaccd; tested 54 initial+46 repair focused cases; joined564-case batch and168 affected files PASS; independently reviewed independent Sol trailing source pass at46d688; root preserves personal-mode forwarding; merged False; deployed False; live verified False.

### R03 — Build exact handoff authority

**Owner:** Sol implementation lane B. **State:** in_progress. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Production-shaped restored catalog, actual migration-role proof, old/future writer fences, exact joined profile, installed KMS and live acceptance. Formal VERIFY/reverse is now composed; no SQL installation.

**Acceptance:** Native PostgreSQL/PostgREST race, revoke, expiry, ACL and lost-ack tests; exact audit. Do not mount until legacy writer fences and signed review are qualified.

**Source:** `lib/vms/coordination/session-manager.ts`, `docs/agent-run/evidence/r03-handoff-formal-20261002/README.md`.

**Evidence:** implemented Unmounted real wallet/session anchor repair4df3+384d composed563b/6c6; native tenant-DEK v2 evidence0d01 composedb40d.; tested Root aeda actual PG17/PostgREST/SDK:3 fenc:v2 cases PASS including first-use;2 fenc:v1 PASS+v2-onlySKIP. Standalone first-use4native+10unit+12typesPASS. Prior10signed andjoined46callback/MCP/handoffunit receipts retained. Formal packet exact142 hosted PG17 PASS; five receipt hashes verified; composed4bfc.; independently reviewed Independent Sol source review initially blocked4df3 for post-mutation authorization;384d repair passes with pre-apply anchor check.; merged False; deployed False; live verified False.

### R04 — Mount reviewed handoff and graph upgrade

**Owner:** Sol B repairs; Sol C exact-source hosted qualification; root independent review and composition. **State:** in_progress. **Dependencies:** R01, R03.

**Remaining:** R03 and R04 formal packets composed. Exact joined release profile requires target inventory, actual migration-role proof and restored-copy qualification, then installed catalog/KMS/live acceptance.

**Acceptance:** Actual approved specialist workflow succeeds; denied/stale/unknown retains original outcome and cannot fallback; real review UI; schema/profile qualification before installation.

**Source:** `lib/vms/coordination/trigger.ts`, `lib/vms/coordination/session-manager.ts`, `lib/vms/coordination/seed-factory-workflows.ts`, `lib/vms/coordination/factory-workflows.ts`, `docs/agent-run/evidence/r04-signed-caller-blueprint-20261001/README.md`.

**Evidence:** implemented Reviewed signed approval POST is mounted through applyReviewedSessionHandoff; PendingRequestsSection wires approveExact. Signed GET/detail/held UI and formal packets are composed with existing legacy/dormant writer guards. SQL is uninstalled; actual installed catalog/KMS/profile/old-writer/live proof remains open.; tested Browser314 PASS390/1440, formal123c nativeforward/VERIFY/reverse/reapply/racePASS; integratedapproval122PASS.; independently reviewed Independent source reviews cover composed signed advisory GET/detail, signed action/approval wiring and formal packets. Source review does not establish installed authority, legacy-writer exclusion or live acceptance.; merged False; deployed False; live verified False.

### R05 — Close remaining workflow and tool outcomes

**Owner:** Sol A: release companions; Sol B: reachable integration and trailing audit; Sol C: native races; root: joined qualification. **State:** in_progress. **Dependencies:** R00.

**Remaining:** Legacy exact output/lifecycle ACK andnative17dedicatedadmission proof nowcomposed; finaljoinedparallel/terminalauthority and deployedlivequalificationremain.

**Acceptance:** Counterexample-driven tests at real adapters, fresh denied grants, lost replies, no-repeat original recovery; checked durable rows and display on each affected path.

**Source:** `lib/vms/workflows/execution-engine.ts`, `lib/vms/workflows/outcome-delivery.ts`, `lib/harness/tool-provenance.ts`, `lib/agent-run/action-attempts.ts`, `app/api/agent-execute/route.ts`, `lib/vms/coordination/node-handlers.ts`.

**Evidence:** implemented Explicit saved Research editor action and owner-signed route are composed with bounded dedicated admission, stable retry identity and read-only lost-reply recovery. Shared legacy coexistence implemented; all supported workflow paths and live/provider acceptance remain open.; tested Legacy output9nativePASS; final lifecycle5e47 native10PASS, efd independent801PASS/5SKIP, integrated74testsPASS; Exact23da native17/17 PG17/PostgREST PASS with clean scratch; manifest83287c6070e06c9081b74ec7451a4828b5de8c7869363647021d782436e74da6. Editor formal adc6 hosted PostgreSQL 17 passed; composed2182, root verified five receipt hashes.; independently reviewed Independent Sol feed review and MCP repair source review PASS through2dbe; actual MCP editor browser unresolved. Independent census reviewed before implementation; frozen8365 independent trailing source review found no narrow blocker. Exact4ce source review found no narrow blocker; saved-editor/browser/live not qualified. Independent Sol8e/a593 reviews found no remaining narrow blocker; original admission-race finding retained. Frozen32fd independent narrow source audit found no remaining blocker; native and product-entry acceptance remain open.; merged False; deployed False; live verified False.

### R06 — Integrate the shared contract across every path

**Owner:** root integration; two independent Sol implementation/audit lanes. **State:** in_progress. **Dependencies:** R01, R02, R04, R05, S01, R00.

**Remaining:** Headless original-result source and formal/real PG+PostgREST recovery composition are integrated in frozen ae2f, alongside saved-answer routing. Scoped native/browser evidence passed; installed schema, whole-path terminal authority, cross-path context/latency and authenticated live acceptance remain. Historical isolated/pending labels in older receipts are superseded only within their exact evidence scope.

**Acceptance:** Per-path current preferences + next-turn readback, bounded context and receipts, denied effects, original unknown recovery, durable truthful terminals. Personal chat cannot qualify other paths.

**Source:** `docs/agent-run/EXECUTION-PATH-ACCEPTANCE.md`, `app/api/agent-execute/route.ts`, `lib/vms/coordination/node-handlers.ts`, `lib/vms/workflows/execution-engine.ts`, `lib/vms/coordination/system-workflow-model-audit.ts`, `lib/vms/coordination/workflow-model-preferences.ts`.

**Evidence:** implemented Root7ce composes scoped THINK/search failure truth, unsupported memory-sync write/lock refusal, late fast-dispatch fences, and fast/direct saved-reply publication guards with neutral stream opening. Rootbd30/9c54/e93 adds read-only grant preflight and lane cancellation through canonical tool admission, including joined actual POST wrapper regression. Composed bounded saved-reply observation6824 and all-eight System model deadline bridge038b. Root23f0 rejects malformed node/SLA timeout configuration before handler entry. Root7b7cec includes bounded owner-only canonical preferences in all eight System model calls, with initial/post-import expiry guards. Final242b caps running nodes by original totalSLA and includes unmounted exact System/null-actor context provenance with scalar/budget binding.; bounded System preference/provenance post-transformation callbacks now mounted in a542 and joined61b8370b13; joined9c25 bounds original ordinary lifecycle and shared terminal persistence window, separating required checkpoint ACK from diagnostic telemetry; main merge 479c16784a incorporates main 896fae592b, and 348c22ec07 binds all eight System model calls to explicit null-agent/internal-SCM audit while preserving original node signal/deadline and prepared-context callback; tested Fresh-lockfile root7ce:350 checks in12 workflow/handoff/room suites and8 actual POST save cases PASS;186 cases excluded by POST name filter. Adjacent-main e53:377 checks in10files PASS. Current418-file delta typesPASS at6144MiB; original4096MiB heap failure retained. Real-browser/current full qualification pending. Current8365:103 grant/fast/provenance tests and12 actualPOST cases PASS;63delta typesPASS. Browser/native still pending. Joined save6824:82 helper/fast plus14 actualPOST PASS,186 filtered;29 delta typesPASS. System038b:112 checks/5files and37 delta typesPASS. Timeout23f0:42 root tests/29types PASS; independent44checks PASS/1optionalbrowserSKIP. Joined7b7cec:169 checks/8files PASS,1optionalbrowserSKIP;32 affectedtypesPASS. Final242b:114 tests/9filesPASS,1optionalbrowserSKIP;53 affectedtypesPASS. Initial totalSLAfixture mismatch retained and correctly separated in2f40.; root127 cases/7 suites and18 mount-specific cases PASS; adapter64PASS, overlapping coverage; root9c25 four lifecycle suites38PASS/1optionalbrowserSKIP; author425PASS/3SKIP and42types; identity author five focused suites72PASS and33 affected typesPASS on frozen15ea91; root final348 exact-source checks pending Isolated96dad actual private PG17/PostgREST System identity/context append11/11PASS,11-filetypesPASS; reduced-schema/signing/provider limits retained. Source96dad plus evidenceb6a2 preserved separately.; independently reviewed Independent Sol bounded source audits for THINK6be, web-search982, memory-sync66dd, fastbd8, actualPOST913, directdfe and final joined chat7ce. Initial fast candidate audit failures are retained; no full-path/live approval. Independent Sol grant135/signal2fa/joinedPOST713 source reviews found no narrow blockers; native/browser limits retained. Final save chain dfd..a424..c1b and System deadline243 have independent exact-source Sol reviews without narrow blockers; earlier save races retained. Exact23f0 independent Codex audit found no narrow blocker. Exact810c independent source review and28 additional helper/engine checksPASS; initialb694 late-read finding retained. Independent7daf/7ddb source audits and additional actual Sol trailing reviews of final242b PASS within narrow scope; no mounted/native/provider approval.; d8c independent108 cases and separate Sol72 cases/source review PASS, scope-specific; independent Sol413a lifecycle source review and38PASS/1optionalbrowserSKIP; independent Sol source review of exact identity15ea91 found no narrow blocker for eight-call identity/SCM/House Rules boundary, with no positive agent-memory/provider claim Independent Sol96dad native fixture source audit closed missing disposable-role setup finding; no remaining narrow blocker.; merged False; deployed False; live verified False.

### S01 — Finish original room lifecycle integration

**Owner:** Sol B isolated room schedule fence. **State:** in_progress. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Missing receipt-column schema blocked full ratchet. Reviewed original_aware mode now refuses before DB request/slot mutation; legacy default unchanged.29focused/16types/columnratchetPASS, independent reviewPASS. Actual original room transfer/store/schema and old-worker exclusion remain unfinished; hold is not implementation acceptance.

**Acceptance:** Native concurrent stale-settings/slot/late-worker cases, actual room UI/SSE/browser, terminal retained history and old-writer drain. Existing legacy repairs do not qualify original producer.

**Source:** `lib/vms/rooms/huddle.ts`, `lib/vms/rooms/huddle-sweep.ts`, `lib/vms/rooms/room-original-turn.ts`, `lib/vms/orchestrator/meeting-indexer.ts`.

**Evidence:** implemented Explicit original-aware atomic schedule claim guard composedad4b; missing private columns refuse without weaker fallback. Actual default remains legacy.; tested 15 author SDK/sweep tests and16 affected types PASS; joined root81 room/reminder checks PASS.; independently reviewed Independent Sol21d644 source review PASS within unmounted claim scope.; merged False; deployed False; live verified False.

### N01 — Mount original reminder scanner safely

**Owner:** Sol A isolated reminder bridge. **State:** in_progress. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Implement actual durable cursor store and qualify installed SQL; prove old v1 worker exclusion/drain before mounting original service. Existing per-transaction REST admission probe cannot exclude an old JS worker after reopen; do not replace it with a misleading pre-append probe.

**Acceptance:** Actual SDK/PostgREST/PG tests, cursor crash/retry, expiry/supersession/long lineage, before-state history, no duplicate notifications, existing job/route integration. No new timer.

**Source:** `lib/notifications/task-reminder-original-selector-service.ts:7`, `lib/notifications/task-reminder-scan-reader.ts:6`, `lib/user-tasks.ts:31`.

**Evidence:** implemented Bounded unmounted scan/selector bridge composed883b; original cursor CAS/readback required before promotion; v1 job unchanged.; tested Author and independent135 checks PASS;11 affected types PASS. Joined room/reminder root81 checks PASS across4 files; overlapping scopes.; independently reviewed Independent Sol6a176 source and135 focused checks PASS within unmounted scope.; merged False; deployed False; live verified False.

### G01 — Complete six-source attention and recovery

**Owner:** unassigned. **State:** ready. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Joined dispatcher → actual macro-loops GET → recovery worker is fixture-qualified and composed, with saved original cursors and lost-ACK recovery. Remaining: current packet compatibility, production writer exclusion, full six-kind terminal/checkpoint and provider integration, activation/live recovery. Global attention cutover remains0.

**Acceptance:** Fresh composed native readiness/claim/recovery and source receipts; bounded finite scans survive lost replies; LC producer and legacy-display policies audited together.

**Source:** `lib/notifications/global-attention-batch.ts:27`, `lib/notifications/living-contract-attention-retention.ts:18`, `lib/supraos-build/living-contracts/note-recovery-worker.ts:16`, `app/api/cron/macro-loops/route.ts:70`.

**Evidence:** implemented partial; tested Isolated be915 exact private PG17/PostgREST joined worker1/1PASS (3.42s),10-file typesPASS. Lost committed-note HTTP ACK, blocked second note, failed observation child, exact retained cursor lower bound and original note identity are asserted. First58e setupRED retained; phase verifier ordering repaired without SQL edits. Successor1196af2bc6 native1/1PASS in7.70s; actual GET/dispatcher PG17/PostgREST, clean scratch/source. Earlier7e URL predicateRED retained; corrected getAll requires both upper/lowerbounds. Reduced-schema controlled siblings/telemetry, not live cron.; independently reviewed Independent Sol be915 source review found no narrow test-scope blocker. Production roles, actual macro-loop dispatcher persistence, cutover and live acceptance remain unqualified.; merged False; deployed False; live verified False.

### G02 — Converge remaining attention producers

**Owner:** unassigned. **State:** blocked. **Dependencies:** G01.

**Remaining:** Close writer-by-writer ordinary notification, generic event-bus, legacy pending/unclaimed and exception policies. Preserve explicit report schedules and trusted urgent evidence. Keep cutover zero.

**Acceptance:** Cross-producer native cadence/quiet-hour/DST/preference/revoke races; real inbox/toast/detail/browser with no double interruption; no model-prose urgency bypass. Audit room/reminder/event-bus intersections independently of new producer completion; all-path baseline still requires S01 and N01.

**Source:** `docs/agent-run/evidence/global-attention-cutover-inventory/CHECKLIST.md`, `lib/notifications/attention-cutover-contract.ts:5`.

**Evidence:** implemented partial; tested pending exact joined source; independently reviewed pending exact joined source; merged False; deployed False; live verified False.

### D01 — Qualify imported digest execution and writes

**Owner:** unassigned. **State:** ready. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Finish original-session reservation/claim/accounting/settlement plus authenticated memory-write composition and same-token recovery. Current user-facing producer remains execution_unqualified; saving limits must not dispatch.

**Acceptance:** Actual SDK/PG/pgvector source races, native writer/consumer union, bounded cost and lost-reply cases; producer only mounts after atomic admission proof. No paid call in fixtures.

**Source:** `lib/agent-import/digest-runtime.ts:11`, `lib/agent-import/digest-execution-lifecycle.ts:76`, `lib/agent-import/digest-memory-writer.ts:103`.

**Evidence:** implemented partial; tested pending exact joined source; independently reviewed pending exact joined source; merged False; deployed False; live verified False.

### D02 — Finish digest downstream containment

**Owner:** unassigned. **State:** blocked. **Dependencies:** D01.

**Remaining:** Reconcile embedding/compression/dreaming/conflict consumers with current writer, source ancestry and mutable-row exclusion. Preserve held/unbound sources; no permission inferred from existing memory.

**Acceptance:** Exact combined source/native tests, old derived ancestry and late mutable-source cases; total deadlines; no unqualified paid derivation or leakage.

**Source:** `lib/memory/imported-digest-embedding-policy.mjs`, `lib/agent-import/digest-memory-preparation.ts`.

**Evidence:** implemented partial; tested pending exact joined source; independently reviewed pending exact joined source; merged False; deployed False; live verified False.

### H01 — Close state-history and writer coverage

**Owner:** unassigned. **State:** ready. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Editor and activation CAS callers and formal safeguards are composed; profiles integrated at da567 with exact reviewed blobs, native1/1 and110 affected Python checks PASS. SQL remains uninstalled. Actual migration-role/restored-copy rehearsal, direct-writer authority, admitted schema-before-app rollout and live history-before-state/readback remain.

**Acceptance:** Strict inventory gate plus native lost-ACK, cross-owner, prehistory failure and next-turn readback proofs for each changed writer. Reconcile current counts; do not waive hazards.

**Source:** `lib/agent-run/owner-preferences.ts`, `lib/harness/tool-provenance.ts`, `docs/agent-run/evidence/global-attention-cutover-inventory/CHECKLIST.md`, `lib/agent-run/action-attempts.ts`.

**Evidence:** implemented partial; tested pending exact joined source; independently reviewed pending exact joined source; merged False; deployed False; live verified False.

### P01 — Complete independent readiness and Guide qualification

**Owner:** unassigned. **State:** ready. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Main 896 AI-connect flag-off step was composed with owner-scoped resumable Guide draft/CAS in merge 479c. Exact348 hosted owner-draft Chromium r2 passed flag-off/on and owner-switch resume, plus the existing onboarding page browser. Full current-source types, independent readiness and live provider qualification are still required; saved plan display is not provider readiness.

**Acceptance:** Main-admin refusal, independent capability failure/recovery, resumable setup and history-before-change; actual browser; live provider acceptance remains separate.

**Source:** `lib/agent-run/capability-readiness.ts:29`, `lib/onboarding/guide-owner.ts:11`, `lib/onboarding/guide-preference-change.ts`, `components/onboarding/CapabilitySetup.tsx`, `lib/onboarding-draft.ts`, `app/onboard/hooks/useOnboardingState.ts`, `app/onboard/page.tsx`.

**Evidence:** implemented Onboarding conflict resolution in merge 479c preserves verified wallet owner hydration, server revision CAS, Guide save flush, dynamic flag-off/flag-on AI step and bounded optional display-plan draft schema.; tested Composition worktree: three focused API/unit suites16PASS, including signed-owner AI-step round-trip, foreign-owner isolation, credential stripping, malformed provider refusal and flag-off step order. Exact348 hosted owner-draft Chromium r2 passed flag-off/on and owner-switch resume; existing onboarding capability page browser passed. Current-source changed types and provider checks pending.; independently reviewed Onboarding merge source and narrow tests reviewed in composition; independent final UI/browser and readiness audit pending.; merged False; deployed False; live verified False.

### P02 — Prepare and qualify Link credentials

**Owner:** unassigned. **State:** external. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Confirm actual Stripe-issued encrypted credentials and approved client configuration through secure setup; the owner-generated public .asc is not the Stripe secret. Preserve settled Link choice/callback.

**Acceptance:** Secure configuration, real consumer OAuth onboarding and exact owner-approved purchase limit/receipt; no secret in chat/logs/GitHub; no purchase without specific approval.

**Source:** `lib/integrations/link-agent-wallet/`, `docs/agent-run/evidence/provider-setup/LINK-REGISTRATION-AND-ACCEPTANCE.md`.

**Evidence:** implemented see evidence; tested pending exact joined source; independently reviewed pending exact joined source; merged False; deployed False; live verified False.

### P03 — Prepare and qualify Migadu mailbox

**Owner:** unassigned. **State:** external. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Prepare exact subscription, secure credentials and mail.supraos.ai DNS steps using settled provider. No DNS, purchase or test send until separately authorized.

**Acceptance:** Real unique mailbox inbound to same private conversation, current credentials/pickup, failure/recovery; receiving-only status stays distinct from sending/browser readiness.

**Source:** `lib/agent-run/migadu-provider.ts`, `lib/agent-run/migadu-mailbox.ts`, `lib/agent-run/mailbox-ingress.ts`.

**Evidence:** implemented see evidence; tested pending exact joined source; independently reviewed pending exact joined source; merged False; deployed False; live verified False.

### P04 — Qualify private computer publication and launch

**Owner:** unassigned. **State:** external. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Resolve independent human reviewer/protected environment, then approved image publication, GHCR→ECR promotion and exact AMI/host launch qualification. Self-review by initiating jtobkin is insufficient.

**Acceptance:** Actual restricted runtime, ingress/privacy/takeover/expiry/replay/handback on released host. Retain separate source, image, host and owner acceptance evidence.

**Source:** `deploy/private-ai-browser/`, `lib/phone-agent/`.

**Evidence:** implemented see evidence; tested pending exact joined source; independently reviewed pending exact joined source; merged False; deployed False; live verified False.

### P05 — Prepare remaining provider acceptance

**Owner:** unassigned. **State:** ready. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Prepare exact target/purpose for approved calls, email edit/send/ignore, Telegram, location and dual-owner friends. Use existing capability/approval records; real calls/messages require specific authorization.

**Acceptance:** Authorized live provider outcomes and revoked/expired/unknown cases; later suppression and cross-channel readback. Configured/simulated is never accepted live. Execution requires L01 and P01; computer-mediated journeys additionally require P04. Preparation is read-only and can start now.

**Source:** `lib/phone-agent/shop-call-media.ts`, `lib/integrations/telegram-agent-turn.ts`, `lib/vms/workflows/email-draft-sent.ts`.

**Evidence:** implemented see evidence; tested pending exact joined source; independently reviewed pending exact joined source; merged False; deployed False; live verified False.

### V01 — Exact-source full qualification

**Owner:** root integration/qualification, Sol A independent review. **State:** in_progress. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Finish managed retry batch0000e, independently audit exact source/gates/build; isolated unchanged PG2/2PASS135.22s is diagnostic only. Native/schema/recovery gates remain.

**Acceptance:** Current required contexts green plus independent exact-source Sol review and actual UI; older full build cannot qualify new source.

**Source:** `scripts/ci/box-ci/merge-if-green.sh`, `tests/native-qualification/`.

**Evidence:** implemented Frozen458f6 runtime PR6168; test-fixture/CI-memory blocker repairs only, no production runtime change.; tested Current458f6:59763unitPASS252skip, changedtypesPASS119s, productionbuildPASS7steps920s. SecurityRED: one integrationtest180s timeout(actual212.6s); prior samefixture139.1sPASS. Independent full-log audits sealed.; independently reviewed Exact managed build PASS independently audited e7ddfc6b; security RED independently audited7f0abfaa. No broadrelease approval.; merged False; deployed False; live verified False.

### V02 — Joined contract and baseline local acceptance

**Owner:** unassigned. **State:** blocked. **Dependencies:** R06, N01, G02, D02, H01, P01.

**Remaining:** Run integration across all included features, 16 original behaviors and all supported paths. Reconcile failed receipts and schema dependencies; never sum overlapping tests as coverage.

**Acceptance:** Each original behavior has exact local source/evidence, truthful blocked external cases, reviewed integration and browser proof; live acceptance is L04.

**Source:** `docs/agent-run/BASELINE-BEHAVIORS.md`, `docs/agent-run/evidence/BASELINE-16-RELEASE-ACCEPTANCE.md`.

**Evidence:** implemented see evidence; tested Partial: ed6 historical fulltypes/715SystemPASS;2160 release rehearsalPASS;5fa signedResearch2PASS;c41 legacy729unitPASS5skip and9nativePASS. Fullunitf7RED remains recorded; final joined matrix pending.; independently reviewed pending exact joined source; merged False; deployed False; live verified False.

### L00 — Reconcile installed ledger and phased profile

**Owner:** Sol B read-only profile; root release coordination. **State:** in_progress. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Fresh production01:53UTC readback confirms six editor/activation RPC names and provisional ledger IDs absent. Actual-role restored-production-copy rehearsal, writer exclusion, phased profile application, current target recheck and final image/recovery qualification remain. Populated workflow/history prevents reverse; do not promise automatic schema/image downgrade. Old backup2db pins are stale; preserve unrun attempt. Research ledger/factory/readiness remain separate before activation.

**Acceptance:** Exact installation preconditions and safe disabled-code schema ordering, native forward/VERIFY/rollback/reapply; full plan independently audited.

**Source:** `scripts/qa/agent-run-release-profile.py`, `scripts/qa/agent-run-packet-rehearsal.py`.

**Evidence:** implemented Headless and ordinary editor/activation numbered packets composed; inactive expand order headless→editor→activation. Activation remains disabled.; tested Headless packet/readback2/2PASS atd7c; editor/activation canonicalpair1/1PASS at91e; postmergeda567 sourcehash validation all3profilesPASS; focused45PythonPASS. Disposable reducedschema does not qualify productionrestore.; independently reviewed Independent Sol source and composition audits clear for included headless/editor/activation packets; full live release audit pending.; merged False; deployed False; live verified False.

### L10 — Finish continuous admission and drain proof

**Owner:** Sol B native caller/PG integration; Sol C host/image; root staging; Sol A independent audits. **State:** in_progress. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Correct volatile nft counters in all pinned readiness producers/consumers, qualify fresh private daemon, then actual loads/probe/network/apps/PG/REST. Strategies context77,962members independently sealed; no image build. Actual writers and joined native proof remain.

**Acceptance:** Actual isolated host/PostgREST lab, continuous hold/drain/recovery, old-worker and late-effects negatives; no unknown operation discarded.

**Source:** `scripts/qa/agent-run-release-host.py`, `scripts/qa/money-release-operator.py`.

**Evidence:** implemented Named Money coordinate-cutoff-run caller holds same coordinator/window through prefix. Reviewed fdce46e9 adds actual read-only companion/runner preflight before REST/cron effects; d550 app phases source only.; tested child identity7/7, owner filesystem6/6, joined journal/port/host3/3 native; external authorities synthetic; actual process restart remains pending; isolated0906/6 and canonicalbcc0 actualPG17 preflight1/1, zero skips. Cron orderly/SIGKILL4/4 uses injected effect log; real Docker/live owner replacement remains pending.; independently reviewed Independent producer/caller/61fd exact composition clear. Native evidence retained within disposable/synthetic predecessor scope.; merged False; deployed False; live verified False.

### V00 — Qualify the included inactive release profile

**Owner:** root coordination. **State:** blocked. **Dependencies:** V01, L00, L10, L12.

**Remaining:** Qualify frozen30875 candidate through managed production build/security/types plus exact Linux browser and native gates. Preserve aef5 schema-only PASS with explicit source scope; no newsource blanketinheritance. Recovery and operator prerequisites remain before deployment.

**Acceptance:** Exact included-source full checks, actual UI/native where relevant, profile-specific independent audit and tested recovery. No schema or safety gate is waived for phased release.

**Source:** `scripts/qa/agent-run-release-profile.py`, `docs/agent-run/EXECUTION-PATH-ACCEPTANCE.md`.

**Evidence:** implemented partial; tested aef5497 private schema-only canonical rehearsal independently PASS17 packets/51 results+catalog checks/9 baseline checks. Production-data restore and exact final-source qualification remain distinct.; independently reviewed Independent Sol expect f7a5cddf and canonical43eb18bc; sealed76members, terminalexit0, empty cgroup/private containers. Original a88d RED retained.; merged False; deployed False; live verified False.

### L11 — Qualify faithful backup and restored copy

**Owner:** root release coordination. **State:** external. **Dependencies:** L00.

**Remaining:** Fresh dfd40ff4/15756ae4 captured09:37:42 expires13:37:42. AWS72.07GiB below85GiB start floor; investigate exact safe capacity remediation. Independent plan audit and specific shared-lock approval required before run. No backup/lock/migration.

**Acceptance:** Fresh coherent rows/ledger/roles/catalog match, snapshot/lock cleanup and exact packet rehearsal; prior approval consumed. No lock/migration implied by this plan. Restored-copy migration/ACL rehearsal under the actual migration role joins L00/V00; synthetic superuser/NOLOGIN fixtures do not prove production authority.

**Source:** `scripts/qa/agent-run-production-backup.py`, `docs/agent-run/evidence/backup-prior-reconciliation-20260930/STAGING-AND-CAPTURE.md`.

**Evidence:** implemented Reviewed dfdc wrapper/helper closure staged privately on AWS with exact source pins; capture-only plan completed with read-only database transaction. No lock or backup acquired; no migration/activation.; tested Root and independent Sol reviewed unchanged guards;26 focused tests pass. Consumed attempt6d79 refused before helper/archive, lock released. Fresh restore remains unproved.; independently reviewed Independent Sol reviewed exact preparation/transport/plan/run packet; audit a4caad9600fc2c9ba3f4eb3edb98520f988d0b42addbdea05ad8793ca298da49. Source clear for exact approval request only; no run or restore evidence.; merged False; deployed False; live verified False.

### L12 — Implement the qualified live release coordinator

**Owner:** Sol release-coordinator lane. **State:** in_progress. **Dependencies:** L00, L10.

**Remaining:** Money arm and monitored coordinate-cutoff-run production caller integration is under test. Confirmed process-local monitor defect repaired WIP by retaining one live run process; crash/unknown never auto-replayed. Exact native isolated fullprefix/lost-ACK and private inbox mount proof pending. Writer/reopen/forward remain explicitrefusals; full releaseprovider construction still open.

**Acceptance:** Native lost-ack/contender/stale-generation/stop/schema-COMMIT/launch/health tests and independent source audit. A running container or REST-only barrier cannot establish complete writer exclusion. Production use additionally requires fresh backup/profile/authorization.

**Source:** `scripts/qa/agent-run-release-profile.py:270`, `scripts/qa/agent-run-release-host.py:303`, `scripts/qa/agent-run-admission-barrier.py`, `scripts/qa/agent-run-live-coordinator.py`, `scripts/qa/test-agent-run-live-coordinator.py`, `scripts/qa/agent-run-live-journal.py`, `scripts/qa/test-agent-run-live-journal.py`.

**Evidence:** implemented Frozen61fd contains reviewed v4 producer/caller and guarded owner preflight. Canonical55eab integrates reviewed701539dce4, which composes090 reader/boundary and cron retain/launch routing with test-only recovery repairs; projection preserves61fd application/SQL/install bytes. No full effectful canonical Coordinator caller.; tested child identity7/7, owner filesystem6/6, joined journal/port/host3/3 native;090 actual-role disposablePG6/6. Separate7015 cron distinct-process recovery4/4 independently PASS (orderly exit and SIGKILL, injected effect log), not real Docker/power loss. Fresh canonicalbcc0 joined Money preflight with actualPG17/090 passes1/1, zero skips; first ownership setup RED retained. No broad writer/ingress or live proof.; independently reviewed Independent exact7015 source and four process tests clear. Root+Sol conflict-free canonical projection verified; two extra canonical backup files match reviewed39f23. Native08aa proof carries four exact inputs only; staged7c full packet differs through cron aggregate and has no terminal result yet. Freshbcc0 33-blob packet and stage-only ownership repair reviewed; root+Sol verify3/3 terminal receipts, manifesta33f0b97. Older7c packet remains unrun and is not relabeled.; merged False; deployed False; live verified False.

### L01 — Deploy qualified inactive foundation

**Owner:** unassigned. **State:** blocked. **Dependencies:** V00, L11.

**Remaining:** Qualified merge and phased disabled release with exact image/source/schema and tested recovery; provider preparation may proceed in parallel beforehand. This is a phased deployment milestone, not automatic closure of original L0; its original acceptance dependencies must independently pass.

**Acceptance:** Required gates and audits pass; observed AWS web/cron/image/health agree; no flag enabled solely because deploy succeeds.

**Source:** `scripts/qa/agent-run-release-profile.py`.

**Evidence:** implemented see evidence; tested pending exact joined source; independently reviewed pending exact joined source; merged False; deployed False; live verified False.

### L02 — Complete provider acceptance after foundation

**Owner:** unassigned. **State:** blocked. **Dependencies:** L01, P02, P03, P04, P05, P01.

**Remaining:** Execute specifically authorized provider journeys and failure/recovery cases with independent readiness. Report exact blocked capabilities.

**Acceptance:** Real approved outcomes for all in-scope consumer capabilities; no test-message/purchase/call without exact permission.

**Source:** `docs/agent-run/evidence/BASELINE-16-RELEASE-ACCEPTANCE.md`.

**Evidence:** implemented see evidence; tested pending exact joined source; independently reviewed pending exact joined source; merged False; deployed False; live verified False.

### L03 — Activate qualified behavior and attention

**Owner:** unassigned. **State:** blocked. **Dependencies:** L02, V02.

**Remaining:** Prepare reviewed source/graph/owner/schema-bound activation with per-capability readiness and tested pause/revoke/recovery. Global attention cannot turn on until producer and drain acceptance.

**Acceptance:** Exact configuration readback, current preference/history linkage and no unsafe legacy admission; activation records retained.

**Source:** `lib/agent-run/activation.ts`, `lib/notifications/attention-cutover-contract.ts`.

**Evidence:** implemented see evidence; tested pending exact joined source; independently reviewed pending exact joined source; merged False; deployed False; live verified False.

### L04 — Verify all live behaviors and recovery

**Owner:** unassigned. **State:** blocked. **Dependencies:** L03.

**Remaining:** Exercise all supported paths and all 16 behaviors after deployment, with authenticated chatbox/TG browser/transport proof, real provider outcomes, monitoring and recovery.

**Acceptance:** Every matrix cell has source-bound evidence; measured latency; truthful failure/unknown; no duplicate effects; tested recovery. Safe unsigned smoke tests alone cannot pass.

**Source:** `docs/agent-run/EXECUTION-PATH-ACCEPTANCE.md`, `docs/agent-run/evidence/BASELINE-16-RELEASE-ACCEPTANCE.md`.

**Evidence:** implemented see evidence; tested pending exact joined source; independently reviewed pending exact joined source; merged False; deployed False; live verified False.

### L05 — Close shipped and working goal

**Owner:** unassigned. **State:** blocked. **Dependencies:** L04.

**Remaining:** Reconcile final evidence, accepted tasks, running source, monitors and operating handoff. Only close when no required gate remains.

**Acceptance:** Implemented, tested, independently audited, merged, deployed, activated and verified live recorded distinctly.

**Source:** `docs/agent-run/plan.json`.

**Evidence:** implemented see evidence; tested pending exact joined source; independently reviewed pending exact joined source; merged False; deployed False; live verified False.

### Z01 — Deferred iMessage

**Owner:** unassigned. **State:** deferred. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Explicitly deferred until chatbox and Telegram release. Retained in historical 62-task ledger; excluded from this release critical path.

**Acceptance:** Separate future scope/qualification; do not count it complete or remove original task.

**Source:** `docs/agent-run/plan.json`.

**Evidence:** implemented see evidence; tested pending exact joined source; independently reviewed pending exact joined source; merged False; deployed False; live verified False.

## Execution order and parallel-agent procedure

Use root plus **three GPT-6 Sol workers**, each with an isolated worktree or nonoverlapping owned files. Package owner labels below preserve historical assignments; a new session must assign current workers explicitly and must not assume old agent IDs or processes still exist:

1. **Root integration owner:** maintain one candidate, review actual callers and dependencies, integrate only audited blocker fixes, keep the plan/handoff synchronized, and own final release decisions.
2. **Implementation worker:** finish current ingress/operator and real caller integration. Every component names its production caller, integration owner and true/false acceptance test. A tested composite with no production constructor remains incomplete.
3. **Qualification worker:** finish immutable whole-run terminal collection, exact-source browser/native/schema/build checks and resource/host prerequisites. It may prepare independent packets while a long run executes, but cannot mutate active inputs or cancel for unrelated changes.
4. **Independent trailing reviewer:** review exact source and receipt hashes, challenge environment/proof claims, exercise real failures/unknowns/recovery, and audit integration. Source approval is never promoted to native/live proof.

Shortest remaining path: preserve the independently verified frozen f74 full-unit PASS and finish its original read-only local archive transfer → prepare a fresh exact-f74 build donor and independently reviewed bounded launch → finish remaining security/build and real-browser/native/schema gates. The fixture/reset repairs are already integrated in f74; do not repeat that composition or chase the later evidence-only branch tip. In parallel, close actual all-origin ingress, continuous direct-writer exclusion, production operator assembly and faithful restored-copy rehearsal. Join these paths before qualified phased migrations and inactive deploy. Then authorized provider qualification, activation, all16 behaviors/all supported callers live, monitoring and tested recovery.

Do not open unrelated improvement lanes. Keep only one heavy qualification admitted at a time where capacity requires it; preparation, source work and review stay parallel. No lost-ACK operation is blindly replayed. Unknown outcomes remain held and linked to the original attempt. Each checkpoint answers: which usable capability advanced; what delivery dependency closed; next blocker/owner/proof; whether we are finishing delivery or accumulating components.

Missing code, missing evidence, missing access and missing specific approval are separate blocker types. Owner migration authorization persists, but does not waive technical gates or a new shared cross-project lock approval. Do not repeat pending capacity approval requests. Keep full scope: an inactive milestone is not project completion.

## Starting from a brand-new computer

If the private clone fails, sign in to the intended GitHub account using `gh auth login --hostname github.com --web` (or the normal GitHub browser flow), then have the owner grant that account access to jtobkin/suprafx-platform. Confirm `gh repo view jtobkin/suprafx-platform` succeeds. Do not paste credentials or private keys. Public documentation is available before private access is granted.


No local memory, SSH identity, environment secrets, accounts or repository access should be assumed. Obtain private repository access through normal GitHub sign-in/owner invitation, never by pasting a token into chat. Read the public checklist first if access is missing.

```sh
git clone --branch codex/agent-run-execution-20260928 --single-branch https://github.com/jtobkin/suprafx-platform.git
cd suprafx-platform
git status --short
git rev-parse HEAD
git log -1 --oneline
```

To inspect an isolated branch after the single-branch clone, fetch its explicit remote-tracking ref without changing the canonical checkout. Example:

```sh
git fetch origin refs/heads/codex/agent-run-check-fixture-20261004:refs/remotes/origin/codex/agent-run-check-fixture-20261004
git worktree add --detach ../supraos-agent-qualification f74bb97818c755527154c8c1633024f525bd2cda
git -C ../supraos-agent-qualification rev-parse HEAD
```

The branch tip may contain a later documentation-only commit (3d952); the qualification checkout intentionally pins f74. Compare with the lane pin in this document. A detached inspection tree is not permission to bypass outstanding gates or overwrite another worker's source. Create an explicitly owned implementation branch when further changes are needed.

Compare HEAD with the current published handoff commit rather than resetting to a historical pin. Fetch separate branches explicitly before composing them. If using an existing checkout, inspect status and process ownership first. Read in order: this handoff; AGENTS.md; CONTEXT.md and all required boot documents; PLAN.md/plan.json; EXECUTION-PLAN-20261001.md/progress.json; BASELINE-BEHAVIORS.md; BASELINE-16-RELEASE-ACCEPTANCE.md; EXECUTION-PATH-ACCEPTANCE.md; global-attention DAG and cutover inventory; session-transfer20260929 README; current release-order and lane evidence.

### Repository-declared bootstrap and verification prerequisites

The read-only setup survey found `.nvmrc` pins **Node 22.23.2**, while `package.json` permits `>=22.11 <23`. The root uses `package-lock.json` and npm; it does not declare a `packageManager` field. Install the pinned Node version through your normal trusted setup. If nvm is already installed, `nvm install` then `nvm use` reads the pin. Confirm `node --version` before dependency installation. Check `id -un` and available disk space as well: the historical Mac could not resolve uid501 and Chromium could not launch, which invalidated native/browser qualification there. Those are environment observations, not assumed defects on the new computer. If SSH fails, distinguish local user lookup from server authentication before changing anything; no new key rotation is requested by this handoff.

The following commands come from repository/CI configuration; they are a fresh-machine recipe, **not a claim that a new clean install was executed during this checkpoint**:

```sh
npm ci --no-audit --no-fund
node scripts/gen-docs-index.mjs
node scripts/generate-vms-manifest.mjs
node scripts/gen-migration-manifest.mjs
node scripts/gen-dead-code-manifest.mjs
npm run typecheck
```

The four generators prepare ignored test/type artifacts. Inspect `git status --short` afterward and retain any unexpected changes. Existing donor dependencies on the historical Mac do not count as a fresh install. Read the exact current `.github/workflows/security-gates.yml` and `.github/workflows/production-build.yml` before full qualification; their ratchets, source scope, resource limits and evidence capture matter. `npx vitest run tests/unit` and `npm run build` are broad, resource-intensive gates, not quick bootstrap checks. Do not run them on a small machine without admission and enough time to finish.

Browser fidelity additionally uses `npm ci --prefix services/hedge-desk --no-audit --no-fund`, Chromium installed by `npx playwright install chromium`, and the required OS dependencies on Linux. The workflow invokes `npx playwright test --config=playwright.fidelity.config.ts` with a unique development-server port and `NEXT_PUBLIC_PLAN_GRAPH=1`. Use the exact affected test runner when qualifying isolated lanes, and retain actual 390/1440 browser evidence where required. Installing a browser does not establish that it can launch in this environment.

Native lanes need PostgreSQL 17 binaries (`PG_BIN` containing `initdb`, `pg_ctl`, `psql`) and the exact PostgREST binary pinned by the lane (`TASK_POSTGREST_BIN`); do not silently replace a retained PostgREST13 fixture with14.18. Some fixtures also require `SUPRAOS_TEST_LOCAL_POSTGRES=1`. Read each lane's runner/config; use only an owned disposable database/socket, never a production DSN. The staged host runner/source/receipt hashes are in the host queue checkpoint. Its admission cutoff belongs to this paused session. After an explicit resume, establish a fresh bounded window, recheck source/HEAD, resource floors and scratch ownership, and retain new evidence under a distinct attempt path; never overwrite a prior receipt or reuse an expired production plan. Docker-backed tests additionally need the approved daemon/image and their own disk floor.

`.env.local.example` documents configuration names. Obtain actual Supabase and server-side secrets only through approved secure configuration; do not copy them into chat or documentation. Signing/provider credentials, the actual migration role, installed-ledger readback, backup archives and authorized host access are separate prerequisites, not generated by npm. `scripts/setup.sh` mutates `.env.local` and contains an older Node>=18 check, so it is not an unattended qualification bootstrap for this source. Fresh infrastructure must be authenticated and inspected before any production command.

Clean up only your own merged worktree after proving merged/current-main ancestry, clean status and no running process; use `git worktree remove` without force. Unmerged/dirty/active/other-agent folders must remain. No blanket worktree prune.

## Keeping the plan, checklist and handoff synchronized

Edit the canonical handoff narrative, `docs/agent-run/plan.json` acceptance ledger and `docs/agent-run/execution-dashboard/progress.json` delivery graph at the same checkpoint. Preserve historical journal entries; replace stale current-state summaries rather than adding contradictory next-action lists. The graph's package ownership labels must be reassigned explicitly when a new session starts.

Regenerate the private plan/artifact and sanitized public documents with the repository-owned tools:

```sh
python3 docs/agent-run/execution-dashboard/render.py
python3 docs/agent-run/render-plan.py
python3 docs/agent-run/render-public-handoff.py --update-private --output-dir ../supraos-agent-public-docs
git diff --check
git status --short
```

The third command reads this canonical handoff, refreshes its generated package section, and writes exactly four public Markdown files to the explicit output directory: the handoff, checklist, execution procedure and README. It has no network or publication effect, refuses the private repository root as its output directory, validates task counts against the original ledger and rejects known private-host/credential markers before writing public output. Its marker check supplements human review; it is not a general secret scanner. Update the narrative checkpoint and release metadata before rendering; the tool cannot infer deployment from code.

Review all diffs and public content. Commit the private documents to the canonical coordination branch using an explicit non-force refspec. In a separately authenticated checkout of `jtobkin/supraos-agent-completion-handoff`, inspect existing status, copy only the four reviewed generated files, commit and push normally. Preserve others' edits. Finally fetch the public files without authentication and compare bytes/commit pins, then record the private/public checkpoint pair. The original workstation's QA publisher is a historical convenience, not a dependency for a new account. Public documentation access does not grant private source or infrastructure access.

## What Finished means, end to end

Every required implementation is integrated into the actual deployed source; exact-source tests and independent reviews pass; correct schema/graph versions are installed in the prescribed order; eligible capabilities are activated with real per-owner readiness; and all applicable execution paths are independently exercised live after deployment. Monitoring, retained recovery and faithful backup restoration work. No required implementation, release or baseline gate remains open.

The 16 original behaviors are: quiet morning; personal reply style; visible shopping; an approved real call; appropriate initiative; private in-chat computer handoff; one useful loose end; mail follow-up with ignored-thread suppression; friend sharing with both consents; an actual agent mailbox; exact authorized payment; trustworthy marks linked to durable evidence; useful bounded personal recall; honest stops; attention protection; and tone/length informed by real context. The baseline evidence matrix defines exact proofs.

Across chatbox, Telegram, background, delegation and System Workflows, demonstrate current scoped preferences, bounded context, history-before-state, fresh permission-before-effect and truthful outcomes. Lost acknowledgements, restarts, retries, absent providers and revoked consent must not invent success or duplicate effects. A partial inactive release is a milestone, not project completion.

## Suggested prompt for the next session

> Resume the SupraOS Universal Agent project from this public handoff and its linked private checklist. Assume no local history, credentials or repository access. Obtain access through normal sign-in, fetch the canonical coordination branch and the explicitly named current application/repair branches, inspect status and running jobs before editing, and read all required boot documents. Preserve the complete scope and62-task ledger. Use root plus three GPT-6 Sol lanes for integrated implementation, release qualification, and independent review. Follow the current dependency order; preserve failed evidence, resource floors and original-attempt recovery. Keep code, tests, audit, merge, deploy, activation and live acceptance separate. Do not claim completion until all16 baselines and all supported paths are live-verified with tested recovery. Report actual current state and any concrete external access/approval gap, then execute the shortest path to a usable release.

## Scheduled pause and current process ownership

New work stopped at19:43UTC as requested. The f74 full-unit service is terminal: after.exit=0, gate=0, fullStarted=true, install inputs unchanged; independent audit verified174members and no running main process/cgroup. Its transient unit later unloaded; the seal and prior identity, not disappearance alone, establish the result. No production migration, deployment or activation is in progress.

The only surviving work at the last observation is the original read-only local evidence transfer, owned by the host worker. Its detailed PID, paths and monitoring instructions are in the private evidence inventory. It must not be duplicated. Published private evidence commit f72f4860f21dc92c8fad6d5775bc375684533ce6 already preserves the terminal summary and independent remote audit. If the local copy is still pending on resume, inspect its existing process and final receipt; missing local archive completion does not erase the independently verified QA result, but must not be called a completed transfer. All implementation lanes are paused; preserve their unmerged worktrees.
