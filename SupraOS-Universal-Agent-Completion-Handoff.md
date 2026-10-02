# SupraOS Universal Agent Completion Handoff

Updated 2026-10-02T18:12:39Z. Work is active; a final pause checkpoint is being prepared. This is a status snapshot, not a live monitor.

## Goal

Make the same behavior contract the default across every supported SupraOS agent path: chatbox, Telegram, background work, delegation and System Workflows. Telegram carries messages; the shared platform owns orchestration, memory, preferences, permission checks and learning. iMessage is deferred.

Orchestration must load current scoped preferences and relevant memory, skills and lessons within bounded latency. Preference changes must append before/after history before updating active state, so the next turn sees the saved value. Tools must check current permission before side effects and retain truthful outcomes. Interrupted work must recover the original attempt without unsafe replay. Setup must resume per user, readiness must be independently verified for each capability, and initial Guide rollout must require main-admin authorization.

## Current status

The full project is **not shipped or activated**. Acceptance is **5 of 62 tasks (8.1%)**, with **56 pending (90.3%)** and **1 deliberately dropped (1.6%)**. These measure accepted outcomes, not code written, effort spent or time remaining. Several earlier narrow repairs shipped separately; they do not establish completion of this project.

The frozen application candidate is `1d84264f85d30c30039d31eb436817c17155d4b2`. Its application type check passed on application-equivalent source. Its full Mac unit run finished with 4,517 files passed, 142 failed and 16 skipped; 57,927 tests passed, 177 failed and 674 skipped. Independent triage found 176 environment or derivative failures and one genuine catalog mismatch. The conservative catalog repair passed its focused suite and was integrated; the whole-run result remains RED. Linux qualification and the current production build remain pending. Earlier builds and tests do not qualify newer source.

The separate headless original-result candidate passed its disposable PostgreSQL test after a test transaction fix. Its formal migration verification and conservative rollback rehearsal also passed in disposable PostgreSQL; joined route/transport recovery remains under qualification. The disposable release-routing fixture now passes its six strict checks; the health observer and full release sequence remain under qualification. Disposable tests are not production acceptance.

Additional checks on the frozen application passed: full application types, lint (zero errors, retained warnings), the pinned secret scan, Electron types, the production-dependency audit (zero reported vulnerabilities), and 427 coordination-harness tests. A 31-command static subset had one workflow error-copy/catalog failure; its isolated repair now passes the full static suite and awaits actual-browser verification. None of these results replaces the remaining Linux, browser, production-build, release or live acceptance gates.

Code already covers substantial shared workflow context, preference/history persistence, onboarding, original-run recovery and release safeguards. The next milestone is a qualified integrated release, not another isolated feature count. Missing provider readiness, safe database writer exclusion and faithful restore still prevent an honest shipped-and-working claim.

## Tasks and dependency graph

A checked task means accepted end to end. An unchecked package may already contain implemented, tested or independently reviewed code.

| Package | Task | State | Depends on |
|---|---|---|---|
| R00 | Maintain the execution and effect census | in_progress | None |
| R01 | Finish truthful delegation status | in_progress | None |
| R02 | Complete bounded specialist context | in_progress | None |
| R03 | Build exact handoff authority | in_progress | None |
| R04 | Mount reviewed handoff and graph upgrade | in_progress | R01, R03 |
| R05 | Close remaining workflow and tool outcomes | in_progress | R00 |
| R06 | Integrate the shared contract across every path | in_progress | R01, R02, R04, R05, S01, R00 |
| S01 | Finish original room lifecycle integration | in_progress | None |
| N01 | Mount original reminder scanner safely | in_progress | None |
| G01 | Complete six-source attention and recovery | ready | None |
| G02 | Converge remaining attention producers | blocked | G01 |
| D01 | Qualify imported digest execution and writes | ready | None |
| D02 | Finish digest downstream containment | blocked | D01 |
| H01 | Close state-history and writer coverage | ready | None |
| P01 | Complete independent readiness and Guide qualification | ready | None |
| P02 | Prepare and qualify Link credentials | external | None |
| P03 | Prepare and qualify Migadu mailbox | external | None |
| P04 | Qualify private computer publication and launch | external | None |
| P05 | Prepare remaining provider acceptance | ready | None |
| V01 | Exact-source full qualification | in_progress | None |
| V02 | Joined contract and baseline local acceptance | blocked | R06, N01, G02, D02, H01, P01 |
| L00 | Reconcile installed ledger and phased profile | in_progress | None |
| L10 | Finish continuous admission and drain proof | ready | None |
| V00 | Qualify the included inactive release profile | blocked | V01, L00, L10, L12 |
| L11 | Qualify faithful backup and restored copy | external | L00 |
| L12 | Implement the qualified live release coordinator | in_progress | L00, L10 |
| L01 | Deploy qualified inactive foundation | blocked | V00, L11 |
| L02 | Complete provider acceptance after foundation | blocked | L01, P02, P03, P04, P05, P01 |
| L03 | Activate qualified behavior and attention | blocked | L02, V02 |
| L04 | Verify all live behaviors and recovery | blocked | L03 |
| L05 | Close shipped and working goal | blocked | L04 |
| Z01 | Deferred iMessage | deferred | None |

