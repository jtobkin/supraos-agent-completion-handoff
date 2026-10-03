# SupraOS Universal Agent Completion Handoff

## Latest qualification checkpoint — 2026-10-03

The full project remains unshipped and inactive. Accepted outcomes remain **5/62 (8.1%)**; this does not measure code completion or effort.

Frozen candidate `c2c8f937e5` finished its Linux unit run: **58,741 passed, 4 failed, 189 skipped**. This is a failed qualification, not release acceptance. The failures are two permission-test fixture bindings, a stale plain-language exception count, and missing writer-catalog entries. Reviewed fixes for the first three are integrated at `8d3ae49ecf`; all 38 related tests pass. The catalog repair remains in the separately reviewed migration-profile lane, without weakening safety checks.

The first profile native test exposed a PostgreSQL fixture setup error before migration execution. A reviewed repair uses a separate bootstrap administrator and the required non-superuser operator; its native rerun remains pending. The clean production build is running. Prior scoped native/browser/type/static passes retain their original limits and do not prove live readiness.

Next: finish the build, qualify the corrected PostgreSQL fixture, integrate the profile, and verify the combined successor before release. Continuous writer exclusion, faithful restoration and live acceptance remain open. A fresh shared-lock backup attempt is prepared but awaits specific approval. All original scope and 16 baseline behaviors remain required.

## Goal

Make the same behavior contract the default across every supported SupraOS agent path: chatbox, Telegram, background work, delegation and System Workflows. Telegram carries messages; the shared platform owns orchestration, memory, preferences, permission checks and learning. iMessage is deferred.

Orchestration must load current scoped preferences and relevant memory, skills and lessons within bounded latency. Preference changes must append before/after history before updating active state, so the next turn sees the saved value. Tools must check current permission before side effects and retain truthful outcomes. Interrupted work must recover the original attempt without unsafe replay. Setup must resume per user, readiness must be independently verified for each capability, and initial Guide rollout must require main-admin authorization.

## Current status

The full project is **not shipped or activated**. Acceptance is **5 of 62 tasks (8.1%)**, with **56 pending (90.3%)** and **1 deliberately dropped (1.6%)**. These measure accepted outcomes, not code written, effort spent or time remaining. Several earlier narrow repairs shipped separately; they do not establish completion of this project.

The frozen application candidate is `1d84264f85d30c30039d31eb436817c17155d4b2`. Its application type check passed on application-equivalent source. Its full Mac unit run finished with 4,517 files passed, 142 failed and 16 skipped; 57,927 tests passed, 177 failed and 674 skipped. Independent triage found 176 environment or derivative failures and one genuine catalog mismatch. The conservative catalog repair passed its focused suite and was integrated; the whole-run result remains RED. Linux qualification and the current production build remain pending. Earlier builds and tests do not qualify newer source.

The separate headless original-result candidate passed its disposable PostgreSQL test after a test transaction fix. Its formal migration verification and conservative rollback rehearsal also passed in disposable PostgreSQL; the mounted-handler/real PostgreSQL/PostgREST recovery test now passed 1/1 (external/auth/model boundaries mocked; not deployed HTTP disconnect proof). An earlier release-routing fixture passed six disposable Docker checks; its newer HTTP transport passed 14 actual socket checks and its exact successor now passed six disposable Docker checks. The full release sequence remains under qualification. Disposable tests are not production acceptance.

Additional checks on the frozen application passed: full application types, lint (zero errors, retained warnings), the pinned secret scan, Electron types, the production-dependency audit (zero reported vulnerabilities), and 427 coordination-harness tests. A 31-command static subset had one workflow error-copy/catalog failure; its isolated repair now passes the full static suite and passed actual Chromium verification: four cases with mobile and desktop screenshots. None of these results replaces the remaining Linux, browser, production-build, release or live acceptance gates.

Code already covers substantial shared workflow context, preference/history persistence, onboarding, original-run recovery and release safeguards. The next milestone is a qualified integrated release, not another isolated feature count. Missing provider readiness, safe database writer exclusion and faithful restore still prevent an honest shipped-and-working claim.

The five credited rows are A2 (workflow run-log helper), A3 (structured result labels), A4 (image validation), O0 (scope/contract grounding) and M0 (memory/latency trace). Their original acceptance is scoped to foundations or evidence; they are not five newly deployed universal capabilities. The deliberately dropped task is B2, the standalone Thinking step; iMessage is separately deferred. The 8.1% figure must not be presented as a production-readiness percentage.

## Current delivery path

Finish and integrate existing work before opening unrelated lanes. Each task needs a named production caller, integration owner, boolean acceptance check and exclusive file ownership. Report implemented, integrated, tested, reviewed, merged, deployed and live-verified separately.

1. Close existing exact-source browser/native checks. Generic Workflow authority passed 41/41 browser cases and was composed into the working branch; the two selected provisional headless browser cases now passed (48 other cases filtered, not a full-file pass).
2. The reviewed main refresh, complete headless chain and editor repair are composed and frozen as `c2c8f937e5536284e9eef1172a68065b8b07463d`. Both unresolved writer hazards remain recorded. Independent composition review found no merge-specific defect. Only demonstrated blocker fixes enter qualification.
3. Independently verify the composed source, real execution paths, full Linux suite and production build.
4. In parallel, establish actual writer exclusion and prepare faithful restore and release coordination. Separate missing code, evidence, access and approval. Preparation can proceed while access is investigated; final release admission cannot bypass writer exclusion.
5. Complete included-profile qualification and initial inactive deployment. Provider acceptance and the joined baseline must pass before activation.
6. Independently verify live behavior and tested recovery across all supported paths. Preserve all 16 baseline behaviors and the full 62-task scope.