## Immediate work and next steps

1. Keep the application candidate frozen while completing full unit, security, type, production-build and actual browser gates. Preserve failed evidence and qualify repairs on their exact source.
2. Finish original-result recovery and its formal database checks. Preserve one original attempt through disconnects and ambiguous acknowledgements; do not rerun effects to obtain a result.
3. Finish release routing and health verification. A running container, a successful HTTP response or a scheduled tick alone cannot prove safe release.
4. Reconcile installed migrations with the exact phased release profile. Verify the actual migration role, rehearse on a faithful restored copy and never replay installed migrations.
5. Qualify backup restoration and continuous exclusion of other database writers through the migration window. Automatic migration authorization is recorded; it does not substitute for these technical checks.
6. Deploy the qualified inactive foundation; verify it independently, finish each provider readiness requirement, then activate only qualified behavior.
7. Exercise all 16 baseline behaviors and all applicable execution paths live, including denied effects, interruption recovery, next-turn preference readback, memory latency and monitoring.

## Parallel execution

Implementation, release prerequisites and independent verification use separate ownership and immutable source checkpoints. Successful local tests are tracked separately from independent review, integration, merge, deployment, activation and live acceptance. Host capacity currently constrains broad checks; resource and permission controls are not lowered to make a check pass.

## External dependencies

Payment-provider approval and securely delivered client configuration; mailbox subscription, secure setup and authorized DNS/delivery verification; required independent publication review; authenticated database network inventory; and a faithful restore remain dependencies. Purchases, DNS changes and consumer test messages require specific authorization. Credentials, configured accounts and simulations alone do not establish readiness.

## Start on a new computer

This public handoff is readable without repository access. The implementation and detailed engineering evidence remain in a private GitHub repository. Obtain access through the repository owner or normal GitHub sign-in; never paste credentials into a conversation.

Private repository: https://github.com/jtobkin/suprafx-platform
Canonical working branch: `codex/agent-run-execution-20260928`
Published checkpoint at this snapshot: `ace9619f54` (a documentation/evidence checkpoint; verify the full remote SHA again when resuming).

On a fresh computer with authorized access:

```sh
git clone --branch codex/agent-run-execution-20260928 --single-branch https://github.com/jtobkin/suprafx-platform.git
cd suprafx-platform
git status --short
git log -1 --oneline
git rev-parse HEAD
```

Compare the full HEAD with the published checkpoint above. A newer remote head requires reading its current handoff and evidence; do not silently reset to an older checkpoint.

If a checkout already exists, inspect its status and preserve changes before fetching. Do not reset or clean it. The entire project is not on main. Read repository instructions before installing dependencies or running code.

Read in order:

1. `SupraOS-Universal-Agent-Completion-Handoff.md` — detailed current engineering state and retained evidence.
2. `AGENTS.md`, `CONTEXT.md` and every required boot document.
3. `docs/agent-run/PLAN.md` and `docs/agent-run/plan.json` — original scope and task ledger.
4. `docs/agent-run/EXECUTION-PLAN-20261001.md` and `docs/agent-run/execution-dashboard/progress.json` — work packages, dependencies and progress.
5. `docs/agent-run/BASELINE-BEHAVIORS.md` and `docs/agent-run/evidence/BASELINE-16-RELEASE-ACCEPTANCE.md` — original behavior acceptance.
6. `docs/agent-run/evidence/research-release-order-20261002/README.md` — schema-before-application release ordering.
7. Referenced exact-source evidence and separate lane handoffs before composing branches.

## Code and data map

| Area | Repository location |
|---|---|
| Headless agent entry point | `app/api/agent-execute/route.ts` |
| Accepted submissions and original results | `lib/private-ai-workspaces/` |
| Workflow execution | `lib/vms/workflows/execution-engine.ts` |
| Shared orchestration and node handlers | `lib/vms/coordination/` |
| Bounded memory and context | `lib/vms/memory/` |
| Workflow API and UI | `app/api/system-workflows/`, `app/vms/workspace/system/` |
| SQL source | `supabase/migrations/`; uninstalled candidate packets are also retained under `docs/agent-run/evidence/` |
| Release verification and recovery tools | `scripts/qa/` |
| Unit, integration and browser checks | `tests/unit/`, `tests/integration/`, `tests/ui/` |
| Architecture | `docs/PLATFORM_ARCHITECTURE.md`, `docs/architecture/agent-run-spine.md` |
| Plan and evidence index | `docs/agent-run/` |