No new accepted task, production migration, deployment or activation is claimed in this update. Receipt-scoped passes close evidence dependencies only. The next gate is combined qualification of the frozen candidate. The headless SQL still needs numbered release-profile wiring before schema-before-application deployment; this blocker repair is isolated from the frozen candidate. Other release blockers remain actual writer exclusion, migration-role/profile proof, faithful restore and joined coordination.

## Tasks and dependency graph

A checked task means its original scoped acceptance was met; some rows are foundational helpers or source surveys. An unchecked package may already contain implemented, tested or independently reviewed code. An `in_progress` task means unfinished scope; it does not imply a worker remains running while the session is paused.

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

1. Establish usable qualification capacity, then keep the application candidate frozen while completing full unit, security, type, production-build and actual browser gates. The current Mac native/browser environment and shared-host disk pressure prevented required checks; repeating those unavailable prerequisites is not progress. Preserve failed evidence and qualify repairs on their exact source.
2. Complete joined original-result recovery through the mounted handler and real PostgreSQL/PostgREST. Direct storage and formal disposable database rehearsal have passed; the joined suppressed-acknowledgement case and applicable browsers remain pending. Preserve one original attempt; do not rerun effects to obtain a result.
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
Published checkpoint at this snapshot: `d7cc12da42a3d50bb859c377da52002c4e0424e2` (a documentation/evidence checkpoint; verify the full remote SHA again when resuming).

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

The repository pins Node **22.23.2** in `.nvmrc` and uses npm with `package-lock.json`. After reading repository instructions, use the current CI workflow's clean-install and generator sequence; the private handoff includes the exact commands. Browser qualification needs Chromium and its OS dependencies; native database qualification needs PostgreSQL 17 and PostgREST 14.18 with disposable test databases. A fresh machine will not inherit authenticated host access or securely configured provider/database secrets. The older setup shell script is not a substitute for current qualification instructions.

## Preserved parallel lanes

These branches are pushed to the private repository. They are separate from the canonical branch unless the engineering handoff explicitly records composition. Some dependency commits overlap; inspect ancestry instead of merging every branch blindly.

| Branch (under `codex/`) | Exact checkpoint | Completed proof and remaining gate |
|---|---|---|
| `headless-result-20261002` | `80abed3e59a70e6e90468268f5ea14d3bf4c5e64` | Direct PostgreSQL result storage passed; SQL uninstalled. |
| `headless-formal-20261003` | `d3c568f59ef35fab815b46379963eedc5633b07c` | Formal disposable PostgreSQL verification passed; SQL uninstalled. |
| `headless-joined-postgrest-20261003` | `e28233c0130b61041dd0af6d986b4a4408751872` | Source reviewed; joined real-transport test awaits host capacity. |
| `headless-integrated-provisional-20261003` | `50d41b1c792fc019906d4462b792ad3469122912` | 64 focused tests and affected types passed; native and two browser cases remain unrun. |
| `workflow-config-plain-language-20261003` | `d0446150718c231faba318ed3ad9f88f11266805` | Static tests and types passed; actual component browser gate pending. |
| `agent-run-main-refresh-20261003` | `d871bcbd9f8543c1fbdafee48f5de3207cb19833` | Latest observed main reconciled in isolation; affected types and scoped tests passed, browser pending. |
| `l12-backend-observer-20261002` | `5e45fe48da8db2dd778d7de70cccfa82e54f002e` | 14 actual socket checks passed; latest Docker rerun pending. |
| `l12-web-candidate-observation-20261003` | `3dcba59ebfd58e9fde18c7cb333082cf565605ce` | 11 local checks passed; joined host and operator integration pending. |

The queued joined headless test calls the mounted handler with real database transport but mocked authentication/model responses and a deliberately suppressed committed acknowledgement. It is not a real deployed client-disconnect or provider-readiness test. Those broader acceptance requirements remain separate.

After a single-branch clone, fetch a lane explicitly before inspecting it. Example:

```sh
git fetch origin refs/heads/codex/headless-integrated-provisional-20261003:refs/remotes/origin/codex/headless-integrated-provisional-20261003
git worktree add --detach ../supraos-headless-review origin/codex/headless-integrated-provisional-20261003
git -C ../supraos-headless-review rev-parse HEAD
```

Compare the result with the pin above and read its lane evidence. A passing local fixture does not authorize installation or establish live readiness.

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

The requested pause is in effect. The final host queue did not run its pending native/browser checks because available disk stayed below the admission floor. Sources, failures, evidence and unmerged worktrees are preserved. Resume from the documented gates; do not treat paused tasks or staged tests as completed.

## Original task checklist

This is the original 62-task acceptance ledger. The 32 packages above organize execution dependencies; they are not a second completion percentage. Blocked or pending rows may contain substantial implementation. Only done rows are accepted.

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