Production data, secrets, private backups and host-local test archives are not contained in this public document and must not be assumed present on a new computer. The private engineering handoff identifies the authorized locations and recovery procedures. Source files named migration or candidate do not establish that SQL has been installed.

## Finished means

All in-scope behavior is merged, deployed, activated where appropriate and independently verified live across its applicable paths. All 16 baseline behaviors pass. Preferences persist with history and next-turn readback; permissions remain separate; outcomes and recovery are truthful; each capability has real readiness evidence; backup restoration, monitoring and recovery work. No required implementation, release or acceptance dependency remains open.

At the requested pause, the private handoff and this public snapshot will be updated with final source pins, completed work, unresolved failures and the next safe execution order.

## Original task checklist

This is the original62-task acceptance ledger. The32 packages above organize execution dependencies; they are not a second completion percentage. Blocked or pending rows may contain substantial implementation. Only done rows are accepted.

| ID | Original task | Acceptance state |
|---|---|---|
| A1 | Shelf | blocked |
| A2 | Use the workflow run log | done |
| A3 | Result labels | done |
| A4 | Picture check | done |
| W1 | The spine is a System Workflow | blocked |
| B1 | Run loads the shelf | blocked |
| B2 | Thinking step | dropped |
| B3 | Shared behavior text | blocked |
| R1 | Tools, skills, and lessons on the picture | blocked |
| B4 | A real screenshot is kept | blocked |
| C1 | Learn a preference | blocked |
| C2 | Claim gate | blocked |
| C3 | Picture reaches Telegram | blocked |
| C4 | Computer and handoff | blocked |
| D1 | Pay tap | blocked |
| D2 | Loose ends | blocked |
| D3 | Busy or open day | blocked |
| D4 | Private computer page | blocked |
| E1 | Email follow-up | blocked |
| E2 | Shop call | blocked |
| E3 | Agent mailbox | blocked |
| E4 | Friend agents | blocked |
| F1 | Location | blocked |
| F2 | Quiet morning | blocked |
| F3 | Marks in the chat | blocked |
| F4 | Screenshot proven in the recipe | blocked |
| G1 | One run, both surfaces | blocked |
| D0 | Retained spend presentation hook (discovered prerequisite) | blocked |
| W0 | Canonical System graph and guarded compiler | blocked |
| W2 | Buffered structured response before presentation | blocked |
| Q1 | Repository guards and migration verification companions | in_progress |
| Q2 | Reconcile current main and audit affected runtime boundaries | in_progress |
| O0 | Ground follow-up scope and preference/memory contracts | done |
| M0 | Trace SCM and working-memory latency | done |
| O1 | Make onboarding owner-scoped and durably resumable | in_progress |
| A5 | Preserve trusted runtime qualification and activation | blocked |
| P1 | Unify preference updates and explicit scope precedence | blocked |
| M1 | Wire topic skills and bounded memory orchestration | blocked |
| O2 | Enforce main-admin setup rollout with existing authorization | blocked |
| A6 | Per-owner capability readiness and verified activation | blocked |
| O3 | Connect onboarding to real capability setup | blocked |
| G2 | Guide can resume setup and update preferences | blocked |
| G3 | Preference-aware proactive Guide follow-up | blocked |
| S1 | Qualify supported chat and signal entry points | blocked |
| X1 | Qualify real spending provider separately from simulation | blocked |
| X2 | Provision and verify actual mailbox capability | blocked |
| X3 | Verify phone and other enabled integrations | blocked |
| M2 | Measure memory UX and recall correctness | blocked |
| Q3 | Integrate follow-up lanes and audit all changed contracts | blocked |
| L0 | Deploy audited disabled candidate for provider qualification | blocked |
| L1 | Prepare final qualified activation and recovery release | blocked |
| L2 | Activate qualified candidate and verify live configuration | blocked |
| L3 | Prove live user journeys and recoverability | blocked |
| L4 | Close shipped-and-working goal | blocked |
| H1 | Prove append-only hash-chain coverage and latest-state linkage | blocked |
| B5 | Implement and prove all 16 original baseline behaviors | blocked |
| LP1 | Integrate official Link SDK and bounded provider contract | blocked |
| LP2 | Connect each consumer Link wallet securely | blocked |
| LP3 | Execute approved purchases with private credentials | blocked |
| LP4 | Use native purchase grant cards and messaging links | blocked |
| LP5 | Qualify Link end-to-end and consumer onboarding | blocked |
| IM1 | Qualify iMessage after Telegram and chatbox release | blocked |
