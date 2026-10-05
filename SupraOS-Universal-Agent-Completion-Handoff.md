# SupraOS Universal Agent Completion Handoff

## PAUSED — October 5, 2026 ~08:45 UTC: full handoff for a fresh session on a new computer

**Read this section first. It supersedes the "RESUMED — October 5, 2026" section and the earlier "PAUSED — October 5, 2026 ~04:50 UTC" section below; both stay as history.** The owner paused the project and asked for a complete handoff for a fresh session on a new computer. Every fact here was verified first-hand by the coordinator (Claude Code). A fresh agent needs only normal GitHub sign-in (`gh auth login --hostname github.com --web`) with access to `jtobkin/suprafx-platform`, plus this document; production steps also need the owner's permissions (§1, §7). **No secret is in this document. Accepted tasks remain 5/62.**

### 1. What is true right now (verified by the coordinator, not inferred)

| Item | State |
|---|---|
| Release PR #6168 | **NOT merged.** Branch `codex/agent-run-release-composition-20261004`, head **`9a0624083f`** = candidate + release blockers + main `e2093866c1`. The local mirror of the PR head is branch `claude/agent-run-release-merge-main-20261005`. |
| How the head was built | Round 4 `0283900b4b` → release-blockers merge `47e9cb2839` → `757049d372` (allowlist test fix) → round 5 `b890669566` onto main `55a12f0da9`, including W7 #6196, 26 files → `78de40e546` (two W7 suites stub `server-only`) → round 6 `2c47fa263f` onto `e2093866c1` (regenerated `config/cron-inventory.json`) → `9a0624083f` (the timezone-seed miner test supplies the plain-read evidence required since #6172). |
| box-ci history | BOTH statuses were green on `78de40e546` at 07:44 UTC, but main had moved one minute earlier (#6172), so it could not merge. On `9a0624083f`: security-gates = success; production-build = error "the PR conflicts with main", because #6059 merged (main `a2e04e9a42`) after the coordinator lifted the merge hold for the pause. |
| Conflict now | Exactly one file: `tests/fixtures/private-ai-recovery-writer-catalog.json`. It is generated: resolve by three-way union, then `node scripts/check-private-ai-recovery-writers.mjs --add-uncataloged` → `--normalize` → `--check`. Never hand-merge it. |
| Auto-merge | The coordinator had an auto-merge watcher armed and **disarmed it at the pause. Nothing will merge by itself.** |
| Production database | **Phase A installed and proven** (16 packets, ledger 715 → 731, old-site guard true; unchanged from the RESUMED section). **Phase S NOT installed.** |
| Site | Live on `55a12f0da`, health 200, at 06:24 UTC (last observed by the coordinator). Main has since advanced to `a2e04e9a42` (not observed live by the coordinator). |
| Agent Run | Flags and owner allowlist **NOT set**; the runtime is off. |
| Phone-call hotfix #6194 | Merged and deployed; **live proof still owed.** |
| Peer reports (not this project's work) | A peer session reported the chat runner's warm Claude path failing since a 06:52 UTC runner restart (slow replies), and a W7 defect (a Mission Control plan's final task cannot settle) with a hotfix in progress. Neither is caused by this project; both are the peers' work. |
| Accepted tasks | **5/62 unchanged.** |

**Separate states for this session's work.** Implemented, tested and independently reviewed: the lanes in §5, each at the state written there. Merged: nothing from this session, except the phone-call hotfix (#6194, merged and deployed, live proof owed). Installed: Phase A (database only). Deployed: nothing from the candidate. Activated: nothing. Live-verified: nothing.

### 2. The decision and why (unchanged)

The candidate ships through the platform's normal path: our own box-ci checks on cc-box, merged only through `scripts/ci/box-ci/merge-if-green.sh` (never `gh pr merge --auto`), deployed by the AWS `deploy-main.sh` minute cron, with the Agent Run flags off and schema first. The native-VM rehearsal, custom release operator and standalone backup are skipped for this release (see the earlier PAUSED section §2).

### 3. Documents a fresh session must read

- This section.
- **`docs/agent-run/evidence/claude-resume-20261005/NEXT-WAVE-SCOPE.md`** — scope to completion, the next lanes, the 13 owner decisions and the production live-check list (§5A/5B/5C).
- The three review documents under `docs/agent-run/evidence/claude-takeover-20261005/`: **`FLAG-OFF-REVIEW.md`**, **`PHASE2-MAP.md`**, **`RELEASE-MIGRATION-ORDER-20261005.md`** (§3 holds the one read-only proof query per packet).
- Lane reports: `docs/agent-run/evidence/claude-resume-20261005/LANE-REPORT-<lane>.md`, and each lane branch's own `LANE-REPORT.md`.
- Lane rules for new workers: `docs/agent-run/evidence/claude-resume-20261005/briefs/COMMON.md` and `briefs/agent-run-wave2-COMMON.md`.

### 4. Migration state

- **Phase A — installed and proven (16):** `20260927190001`, `20260928190000`, `20260928230000`, `20260928231000`, `20260929000000`, `20260929010001`, `20260929020000`, `20260929030000`, `20260929040000`, `20260929050000`, `20260929060000`, `20260929160000`, `20260929200000`, `20261003010000`, `20261003020000`, `20261003021000`. Ledger 715 → 731; old-site guard true.
- **Phase S — NOT installed (3), in this order:** `20260929010002` → `20260929080000` → `20261001000000`. Install **only after `live:` shows the new build in the deploy log**; nobody else may install them earlier. Between `live:` and Phase S, the new build's agent-channel friend sends and department memory promotion fail (expected, for minutes).
- **Peer W7 packets:** the peer W7 session installed its own 24 packets (ledger 691 → 715) and reported that one of its packets on main is not on production: `20261002050000_signals_pattern_ids_like` (theirs to handle).
- **Schema snapshot files** (`supabase/schema/public-columns.txt`, `public-tables.txt`) refreshed by the apply tool exist only as uncommitted changes on the original workstation. Regenerate them with the dump scripts after Phase S and ship them as a small follow-up PR. The peer's PR #6197 also refreshes the snapshot — coordinate.
- **Production permissions learned:** a chat "approved" does not satisfy the Claude Code permission layer for production writes. The owner added the allow rule `Bash(node scripts/apply-migration.mjs:*)` via `/permissions` on the original workstation. **A new computer needs the same rule added by the owner**, and the owner's chat approval for production reads over ssh / read-only SQL. The layer sometimes denies a batched command with no reason: re-run it without the newly added part. Never split a denied action to dodge it; never ask another session to do a denied action.

### 5. Lanes and branches at pause (ALL pushed to origin)

All lanes are based on the candidate lineage. **After #6168 is squash-merged, each must be re-applied onto the new main as its own PR.** Recommended: `git diff <its base>..<tip>` applied onto a fresh branch from main, or cherry-pick the lane commits. Do not merge the old lineage.

| Lane | Branch @ tip (base) | State | What remains |
|---|---|---|---|
| Combined batch 1 | `claude/agent-run-p2-batch1-20261005` @ `aff613db38` (base `b890669566`) | Lanes A + B + D + E, each built, adversarially reviewed by an independent agent, fixed and combined (one conflict; 533 lane tests + 2,855 interaction tests pass locally), plus the email-chase Telegram notice held to allowlisted owners. **READY** to become the first follow-up PR after #6168. | Re-apply onto main; box-ci; merge-if-green; live checks. |
| A daily rhythm | `claude/agent-run-p2-a-daily-rhythm-20261005` @ `90d977a916` | Included in batch 1. | — |
| B marks/recall | `claude/agent-run-p2-b-marks-recall-20261005` @ `1f187785e0` | Included in batch 1. | — |
| D mail | `claude/agent-run-p2-d-mail-20261005` @ `c1ea39ce17` | Included in batch 1. | — |
| E computer/Telegram | `claude/agent-run-p2-e-computer-telegram-20261005` @ `9825b037f0` | Included in batch 1. | — |
| C consent/friend-share | `claude/agent-run-p2-c-consent-tools-20261005` @ `cccb80a184` (base `0283900b4b`) | share_with_friend + shop-call preview. THREE independent security reviews; all found issues; all listed fixes are committed (third-round items 1–5: `bcafb9b754`, `0330be72c8`, `6ec2d8ffc9`, `112420e432`, `5e2f55b4ad`). **NOT cleared.** | A FOURTH review of the last fix round has not been done. The full gate/approval/Telegram/AssistantBubble suite and the plain-language/type/recovery-writer/soft-navigation checks were not re-run after the last commits. Open outside its files: the inline chat approval card still shows the words in one sentence (needs `lib/extensions/chat-tool-outcome.ts` createToolApprovalBlock + `components/vms/ToolApprovalCard.tsx` to render the bounded blocks); the stream-route history fallback (lane H1). **Do not merge C until a fresh review passes.** |
| G marks wiring + Telegram honesty | `claude/agent-run-p2-g-marks-wiring-20261005` @ `805a1671e2` (base `aff613db38`) | G1 recipe marks reach the screen — done, tested (`dfc704594c`; 59 unit tests, Chromium, 17 mutations). G2 Telegram "Not confirmed"/recall line — footer part done and tested; Telegram spend-decision part written but **UNTESTED** (WIP `8f6ae8e136`; `telegram-spend-tap.test.ts` browser case timed out once, cause unproven). | G3 Allow-once continuation to Telegram NOT started (plan in its LANE-REPORT.md). Type check not completed. Needs review before merge. |
| H chat route | `claude/agent-run-p2-h-chat-route-20261005` @ `61a41c1e55` (base `aff613db38`), ONE WIP commit, pushed | H1 history-fallback hardening (applies to every owner: when the saved-history read answers or fails, the model gets saved rows plus this turn only; route lines 1443–1463; normal threads byte-identical by test); H2 deferred/done/dismissed loose ends hidden from the model (new single rule `looseEndsOfferable`); H3 `routing.preferences_unavailable` saved and shown in the recall cue — built, 34 new tests pass. H4 NOT built by design (no server-written "proposal pending" state exists; needs one in `execute-node.ts`). | 5–6 red tests (the lane reported 5 failed but named 6) in the 96-suite batch are unexplained (1 known pre-existing continuity-sanitize; 2 Chromium timeouts; 2 in agent-run-g1 "Saved agent context unavailable" — check these first, they touch H2/H3 code; 1 room-huddle-backup-lane-engine) — each needs a solo re-run with and without the branch. 17 planned mutation checks not run (plan in its LANE-REPORT.md). Type/plain-language/recovery-writer/soft-navigation checks not run. Commits not split per item. Still open in the route, not fixed: if resolving the conversation fails, the client history is used whole; ScopedAgentsPage puts visible rows into its own system prompt; with sessions off or a non-UUID agent, saved notices reach the model from the store. **This lane changes the main chat path for every owner: independent adversarial review is mandatory before merge.** |
| I release hygiene | `claude/agent-run-p2-i-release-hygiene-20261005` @ `2f61b223e0` (base `78de40e546`) | I1 shared migration-companion helper (`d508cc21ba`) done. I3 guide-setup cron test replaced under `tests/unit` (`ccab7b1412`) done — finding: box-ci runs only `tests/unit`, so none of the 60 files in `tests/api` run in CI. I4 marks browser script repaired and wired (`ab9f6739b5`) done. I2 release-profile phases HALF-done (WIP `f0077b91f7`). | I2: three Python test files still expect old counts; two suites have undiagnosed errors to check on the start commit first; it also added 160000 and 200000 to the profile so the before-merge phase matches the 16 installed packets — confirm. I5 release-state doc and I6 cron-route audit NOT started. |
| N1 status + switch | `claude/agent-run-p2-n1-status-switch-20261005` @ `4b0491ab99` (base `aff613db38`) | Non-allowlisted owners no longer get an Agent Run row or switch; readiness route + status card for allowlisted owners; tests pass incl. Chromium. Findings: every save of the Agent Run workflow through the normal path switches Agent Run off (migration `20261003020000` lines 139–142) and the owner was told nothing — the card now says so; `ensureAgentRunWorkflow` permanently switches Agent Run off if `AGENT_RUN_QUALIFIED_CONTRACT` changes or `SUPABASE_SERVICE_ROLE_KEY` is rotated (owner must flip the switch again) — operator caution; `tests/integration/agent-run-activation-browser.test.ts:34` is stale on base. | Mutation checks and type check NOT done (WIP). **PRIORITY: without N1, when #6168 goes live every non-listed owner sees an Agent Run switch that refuses them.** |
| N2 email readiness | `claude/agent-run-p2-n2-email-readiness-20261005` @ `cde911d3c9` | Investigation only (report committed), no code. Finding: for "unassigned" or "more than one" Email Agent assignment there is no screen where an owner can fix it. | Owner/product decision. |
| N3 live-check kit | `claude/agent-run-p2-n3-live-check-kit-20261005` @ `3cdaf52b98` | DONE and tested (72 tests incl. local PostgreSQL; 28 mutations): `scripts/qa/agent-run-live-check.mjs` read-only live check + `docs/agent-run/LIVE-CHECK.md`. Warning: with `OWNER_DB_URL` unset it reads the approved `.env.local` = production (read-only). | Type check not run. |
| N6 loose-ends view | `claude/agent-run-p2-n6-loose-ends-view-20261005` @ `817920309a` (WIP) | Read-only route done and tested (13 tests). | Screen component written but untested; no browser test, no mutation table. |
| N4 morning in Telegram · N5 routine quiet hours · N7 handoff card in web chat | not started, no branch pushed | Briefs in NEXT-WAVE-SCOPE.md §3. N5 needs owner decisions 3–5. | Everything. |
| Earlier lanes (history) | release blockers `claude/agent-run-release-blockers-20261005` @ `0662bfeca7` (merged into the PR); schema plan / flag-off review / phase-2 map (documents under `docs/agent-run/evidence/claude-takeover-20261005/`) | Done. | — |

### 6. Exact next steps, in order (a fresh session starts at step 0)

0. Sign in to GitHub; clone `jtobkin/suprafx-platform`; fetch the branches in §5 plus `codex/agent-run-execution-20260928` (this record) and `codex/agent-run-release-composition-20261004` (PR #6168 head). Read this section, `NEXT-WAVE-SCOPE.md` and the three review documents. Get the owner's allow rule `Bash(node scripts/apply-migration.mjs:*)` and the owner's read approval on the new computer.
1. Ask all peer sessions (if any exist on that computer; otherwise tell the owner to pause other windows) to hold merges. **Ask EVERY other session BEFORE the final re-merge and keep the hold until #6168 is merged** — seven sessions honoured it this time, and the PR still lost a green run to a one-minute race.
2. Merge current main into the PR branch (round 7: expect the catalog fixture `tests/fixtures/private-ai-recovery-writer-catalog.json` — three-way union, then `--add-uncataloged` → `--normalize` → `--check`, never hand-merge; check for new conflicts). Run the affected tests. Push fast-forward only. Reminders: any test that sets `AGENT_RUN_RUNTIME` to "on" must stub `AGENT_RUN_OWNER_ALLOWLIST`; tests that import the tool registry need `vi.mock("server-only", () => ({}))`.
3. Wait for both box-ci statuses (box-ci takes ~10 min of gates + ~30 min of build). Merge only via `scripts/ci/box-ci/merge-if-green.sh 6168`. Watch the deploy log for `live:`.
4. Install **Phase S** (3 packets) immediately, each proven; run the ledger readback (19 rows) — with `scripts/qa/agent-run-live-check.mjs` once N3 is merged, or the queries in RELEASE-MIGRATION-ORDER §3. Then tell the other sessions "merges open".
5. The five production click-throughs + the phone-call hotfix proof (NEXT-WAVE-SCOPE §5A), signed in, in a real browser.
6. Follow-up PRs in this order, each re-applied onto main, box-ci green, merge-if-green, then its live checks: **N1** (finish mutation checks first) → **batch 1** → **N3** → **G** (finish G2/G3, review) → **H** (review) → **I** (finish I2, I5, I6) → **N6** (finish) → **C** (only after a clean fourth security review; it installs nothing new — it uses packet 080000 from Phase S).
7. Then, with the owner: set `AGENT_RUN_RUNTIME=on`, `AGENT_RUN_QUALIFIED_CONTRACT=agent-run-20260928-v1`, `AGENT_RUN_OWNER_ALLOWLIST=<owner wallet>` on the web and cron containers (`TOPIC_ROUTING` is already on). The owner activates at `/vms/workspace?tab=system`. Run the NEXT-WAVE-SCOPE §5B checks.
8. Next wave N2, N4, N5, N7 with 3–4 parallel workers (the original workstation saturated at ~9 workers, load average 76 — keep to what the machine carries). Each lane: owned files, tests with mutation checks, **independent adversarial review BEFORE merge** (today every single lane had real defects found by its reviewer), live proof.
9. Keep the record and publish after each material step: edit `progress.json`/`plan.json`, run `python3 docs/agent-run/execution-dashboard/render.py`, `python3 docs/agent-run/render-plan.py`, `python3 docs/agent-run/render-public-handoff.py --update-private --output-dir ../agent-run-public-docs`; commit to the coordination branch; copy the four public files to `jtobkin/supraos-agent-completion-handoff`; verify the anonymous bytes.

### 7. What the owner must supply or decide

**Before production steps on the new computer:** the allow rule `Bash(node scripts/apply-migration.mjs:*)` (added by the owner via `/permissions`), and chat approval for production reads over ssh / read-only SQL.

**The 13 open owner decisions** (NEXT-WAVE-SCOPE §4; the coordinator's recommendation after the arrow):

1. Which wallets go on the Agent Run allowlist? → the owner's only.
2. Should owners not on the list see the Agent Run switch at all? → no, hide it (N1).
3. Should scheduled routines that message you wait until quiet hours end? → yes; allowlisted owners first; "Run now" never waits.
4. If the quiet-hours settings can't be read, should routines still send? → yes.
5. Allow a routine to be marked "may interrupt quiet hours"? → yes, off by default.
6. After you hand the computer back, should the agent carry on by itself? → no; you reply "continue".
7. Telegram stop notices and Allow-once reports go to every Telegram user, not only the allowlist? → yes (already chosen; confirm).
8. Who is the independent reviewer for the browser image? → name a second GitHub person (pictures, handoff and purchases wait on this).
9. Buy a Twilio number and a media host for shop calls now? → wait until chat and Telegram are proven.
10. Subscribe to Migadu and set DNS for mail.supraos.ai? → yes when ready; Revoke is permanent for that agent.
11. Real payments: Link test mode first, real money only after one reviewed test purchase? → yes.
12. Keep "exactly one Email Agent assignment" for email review? → keep it, and show it on screen (N2).
13. Friend sharing: the friend's notice carries none of the shared words (they read them on the Agent Channels page)? → keep this (security).

**Externals unchanged:** Stripe/Link, Migadu + DNS, image reviewer, Twilio/media host. Nothing to buy, no DNS change, no consumer test message without the owner's specific say-so.

### 8. Hosts and tools (access by normal sign-in only)

- **AWS production host:** user ubuntu; the `deploy-main.sh` cron deploys main every minute; the deploy log `deploy-main.log` in that user's home shows `live: <sha>`; `docker ps`. Access details are in the private engineering handoff (section "Data, evidence and host locations") and the owner's memory repo.
- **QA/build host cc-box:** runs box-ci (the `show` command and `journalctl -u box-ci`; paths in `scripts/ci/box-ci/README.md`). Its address is in the private engineering handoff and the owner's memory repo, never in public documents.
- **Migration tool:** `scripts/apply-migration.mjs` (reads `OWNER_DB_URL` from the environment or an approved `.env.local`); `node scripts/apply-migration.mjs --dir=supabase/migrations --name=<basename>`, one packet at a time; prove each in `pg_catalog` with the RELEASE-MIGRATION-ORDER §3 query — never trust the tool's own ✅.
- **Merge tool:** `scripts/ci/box-ci/merge-if-green.sh <PR>` only.
- **Node:** 22.23.2. Lanes on the original workstation borrowed one shared `node_modules` by symlink, in which `server-only`, `imapflow`, `mailparser`, `twilio`, `@stripe/link-sdk`, `valibot` and `viem` were missing; those local test failures were artefacts, and box-ci's `npm ci` is clean.

### 9. Prompt for the next session

> Resume the SupraOS Universal Agent project from the handoff section "PAUSED — October 5, 2026 ~08:45 UTC" (public copy: jtobkin/supraos-agent-completion-handoff; private copy: branch `codex/agent-run-execution-20260928` of jtobkin/suprafx-platform). You are on a new computer; assume no local memory, credentials or running agents. Sign in to GitHub normally; fetch the record branch, the PR #6168 head `codex/agent-run-release-composition-20261004`, and every lane branch in §5. Read §1–§9, `docs/agent-run/evidence/claude-resume-20261005/NEXT-WAVE-SCOPE.md` and the three review documents under `docs/agent-run/evidence/claude-takeover-20261005/`. Then do §6 in order: (0) ask the owner to add the allow rule `Bash(node scripts/apply-migration.mjs:*)` on this computer and to approve production reads; (1) ask every other session (or the owner, for other windows) to hold merges before the final re-merge, and keep the hold until #6168 is merged; (2) merge current main into the PR branch (round 7 — resolve the generated catalog fixture by three-way union then `--add-uncataloged` → `--normalize` → `--check`; check for new conflicts), run the affected tests, push fast-forward only; (3) wait for both box-ci statuses and merge only via `scripts/ci/box-ci/merge-if-green.sh 6168`, then watch the deploy log for `live:`; (4) install Phase S (`20260929010002` → `20260929080000` → `20261001000000`) immediately, each proven, run the 19-row ledger readback, then say "merges open"; (5) do the five production click-throughs and the phone-call hotfix proof, signed in, in a real browser; (6) ship the follow-up PRs in order N1 → batch 1 → N3 → G → H → I → N6 → C, each re-applied onto the new main as its own PR, box-ci green, merge-if-green, then its live checks — C only after a clean fourth security review; (7) with the owner, set the three Agent Run variables on the web and cron containers, let the owner activate, run the §5B checks; (8) run the next wave N2, N4, N5, N7 with 3–4 parallel workers; (9) keep the record. Standing rules: report implemented, tested, reviewed, merged, deployed, activated and live-verified separately; accepted stays 5/62 until a row is proven live; ask the owner only for purchases, DNS, consumer test messages, a shared deployment lock, the allow rule / production approvals, or a genuine product/security decision; never work around a permission denial; merge only via merge-if-green.sh; independent adversarial review before every merge; keep progress.json, plan.json and the handoff current with the three renderers and publish the four public files after each material step.

## RESUMED — October 5, 2026 ~05:05–07:30 UTC

*History: superseded by the "PAUSED — October 5, 2026 ~08:45 UTC" section above.*

**Read this section first. It supersedes the "PAUSED — October 5, 2026" section directly below, which stays as history.** Every fact here was verified first-hand by the coordinator (Claude Code). Implemented, tested, reviewed, merged, installed, deployed and live-verified are reported separately. **Accepted tasks remain 5/62.**

### 1. Owner instructions this session (given directly in chat to the coordinator)

- Resume the project end to end with parallel agents.
- "drive this project forward for the next 4 hrs".
- "automerge and automigrate as needed".
- The owner added the Claude Code allow rule `Bash(node scripts/apply-migration.mjs:*)`. This clears the permission blocker recorded in the PAUSED section §4.

### 2. PR #6168 — the candidate (NOT merged yet)

| Step | Result |
|---|---|
| Merge round 4 | `0283900b4b` (main `7a10b7a3fc`). Fixed a silent clash: the cloud chat runner now reports `warm_delta` for a resumed Codex thread. |
| Release-blockers lane finished and merged into the PR branch → `47e9cb2839` | Item 4 `2e66571f0b`, item 5 `bd3734e17d`, item 6 `0662bfeca7`: packets 010001/020000 made additive; new packet `20260929010002`; the duplicate-number ratchet skips `_PRECONDITION`; the guide-setup-followup cron is held to allowlisted owners. |
| box-ci failure 1 | 7 tests in agent-run-morning-routine failed (the test lacked the owner allowlist) → fixed `757049d372`. |
| Peer PR #6196 (W7) | Merged first, by agreement → main `55a12f0da9`. |
| Merge round 5 | `b890669566`: 26 conflict files resolved by hand; 5 hidden clashes fixed. |
| box-ci failure 2 | 2 W7 test files could not load `server-only`; 61,141 tests passed → fixed `78de40e546`. |
| Now | box-ci running at time of writing. **Not merged.** |

### 3. Production database — Phase A installed

All 16 Phase A packets were installed 06:13–06:25 UTC, each proven by a separate read-only catalog query:

`20260927190001`, `20260928190000`, `20260928230000`, `20260928231000`, `20260929000000`, `20260929010001`, `20260929020000`, `20260929030000`, `20260929040000`, `20260929050000`, `20260929060000`, `20260929160000`, `20260929200000`, `20261003010000`, `20261003020000`, `20261003021000`.

- Migration ledger 715 → 731 rows (the W7 peer had taken it 691 → 715).
- The old-site guard query returned true.
- The site is live on `55a12f0da` (main; the candidate is not deployed), health 200 (deploy log 06:24 UTC).
- **Phase S is NOT installed** (`20260929010002` → `20260929080000` → `20261001000000`). It waits for the new build to be live.
- The schema snapshot files refreshed by the migration tool are not committed anywhere yet.

### 4. Phase-2 lanes built today (none merged, none live)

Lanes A, B, C, D and E were each adversarially reviewed by an independent agent and fixed.

| Lane | Branch | Tip | State |
|---|---|---|---|
| A daily rhythm | `claude/agent-run-p2-a-daily-rhythm-20261005` | `90d977a916` | Built, reviewed, fixed. The routine quiet-hours item was **reverted** after review showed it would drop scheduled messages for all owners; it is now an owner decision. |
| B marks/recall | `claude/agent-run-p2-b-marks-recall-20261005` | `4843206b48` | Built, reviewed, fixed. |
| D mail | `claude/agent-run-p2-d-mail-20261005` | `c1ea39ce17` | Built, reviewed, fixed. |
| E computer/Telegram | `claude/agent-run-p2-e-computer-telegram-20261005` | `9825b037f0` | Built, reviewed, fixed. |
| Combined batch 1 | `claude/agent-run-p2-batch1-20261005` | `aff613db38` | A+B+D+E plus the email-chase Telegram notice held to allowlisted owners. Pushed. |
| C consent/friend-share | `claude/agent-run-p2-c-consent-tools-20261005` | — | Two security reviews found blockers: the approval card could differ from the sent text; the recipient was not bound; cross-owner text could reach the friend's model; invisible characters. Three fix rounds done; third review running. **NOT cleared to merge.** |
| G mark wiring + Telegram honesty | — | — | Started ~07:30 UTC. |
| H chat route items | — | — | Started ~07:30 UTC. |
| I release hygiene | — | — | Started ~07:30 UTC. |
| Scoping pass | — | — | Started ~07:30 UTC. |

Lane reports (private record only): `docs/agent-run/evidence/claude-resume-20261005/LANE-REPORT-<lane>.md` for merge-main, release-blockers, p2-a-daily-rhythm, p2-b-marks-recall, p2-c-consent-tools, p2-d-mail, p2-e-computer-telegram and p2-batch1.

### 5. Not verified / still owed

- Any browser check on production.
- The five production click-through checks (PAUSED §6 step 4).
- The phone-call hotfix live proof (PAUSED §6 step 5).
- A full type check outside CI.
- Phase S.
- Flags and owner allowlist: not set. The Agent Run runtime stays off.
- Accepted tasks: 5/62.

### 6. Open owner decisions

- Routine quiet-hours semantics (lane A).
- Friend-share notice content (lane C).
- Externals unchanged: Stripe/Link, Migadu + DNS, image reviewer, Twilio/media host.

### 7. Where the PAUSED §6 order stands

Step 0 (re-merge) and step 2 (Phase A with proofs) are done. Step 1: the release-blockers lane is reported finished (items 4–6 as listed in §2) and is merged into the PR branch; item 7 was report-only and its findings are in `LANE-REPORT-release-blockers.md`. Step 3 (both box-ci statuses green on the PR head, then `scripts/ci/box-ci/merge-if-green.sh 6168`) is in progress. Steps 4–8 remain as written.

## PAUSED — October 5, 2026 ~04:50 UTC: full handoff for a fresh session on a new computer

*History: superseded by the "PAUSED — October 5, 2026 ~08:45 UTC" and "RESUMED — October 5, 2026" sections above.*

**Read this section first; it supersedes every section below it.** The owner paused the Claude session at 04:46 UTC and asked for a complete handoff. Nothing is broken; the work is mid-flight and every artifact is pushed or listed here. A fresh session needs only normal GitHub sign-in (`gh auth login --hostname github.com --web`) with access to `jtobkin/suprafx-platform`, plus the two SSH hosts named below if it will operate production. **No secret is in this document.**

### 1. What is true right now (verified by the gatekeeper, not inferred)

| Item | State | How verified |
|---|---|---|
| Who runs the project | Claude (Fable 5.1, Claude Code) took over from Codex at the owner's request on 2026-10-05 ~02:30 UTC. Owner rulings that day, given directly in chat: production DB reads approved; the isolated native-VM rehearsal is Claude's call (decision: **skipped**); external accounts coordinated with the owner "when the time is right"; "drive this project end to end to completion … without me". | owner chat |
| Frozen candidate / PR | **PR #6168** head is now **`38fadb1fb19cdb7136866251af20836485c54871`** = frozen `a9ab52fe` + `origin/main 877f3d082e`, merged in three rounds (`cc3be125a4` → `fd2915726b` → `38fadb1fb1`). **Update after the pause was written:** box-ci finished on this head with **error — "the PR conflicts with main; merge main into it"** (no gate ran; the build was skipped). Main had moved to `7a10b7a3fc`; conflicting files now: Dockerfile.chat-runners app/api/agent-chat/stream/route.ts tests/unit/claude-warm-session-server.test.ts. So step 0 of §6 (one more hand merge round, then push) is required before anything else, and the merge pause with peer sessions should be requested first. | `gh pr view 6168`, cc-box `box-ci.mjs show` |
| Production code | `main 877f3d082e`; `deploy-main` cron deploys main every minute (~10 min build). Live container flags: `TOPIC_ROUTING=on`, `PRIVATE_AI_COMPUTER=1`, `PRIVATE_AI_BROWSER_COMPUTER=1`, `D3_OWNER_SCHEMA=1`; `AGENT_RUN_RUNTIME` and `AGENT_RUN_QUALIFIED_CONTRACT` **unset** → Agent Run runtime off. | `docker inspect supraos` on the AWS host |
| Production database | **None of the candidate's 29 forward packets is installed.** Ledger (`supabase_migrations.schema_migrations`) stores version numbers only; dated versions installed since 09-25 include `20260927190000`, `20260929010000`, `20260929153000`, `20261005010000`, `20261005030000` (none are the candidate's). `vms_hash_chain` ≈168k rows / 251 MB; migration user `postgres` (non-superuser); 0 `p2p_messages` with `channel='agent'`; 0 pending department promotions. | read-only SQL via `OWNER_DB_URL` |
| Shipped this session | **PR #6194 merged → main `66851e70cf`, LIVE** (`deploy-main.log: live: 66851e70c health 200`): `phone_call_dispatch` is now in `ALWAYS_APPROVAL` with its own card wording; a standing allow can never cover an always-approve tool. Found via the Phase-2 review; independent of the candidate. **Live proof still owed** (see §6). | `gh pr view 6194`, deploy log |
| Record | Private coordination branch `codex/agent-run-execution-20260928` at **`2cd6fd52a9`** (+ this commit); public handoff repo `jtobkin/supraos-agent-completion-handoff` at **`dd5c7d355ba8`** (+ this publication); anonymous raw bytes verified equal. | `git`, `curl` |
| Accepted tasks | **5/62 unchanged.** Nothing here is accepted on the strength of this plan. | plan.json |
| QA VM (Codex era) | unit `agent-cutoff-kvm-full-4b5dfe5f.service`, qemu PID 1444023 on cc-box, lease ends 08:18:58 UTC; left alone, not needed. | `ps` on cc-box |
| Backup plan 25418d44 | expired 05:56 UTC, never run, **not replayed**; the standalone-backup/operator path is abandoned for this release. | — |

### 2. The decision and why

Codex's critical path (isolated native-VM rehearsal → custom live release coordinator → faithful production restore) ran for a week and completed zero application phases. The platform already ships code and schema every day through `scripts/ci/box-ci/merge-if-green.sh` (our own checks on cc-box; **never** `gh pr merge --auto`) and the AWS `deploy-main.sh` minute cron, with migrations applied by hand through `scripts/apply-migration.mjs`. The candidate ships that way, **with the Agent Run flags off**, **schema first**. This is the owner-approved "decide and continue" posture, recorded in `docs/agent-run/plan.json → claudeTakeover20261005` and `progress.json → execution_strategy.owner_rulings_20261005`.

### 3. Three review documents a fresh session must read (copies committed under `docs/agent-run/evidence/claude-takeover-20261005/`)

- **`FLAG-OFF-REVIEW.md`** — the flags guard almost nothing. With flags off, the new build still: selects `vms_tool_grants.is_inherited` on **every tool dispatch** (`lib/mcp/tool-grants.ts:68`), reads the shelf on **every notification delivery** (`lib/notifications/dispatcher.ts:488`), calls the editor CAS when the **System workflows tab** loads (`app/api/system-workflows/route.ts:33`), and calls `_v2` embedding RPCs from a 15-minute cron (`lib/memory/pending-embedding-worker.ts:152`). Therefore Phase A must land **before** the container swap. Also: `160000` import-digest is needed by the digest panel/approval route/cron (install); `20261001000000` dept-memory is needed by the new build's promotion code but breaks the old build (switch packet); `guide-setup-followup` is a NEW 15-minute cron that reads an EXISTING table (`vms_onboarding_state` launch/completed) and would post to real owners on deploy; "Run saved Research" reads columns no migration creates (dead control).
- **`PHASE2-MAP.md`** — per-behaviour map of all 16 baselines with file:line, what blocks each, and six ranked lane briefs. Two flag-on blockers: **any signed-in user could activate Agent Run** (no owner check in `lib/agent-run/activation.ts`, `runtime.ts`, routes) and **Research V1 workflows are refused** by `lib/vms/coordination/trigger.ts:205-243` when the flags are on. Workflows never run Agent Run (`system-workflow-engine.ts:386-389`): "on" means chat + Telegram only.
- **`RELEASE-MIGRATION-ORDER-20261005.md`** — all 29 packets classified, dependencies, exact `apply-migration.mjs` commands with one read-only proof query each, rollback notes, and a full scratch rehearsal (29/29 applied + verified on a local PostgreSQL 17 baseline). Duplicate-number ratchet fails on the three `_PRECONDITION` files (fix in the blockers lane).

### 4. Final migration plan (gatekeeper decision; amend only with a stated reason)

- **Phase A — before merging, old build keeps working (16):** `20260927190001` shelf · `20260928190000` tool grants · `20260928230000` mailbox ingress · `20260928231000` shelf-history index (seconds-long write lock on `vms_hash_chain`) · `20260929000000` takeover revocation · `20260929010001` email review choice history **(edited: legacy REVOKE removed)** · `20260929020000` email draft proposals **(VERIFY edited)** · `20260929030000` migadu · `20260929040000` purchase lifecycle · `20260929050000` link wallet oauth · `20260929060000` purchase worker · `20260929160000` import digest · `20260929200000` embedding v2 · `20261003010000` headless result · `20261003020000` editor CAS · `20261003021000` activation CAS.
- **Phase S — within minutes after `live:` shows the new build (3), in order:** `20260929010002` **(new, in the blockers lane: REVOKE legacy `mutate_email_chaser_review`)** → `20260929080000` friend send atomic → `20261001000000` department memory promotion atomic.
- **Skip this release (12):** `070000` iMessage · `090000`/`100000` runner-release bootstrap (no caller) · `110000`–`150000` global attention (cutover stays 0) · `170000`/`180000`/`190000` (held digest/reminder work).
- **How:** from a checkout containing the edited files, `node scripts/apply-migration.mjs --dir=supabase/migrations --name=<basename>` one at a time; prove each in `pg_catalog` with the query in RELEASE-MIGRATION-ORDER §3 — never trust the tool's own ✅ (it once recorded a rolled-back migration). Run the "old-site guard" query from §3 after Phase A. Known trap: ROLLBACK scripts leave the ledger row behind.
- **Blocker met this session:** the Claude Code auto-mode permission layer classified `node scripts/apply-migration.mjs` against production as *Production Deploy* and denied it (also denied writing an apply script and removing stale restore scratch containers on the host). **The owner must either add a Bash allow rule for `node scripts/apply-migration.mjs*` (Claude Code `/permissions`) or run the Phase A commands personally.** No workaround was attempted.

### 5. Lanes, branches, worktrees (all on the original workstation under a private workstation or host path (see engineering handoff), briefs in a private workstation or host path (see engineering handoff); everything that matters is pushed or copied into this repo)

| Lane | Branch / location | State |
|---|---|---|
| merge-main | `claude/agent-run-release-merge-main-20261005` → pushed as PR #6168 head `38fadb1fb1`. Worktree a private workstation or host path (see engineering handoff). | DONE (3 rounds). Reviewed semantic fix in `app/api/agent-chat/stream/route.ts` (~line 976): legacy `/vms/chats` threads are exempt from the receipt-callback check only. Test fixes: subscription harness flag rename, readiness mock, chat-route-wiring, backup-request body, tool-approval-resume stand-in. **Not verified:** full typecheck vs main (OOM locally), Docker DB path, browser. One pre-existing failing test on the frozen candidate: chat-route-wiring "sanitizes the continuity block". Lane report: `docs/agent-run/evidence/claude-takeover-20261005/LANE-REPORT-merge-main.md`. |
| release-blockers | `claude/agent-run-release-blockers-20261005` from `cc3be125a4`. Worktree a private workstation or host path (see engineering handoff). **Pushed at pause** (see commit list in its LANE-REPORT). | **Pushed; head `6773c4d5dc`.** Committed: B1 owner allowlist `AGENT_RUN_OWNER_ALLOWLIST` (`4df7948e00`; helper `lib/agent-run/owner-allowlist.ts`; unset → everyone refused; also checked at run time and shown as "unavailable" in the setup panel), B2 Research V1 legacy fallback (`c057a76333`; probe `lib/vms/coordination/research-original-ledger-probe.ts`), item 3 hide dead Research panel + 409 before select (`6773c4d5dc`; Chromium test at 390/1440). 17 mutation checks all red-then-green. **Not started:** 4 (010001/020000 edits + new 010002 packet), 5 (`_PRECONDITION` ratchet), 6 (guide-setup-followup allowlist — matters before the new container deploys), 7 (other unflagged crons). Report: `docs/agent-run/evidence/claude-takeover-20261005/LANE-REPORT-release-blockers.md`. **Must be merged into the PR branch (or stacked as its own PR after #6168) before the flags are turned on; items 4–5 are needed before Phase A/merge.** |
| schema-plan / flag-off-review / phase2-map | read-only lanes, DONE; outputs copied into `docs/agent-run/evidence/claude-takeover-20261005/`. Worktrees a private workstation or host path (see engineering handoff), a private workstation or host path (see engineering handoff) can be removed by their owner once the copies are confirmed. | DONE |
| phone-call hotfix | PR #6194 MERGED, live; lane folder removed. | DONE, live proof owed |
| docs | a private workstation or host path (see engineering handoff) on the coordination branch; this document. | this commit |

Peer sessions on the same Mac were merging to main several times per hour; a 7,000-file PR re-conflicts on every main move. **Before the final push + merge of #6168, ask the other sessions to hold merges for ~90 minutes** (done once at ~06:20 local; re-ask when resuming).

### 6. Exact next steps, in order (a fresh session starts at step 0)

0. Sign in; clone/fetch; read §1–§5 and the three review docs; `gh pr view 6168`; `git fetch origin main` and `git merge-tree --write-tree --name-only origin/main <PR head>` — if it conflicts, do one more merge round (same rules as the merge lane: by hand, per file, regenerate generated files with their scripts, catalog via `--add-uncataloged → --normalize → --check`, re-pin skill citations with `repin-skill-citations.mjs --write`), push to `codex/agent-run-release-composition-20261004` (fast-forward only, never force).
1. Finish the release-blockers lane (items 3–7), merge its branch into the PR branch, push. Confirm `node scripts/checks/duplicate-migration-numbers.mjs` passes.
2. Install **Phase A** on production (owner allow rule or owner-run). Prove each packet; run the old-site guard query.
3. Wait for both `box-ci/*` statuses = success on the PR head; `scripts/ci/box-ci/merge-if-green.sh 6168`. Watch a private workstation or host path (see engineering handoff) on the AWS host for `live: <sha>`.
4. Immediately install **Phase S** (3 packets). Then click through on production: a tool call in chat, a notification, the System workflows tab, an email-review save, `/vms/chats` reply. Run the ledger readback (expect 19 new rows).
5. Prove the phone-call hotfix live: with Proactive autonomy ask the agent to place a call → approval card "This places a real phone call…"; nothing dials until Approve; decline it. (A chat turn asking the CEO agent to call +1 500 555 0001 was left "Waiting for your desktop AI…" at pause — the owner's chat routes to the desktop runner; retry when it is up, or use an agent on the cloud path.)
6. Flag-on for the owner only: set `AGENT_RUN_RUNTIME=on`, `AGENT_RUN_QUALIFIED_CONTRACT=agent-run-20260928-v1`, `AGENT_RUN_OWNER_ALLOWLIST=<owner wallet>` on the AWS `supraos` and `supraos-cron` containers (`TOPIC_ROUTING` is already on); the owner activates at `/vms/workspace?tab=system`; readiness row shows `active`; first Telegram reply carries a mark footer.
7. Phase 2: start the ranked lanes from `PHASE2-MAP.md` §2 (B done partly; then A daily rhythm, C consent/tools, D mail, E computer/Telegram, F payment). Each lane: owned files, tests + mutation checks, prove live, then merge via box-ci.
8. Keep the record: edit `progress.json`/`plan.json`, run `python3 docs/agent-run/execution-dashboard/render.py`, `render-plan.py`, `render-public-handoff.py --update-private --output-dir ../agent-run-public-docs`; commit to the coordination branch; copy the four public files to `jtobkin/supraos-agent-completion-handoff`; verify anonymous bytes.

### 7. What the owner must supply, when asked (not now)

Stripe/Link credentials and approved client configuration (purchases, P02); Migadu subscription + DNS for `mail.supraos.ai` (agent mailbox, P03); an independent human reviewer for the private-computer browser image (P04); the Claude Code allow rule above (or run Phase A personally). Nothing to buy, no DNS change, no consumer test message without the owner's specific say-so.

### 8. Hosts and tools (access by normal sign-in only)

AWS production host `ssh supraos` (user ubuntu; `deploy-main.sh` cron, `docker ps`, a private workstation or host path (see engineering handoff)); QA/build host cc-box as root (address in the private engineering handoff and the owner's memory repo; never in public documents) (cc-box: the box-ci `show` command and `journalctl -u box-ci`; paths in `scripts/ci/box-ci/README.md`); migration tool `scripts/apply-migration.mjs` (reads `OWNER_DB_URL` from env or an approved `.env.local`); Node 22.23.2 (on the original Mac at a private workstation or host path (see engineering handoff), no `nvm.sh`); lanes borrow a private workstation or host path (see engineering handoff) by symlink — `@stripe/link-sdk`, `imapflow`, `mailparser`, `twilio`, `server-only` are missing there (candidate-only dependencies), so one changed-types error and a few test failures are local artefacts; box-ci's `npm ci` is clean.

### 9. Prompt for the next session

> Resume the SupraOS Universal Agent project from the public handoff (jtobkin/supraos-agent-completion-handoff, section "PAUSED — October 5, 2026"). You are on a new computer; assume no local memory, credentials or running agents. Sign in to GitHub normally; fetch `codex/agent-run-execution-20260928` (record), `codex/agent-run-release-composition-20261004` (PR #6168 head), `claude/agent-run-release-blockers-20261005` (fix lane). Read §1–§9 and the three review documents under `docs/agent-run/evidence/claude-takeover-20261005/`. Then: verify PR #6168 still merges onto current main (one more hand merge round if not); finish the release-blockers lane (hide the dead Research panel, split the 010001 REVOKE into packet 20260929010002 and edit the 020000 VERIFY, make the duplicate-number ratchet skip `_PRECONDITION`, limit guide-setup-followup to allowlisted owners) and merge it into the PR branch; ask peer sessions to hold merges; install Phase A (16 packets) on production with proofs — if the permission layer denies it, stop and ask the owner for the allow rule rather than working around it; merge #6168 only through `scripts/ci/box-ci/merge-if-green.sh` when both box-ci statuses are green; install Phase S right after `live:`; click through the five production checks; prove the phone-call hotfix live; then set the three runtime variables plus the owner allowlist and let the owner activate; then run the Phase-2 lanes from PHASE2-MAP.md with 3–4 parallel Opus workers, each with owned files, tests with mutation checks and a live proof. Keep progress.json/plan.json/handoff current with the renderers and publish the four public files after each material step. Report implemented, tested, reviewed, merged, deployed, activated and live-verified separately; accepted stays 5/62 until a row is proven live. Ask the owner only for: purchases, DNS, consumer test messages, a shared deployment lock, the allow rule, or a genuine product/security decision.

## Current checkpoint — October 5, 2026: Claude takeover and the normal release path

**Supersedes the pause section below (kept as history).** At the owner's request Claude (Fable 5.1, Claude Code) took over coordination from Codex at about 02:30 UTC. The owner ruled in that session: production database reads are approved; the isolated native-VM rehearsal is Claude's call; external accounts (Stripe/Link credentials, Migadu mailbox and DNS, an independent browser-image reviewer) are coordinated with the owner when the time is right; and "drive this project end to end to completion … without me".

**Decision.** The isolated native-VM rehearsal, the custom live release coordinator and the standalone backup plan (25418d44, expired 05:56 UTC, never run) are **skipped for this release**. The frozen candidate ships through the platform's normal path: merge current `main` into it, install the additive database packets first, merge PR 6168 through `scripts/ci/box-ci/merge-if-green.sh`, let the AWS `deploy-main.sh` cron deploy it with the Agent Run flags off, then install the three switch packets, then fix the flag-on blockers, then activate for allowlisted owners. Accepted tasks remain **5/62**; nothing below is accepted on the strength of this plan.

**Verified state (gatekeeper, ~02:45–03:40 UTC).** PR 6168 (`a9ab52fe`) is open, both box-ci statuses success (Oct 4), and it conflicts with `main` in eight small files. The production migration ledger contains none of the candidate's 29 forward packets. Live container flags: `TOPIC_ROUTING=on`, `PRIVATE_AI_COMPUTER=1`, `PRIVATE_AI_BROWSER_COMPUTER=1`, `D3_OWNER_SCHEMA=1`; `AGENT_RUN_RUNTIME` and `AGENT_RUN_QUALIFIED_CONTRACT` unset, so the runtime is off. The QA VM (`agent-cutoff-kvm-full-4b5dfe5f`) was still running at 02:25 UTC under its lease ending 08:18:58 UTC and is left alone. No production write has happened in this session.

**Findings from three review lanes (files under the gatekeeper's lanes; summarised in `docs/agent-run/RELEASE-MIGRATION-ORDER-20261005.md`).**
- The flags guard almost nothing: every tool dispatch selects `vms_tool_grants.is_inherited`, every notification delivery reads the shelf, the System workflows tab calls the editor CAS, and a 15-minute cron calls the `_v2` embedding functions. So **Phase A (16 packets) must be installed before the new container starts**: 190001, 190000, 230000, 231000 (brief index lock on `vms_hash_chain`), 000000, 010001 (edited: legacy REVOKE removed), 020000 (VERIFY edited), 030000, 040000, 050000, 060000, 160000, 200000, 20261003010000, 20261003020000, 20261003021000. **Phase S right after `live:`**: new 20260929010002 (the REVOKE) → 080000 → 20261001000000. **Skipped**: 070000, 090000, 100000, 110000–150000, 170000–190000.
- Before the flags go on: any signed-in user could activate Agent Run (no owner check) → owner allowlist; Research V1 workflows would be refused → legacy fallback; the "Run saved Research" panel reads schema no migration creates → hidden; the duplicate-number ratchet fails on `_PRECONDITION` files → fixed; the new `guide-setup-followup` cron would post to all enrolled owners → limited to allowlisted owners.
- A live safety gap on `main` unrelated to the candidate: `phone_call_dispatch` is not in `ALWAYS_APPROVAL`, so proactive autonomy could dial without approval → hotfix PR on `main`.

**Blocker.** The Claude Code permission layer denied applying migrations to production from the gatekeeper session (and removing stale restore scratch on the host). The owner has been asked to add an allow rule for `node scripts/apply-migration.mjs*`; until then no packet is installed.

**Lanes.** merge-main (in progress), schema-plan (done), flag-off-review (done), phase2-map (done), phone-call hotfix on main (in progress), release-blockers (queued behind the merge), docs (this checkpoint).

## Current owner-requested pause — October 5, 2026

**The owner ended the active run early and requested this fresh-session handoff. Implementation is paused.** The earlier authorization through08:53:11UTC is superseded by this pause; it is not authority for background work to continue. Only reconciliation, owned test-runtime shutdown, evidence preservation and document publication continued during closeout. The final runtime record below must be read before any new execution.

**Full Agent Run remains unshipped and inactive. Accepted:5/62 (8.1%); pending:56/62 (90.3%); deliberately dropped:1/62 (1.6%).** These are acceptance counts, not an estimate of code completion or remaining effort. The32 delivery packages below organize the same62 tasks; they are not additional tasks. None was promoted on the strength of this window's infrastructure or helper tests.

### Shutdown status at publication — VM cleanup remains pending

The submitted native-daemon stop returned **STOPPED_ONLY**, receipt `ac5bae2bc77f79690d2e12328ac9ed647949f4f3ab0701222c39e9906fe0780d`: inactive/not-found unit, PID0, zero containers, unchanged default daemon and firewall. Independent post-stop audit `3fbf290bbf74964cb4f9d9876811b268e61034242c8012cf59b462ef62755668` **passed**: the native processes, socket, runtime directory and cgroup are absent; default daemon and firewall are unchanged. All workers are now paused. **The isolated VM stop was not submitted; VM c remains running under its finite lease ending2026-10-05 08:18:58UTC.** The owner required immediate pause/publication, so no further VM preparation or new effects were admitted. All implementation and qualification are paused. The private [final runtime state](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/evidence/resume-isolation-20261005/owner-pause/FINAL-RUNTIME-STATE.json) records this remaining cleanup explicitly. A new session must inspect actual state and original receipts, never replay the completed native stop. Lease expiry alone is not independently verified shutdown.

### Start here from any computer

- [Public plan and full checklist](https://github.com/jtobkin/supraos-agent-completion-handoff/blob/main/SupraOS-Agent-Plan-Checklist.md): all original tasks,32-package dependency graph, acceptance criteria, source paths and evidence stages.
- [Standing execution procedure](https://github.com/jtobkin/supraos-agent-completion-handoff/blob/main/Faster-Verified-SupraOS-Delivery.md): the five mandatory improvements, parallel-lane contracts, reuse rules and completion gates.
- Private repository: `jtobkin/suprafx-platform`, canonical coordination branch `codex/agent-run-execution-20260928`. This branch contains the engineering plan/evidence; it is not automatically the deployable application source.
- Frozen application: `codex/agent-run-release-composition-20261004`, commit `a9ab52fe956e134b667d414a5b47f58cc5741e6b`, [PR6168](https://github.com/jtobkin/suprafx-platform/pull/6168). Auto-merge is held. At02:04:48UTC the PR remained open/unmerged with both managed contexts successful; main was `f8203066e3de86733ee5d8eaab071fbb2259ee70` and mergeability was unknown. Verify current GitHub state before acting.
- [Current private pause inventory](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/evidence/resume-isolation-20261005/owner-pause/README.md): preserved controls, actual receipts, independent reviews, final shutdown state, runtime identities and host/data locations. Public documents grant no private repository or host access.

A fresh session must use normal GitHub/host sign-in, inspect existing Git status/process ownership, fetch the explicit source and evidence branches, then read `AGENTS.md`, `CONTEXT.md` and required boot documents. Follow the full bootstrap section below. Do not reset an existing checkout, assume local memory exists, infer credentials from historical instructions, or ask for secrets in chat.

### Goal and what “finished” means

Every supported SupraOS agent path—chatbox, Telegram, background jobs, delegation and System Workflows—must use one shared behavior contract. Orchestration loads current scoped preferences and bounded relevant memory, skills and lessons. Tools check fresh permission before effects and record truthful durable outcomes. Preference changes append before/after history to the hash chain before updating active state, and the next turn reads the latest saved value. Telegram is a communication transport, not a separate behavior implementation.

The complete scope also includes resumable owner-specific onboarding; independently proven readiness for each capability; main-admin authorization for initial Guide rollout; all16 original baseline behaviors; authorized real provider journeys; qualified schema/application deployment; controlled activation; independent live browser/transport verification; monitoring and tested recovery. A preference is never permission. A configured secret, saved mailbox label or simulated purchase is never proof of capability readiness. iMessage is deferred. The project is finished only when this entire agreed behavior is deployed, activated where required and verified live with recovery evidence.

### What was already shipped

The narrow friend-channel security repair and installed QA disk-admission scheduler have retained shipped evidence. The full Agent Run candidate has not shipped. Unrelated main-branch deployments must not be counted as this project's deployment. The detailed historical shipping section and source-specific evidence remain below.

### What this execution window actually advanced

1. **The execution strategy is now part of the maintained artifacts.** The handoff, generated checklist/dashboard and standalone procedure preserve resumable qualification, early complete-path rehearsal, three delivery-focused lanes, canonical machine-readable state and early precise approval requests. All62 original task records and32 package acceptance/dependency records were preserved. Future sessions must retain these rules when regenerating views.
2. **Fresh isolated native prerequisites ran and received independent evidence checks.** The copied-disk resume path reached a new VM and private daemon generation; exact source/image reuse, network creation, five image loads, base tags, common module and side-effect-free probe build were verified. The first fresh VM's firewall-drift refusal was preserved and its shutdown independently checked. These are QA prerequisites, not product acceptance.
3. **The next application transition was concretely prepared.** The first Traefik packet pair and expected inner packet were independently hash-checked. Existing reviewed source-stage reuse avoids rewriting identical source for each phase while retaining per-phase packets, current identity checks and actual receipt gates. The expected packet is not an actual success receipt. See the final runtime record for the last submitted effect.
4. **Database/operator/recovery integration was made ready for the next transition.** The checked-file-descriptor seed bridge, PG packet/successor producers, read-only REST-close preparation and runner controls were preserved. The successor's900-second source-stage budget is derived from unchanged real subcommand bounds. Operator lifecycle, retained terminal observation, final-acknowledgement recovery, competing-operation proof and failure cleanup were reviewed;36 focused local tests passed. No PG, native caller or operator cutoff effect was submitted by that lane. Fixture/common input staging did occur and is separately recorded.
5. **A fresh production backup plan was captured and read back.** Attempt `25418d44-a966-4fb3-953d-5a523b8e7924`, plan SHA `5ff14ca184da88c58daf300ce49a7b8e3cf381d90b6e2bac646055eb22c58ca4`, expires **2026-10-05 05:56:29UTC**. Capture only ran: no shared lock, backup/restore run, migration or activation. The held launcher and exact plan are preserved; completed Grok source review is PASS_WITH_SCOPE with independently recomputed root hashes, and fresh specific owner approval remains required. Expiry or changed inputs require a fresh capture, not replay or extension of this plan.
6. **The dependency classification was corrected.** Standalone backup preparation does not consume Supabase management-policy readback and can advance independently. Full-release continuous writer exclusion still requires the actual writer policy/coverage and held-writer evidence. Production free space exceeded the unchanged85GiB floor at the recorded observations, but it is not reserved; do not repeat volume expansion based on older low-disk snapshots.
7. **The checklist artifact was exercised in real Chromium.** Mobile390px and desktop1440px checks passed for62 ledger rows,32 cards, search/filter, task dialog, dependency navigation, the standing strategy and absence of page overflow/errors. This validates the project tracker, not the product's missing live acceptance.

### Frozen source and evidence ownership

| Asset | Exact source / where it belongs | How to use it |
|---|---|---|
| Application | `a9ab52fe956e134b667d414a5b47f58cc5741e6b`, release-composition branch / PR6168 | Retain managed security51-step and production-build7-step evidence,59,870 unit passes/zero failures/252 skips,PG2/2,Chromium45/45 with their recorded merge inputs. Do not transfer passes to changed source implicitly. |
| Native application/assembler | `2ff4ddb18d852ad423f6094c1149e4a03097412b`, `feat/agent-run-full-native-guest-20261005` | Existing real app/native assembler, probe and caller sources; verify a fresh generation after stop. |
| Native controller/operator | `0a4c7ba248cee6143661450a36969746656cdc8a`, `feat/agent-run-isolated-native-guest-smoke-20261005` | Existing controller/descriptor/prepare/install tools; source readiness is not runtime acceptance. |
| Portable tooling/donors | `85fa0401f1288a5e8527d087ed6a312d3453b3fc`, `evidence/native-guest-tooling-20261005` | Preserve signed/offline tool and image provenance; large private disks/archives are host-resident, not copied by Git. |
| Copied-disk resume/source-input templates | `19ba233523c302f0bfe7b022b6605abf2e1916de`, `codex/native-resume-delivery-20261005` | Pushed;6 resume and7 input tests pass. Reuse reviewed templates and rebind current identities; actual bound controls are preserved separately. |
| Operator lifecycle/recovery additions | `4a2ec5a20d81cf90b871f07b2c7f993ca98c3282`, `evidence/native-operator-sequence-20261005` | Pushed, clean isolated lane;36 tests and exact-source audits. Its actual caller, contention and recovery effects remain unrun. |
| Current bound controls / reviews | Current canonical branch, `docs/agent-run/evidence/resume-isolation-20261005/owner-pause/` | Historical one-use packets and runnable source references. Rebind fresh identities and requalify actual prerequisites; never blindly execute captured packets. |
| Backup capture | `docs/agent-run/evidence/resume-isolation-20261005/backup-capture-25418d44/` | Exact plan, readbacks and held launch source. Capture success is not restore success or permission to run. |

The code map below names the production callers for preferences, memory, System Workflows, chat/Telegram, onboarding, attention, outcome handling, migrations and tests. Every package also retains its exact source list and acceptance criteria. Read those sections before opening another implementation lane.

### Next five tasks after an explicit resume

1. **Inspect the final pause inventory, current GitHub/host state and available window.** Reuse verified donor bytes and existing resume adapter; allocate new runtime identities after stop. Reserve unchanged execution/transport/owned-child termination bounds plus independent reconciliation and shutdown. Preserve prior UNKNOWN/refused operations and never replay them.
2. **Finish the real native app → database path.** Complete the five app/proxy phases using actual independently checked receipts, then PG start → baseline → bootstrap → PostgREST. Use the existing seed bridge and producers; prepare/install the operator before starting its runner. Source review and expected packets do not satisfy runtime gates.
3. **Complete operator/cutoff/recovery qualification.** Mount the existing operator, idle QA companions and runner; prove continuous admission/drain, the actual seven-step cutoff, original-attempt final-acknowledgement readback and failure cleanup. The competing-operation test still has a timing risk: its receipt binding is only available after launch. Pre-stage permitted static source/fields or narrowly review a pre-armed contender if necessary; never slow or sabotage the baseline, and report a missed overlap as unproven. Final-ACK recovery does not establish every mid-effect lost-ACK case.
4. **Advance faithful production restore in parallel.** Refresh plan validity, free-space/memory and exact source/container identities. Obtain the concrete plan's specific shared deployment-lock approval (up to127minutes held plus30minutes waiting; sites remain online). Run once, reconcile the original attempt, prove rows/ledger/roles/catalog fidelity. Full release additionally needs current writer authority and continuous exclusion; a standalone restore does not replace that gate.
5. **Join qualification, then ship the full scope.** Complete V01/L00/L10/L12/V00/L11 and final source/policy provenance; qualified merge and inactive AWS deployment; all remaining R/S/N/G/D/H/P integration and V02 acceptance; authorized providers; controlled activation; independent live verification of every supported path/all16 baselines, monitoring and recovery; final L05 reconciliation. No milestone narrows the goal.

### How the next session should staff the path

Use one coordinator and up to three workers with distinct files/runtime ownership: native/app/DB caller integration; release prerequisites plus operator/recovery integration; independent exact-source and real-outcome verification. Name one owner for each runtime, source file and acceptance gate. Transfer ownership explicitly instead of leaving ready work idle. Use additional bounded Grok reviews only when they directly unblock this path; record the actual model and terminal result. Sol capacity was unavailable in this window, so replacement Codex reviews are not called Sol reviews. A cancelled or cutoff audit is not approval.

Freeze the candidate and admit only demonstrated blocker fixes. Reuse unaffected evidence, but independently check actual receipts and failed/uncertain outcomes. Maintain concise changes in canonical JSON and generate views; reserve detailed narrative updates for a transition, material blocker or owner-requested handoff. Do not rebuild helpers, stores, donor archives or provider proposals that already exist.

The current pause record supersedes older “next” instructions below. Historical sections preserve provenance; their then-active processes, old disk shortage, missing-adapter claims and approvals are not current authority.

<!-- BEGIN STANDING EXECUTION POLICY -->
## Faster Verified SupraOS Delivery

### Standing execution contract

Owner-mandated revision, October 5, 2026. This procedure is part of every Agent Run plan, checklist and handoff, not optional advice. Future sessions must preserve it when regenerating documents. It governs execution order without changing the 62 original tasks, 32 delivery packages, 16 baseline behaviors or their acceptance criteria. It does not resume paused implementation or grant new production, shared-lock, purchase, DNS or consumer-message authority.

Use the latest execution_state, release and task-count fields for current status. This documentation revision does not resume implementation. Acceptance counts are not effort estimates. The owner's requested conversational estimate of roughly65% implementation/preparation was subjective: do not convert it into measured progress, task acceptance or a delivery-date promise.

The outcome remains one shared SupraOS agent contract across chatbox, Telegram, delegation, background work and System Workflows: current scoped preferences, bounded relevant memory/skills/lessons, permission before effects, truthful durable outcomes, history before active state, next-turn readback, resumable onboarding and independent capability readiness. Telegram is a transport. All16 baselines, main-admin initial Guide authorization, monitored deployment, activation and tested recovery remain required. iMessage stays deferred.

### First resume milestone

**Complete an independently verified native application/database/operator/recovery rehearsal.** Do not substitute another collection of helper tests for this milestone. The native rehearsal uses a side-effect-free release probe; it is not full application/provider acceptance and cannot close the project.

The immediate dependency path is: inspect preserved state → qualify a fresh-generation resume adapter → five app/proxy phases → PostgreSQL baseline/bootstrap/PostgREST → real operator/runner admission and cutoff → lost-acknowledgement, competing-operation and recovery tests → independent terminal review. Production capacity, writer authority and faithful restore advance alongside this chain. Joined release qualification waits for both paths.

### Five mandatory execution techniques

1. **Reuse a resumable qualification environment.** Reuse the reviewed copied-disk resume adapter; bind preserved disk/source hashes and independent stop evidence to fresh VM/native identities. Repair it only for a demonstrated gap. Verify actual readiness before using it. Do not rebuild or retransfer verified unchanged donors by default. Stopped-generation receipts are historical evidence, never live authority. Never restart a spent unit or replay an uncertain effect.
2. **Run the complete qualification path early.** Before unrelated polishing, attempt the earliest complete transition whose prerequisites are satisfied. Budget setup, full existing execution bounds, independent observation, failure recovery, shutdown and publication. Before each effect, require its complete execution/transport/owned-child termination bound plus independently checked recovery and shutdown reserves to fit the current operation, parent environment and owner deadlines. Do not confuse this safety admission with a guarantee that every future phase will consume its maximum timeout and still finish in the same session. Record a decision deadline; do not spend the whole window on preparations and discover too late that the real test cannot fit. Do not shorten tests, timeouts or safety checks to fit.
3. **Give parallel lanes completion targets on the same path.** Staff integration, release prerequisites and independent verification. Each lane closes a specific dependency with named evidence. Additional workers are justified only by a nonconflicting task directly unblocking that path. Do not maximize worker count or open unrelated improvements.
4. **Maintain one canonical record and generate its views.** Record concise state/decision/evidence changes when they occur. Generate the checklist and dashboard from canonical JSON, and embed this standing procedure in plans and handoffs. Write the detailed narrative once per completed transition, material blocker, explicit owner request or pause. Do not repeatedly rewrite chronology or rerun expensive application checks for documentation-only changes.
5. **Escalate delivery blockers early and precisely.** Classify missing code, evidence, access and approval separately. Prepare the exact action, target, source/plan hash, duration, impact, recovery and required authorization before asking. Existing approvals remain valid only within their actual scope; time passing is not approval. Continue independent work on this path while waiting; do not replace the blocker with unrelated coding.

### Resume and qualification schedule

These rounds prioritize execution; they add no new acceptance tasks and remove no existing DAG dependency. Independent drafting may begin before a round, but effects and completion must satisfy their actual prerequisites. The generated package DAG remains authoritative for integration edges.

| Round | Work and owner | Required exit proof |
|---|---|---|
| 0 — establish current facts | Root inspects Git/worktrees/process ownership, frozen source, last terminal receipts, access and current blockers. Assign bounded lanes before edits. | Exact candidate and donor inventory; no duplicated running job; named next transition and acceptance command; full-window budget. |
| 1A — resume and exercise native path | Integration lane, with root composing real callers. Recover preserved guest under a fresh identity; use the existing app/PG/operator/runner sources. | Five app/proxy phases and actual DB/operator/recovery transition independently pass, or a precisely scoped defect/unknown is preserved. Foundation-only success does not close the round. |
| 1B — close production prerequisites, parallel with1A | Release lane plus root for external authority. Refresh capacity, installed ledger/roles and actual writer-policy coverage; qualify faithful restore. | Capacity floor met with authority; all relevant writers covered; fresh reviewed backup plan and its valid shared-lock approval; data/ledger/roles/catalog fidelity. |
| 1C — independent review, parallel with1A/1B | Reviewer inspects exact source and actual terminal evidence; checks failure/cancel/retry/unknown outcomes. | Findings resolved on named source; no inferred pass from helper tests, timeout, stopped worker or unavailable model. |
| 2 — join inactive-release qualification | Root joins V01/L00/L10/L12/V00/L11 and applicable release policy. | Coherent candidate, exact phased schema profile, continuous exclusion and faithful recovery qualify together. Required gates remain intact. |
| 3 — deploy inactive; finish remaining integration | Root owns L01. Existing R/S/N/G/D/H/P package work proceeds only where it directly closes release or acceptance gaps. | Qualified merge and actual AWS image/source/schema/health match. Unqualified behavior remains inactive. Finish V02 full local acceptance; inactive deployment alone is not completion. |
| 4 — providers, activation and live acceptance | L02 → L03 → L04, preserving P01–P05 and V02 dependencies. | Specifically authorized provider journeys, all16 baselines and all supported paths work live; pause/revoke, uncertainty, monitoring and recovery proven. |
| 5 — close the complete scope | Root and independent reviewer reconcile L05/original L4. | Every required acceptance row has matching deployed source and evidence; operating handoff is complete; no required gap remains. |

### Lane contracts and limits

Root owns integration, the frozen candidate, external requests, priorities and final release decisions. Use up to three workers with distinct files/worktrees:

| Lane | Completion target | What it must not become |
|---|---|---|
| Integration | Close L10 native rehearsal and actual L12 operator/runner callers; then the next release-blocking integration. | More unmounted helpers, a new orchestration framework or repeated foundation setup. |
| Release prerequisites | Close L00/L11 capacity, writer authority, exact restore and release-profile prerequisites. Prepare concrete requests early. | Unrelated infrastructure cleanup or a general CI rewrite. |
| Independent verification | Review exact source and real terminal/browser evidence for both lanes; verify failure and recovery cases. | Self-approval, a summary-only review or a perpetual stream of audits without integration. |

One packet per implementation owner. Record: existing package ID, user-visible outcome, real caller (or QA entrypoint and downstream production caller), integration owner, owned files, source/dependencies, blocker category, acceptance command, expected receipt and full runtime bound. A helper without these belongs in its caller's task. Only one owner mutates each runtime/environment; independent readback is coordinated. Serialize scarce native/build capacity while unrelated permitted work continues. Use the available reviewer model and record it truthfully; Sol/Grok absence is not approval or a reason to claim their review.

### Reuse register — do not reimplement

Consult the latest handoff for current pins. These are the retained checkpoint identities, not permission to skip a changed-source or environment check.

| Existing asset | Reuse boundary | Reopen only when |
|---|---|---|
| Application a9ab52fe956e134b667d414a5b47f58cc5741e6b / PR6168 | Freeze it while resolving demonstrated qualification blockers. Managed security51 steps,59,870 unit passes,PG2/2,Chromium45/45 and build7 steps have source-scoped evidence. | A relevant source/dependency/profile change invalidates evidence, a real failure appears, or required final release policy demands a new run. Never transfer the old pass to a different merge implicitly. |
| Native2ff4ddb18d852ad423f6094c1149e4a03097412b | Existing app/native assembler, probe builder, runner and operator callers. | A demonstrated caller defect or fresh-generation binding gap requires a bounded repair. |
| Tooling85fa0401f1288a5e8527d087ed6a312d3453b3fc | Portable source, manifests and582 evidence members; signed Docker inputs, image donors and probe evidence. | Donor bytes or provenance fail verification. Actual daemon/VM readiness must be reacquired after stop. |
| Operator/VM0a4c7ba248cee6143661450a36969746656cdc8a | Existing controller/descriptor/prepare/install sources and31 terminal shutdown artifacts. | Actual rehearsal exposes a defect. Do not treat source tests or fixture staging as installed operator proof. |
| Root PG/runner controls | Reuse the checked-FD seed bridge, packet/successor producers, runner staging and bounded guards in current engineering evidence. | Exact consumer contract changes or a demonstrated runtime failure. Do not raise source-size limits to bypass the bridge. |
| QA disk scheduler PR6153/runtime4a015f9 | Scoped installation/readback is complete. | New evidence shows a defect. Free disk is not reserved capacity; retain per-run admission. |
| Shared preference/history, grants, outcome, onboarding and provider code | Use named package code locations and existing stores/routes. Finish integration and evidence gaps. | A recorded missing behavior requires change. Do not introduce parallel stores, duplicate timers, substitute provider proposals or another behavior engine for Telegram. |

A stopped guest is not ready to execute. The copied-disk resume adapter is implemented and a fresh generation has passed independent readiness checks; consult current state for its stop status. After shutdown, those readiness receipts are historical and do not authorize new effects. Reuse this adapter rather than rebuilding it. Old generation receipts cannot authorize new effects. Preserve old intents/UNKNOWN outcomes; inspect actual state and reconcile the original attempt instead of replaying it.

### Complete package execution map

Every original package remains required except explicitly deferred Z01. The detailed package records following this procedure retain all source locations, dependencies, acceptance text, tests and audit boundaries. “Reuse” does not mean accepted.

| Package | Preserve and reuse | Next required completion target |
|---|---|---|
| R00 | Existing execution/effect census and provenance | Complete scheduled, extension and non-REST caller coverage. |
| R01 | Delegation UI/ACK/CAS and recovery code | Original-attempt recovery, obsolete-writer exclusion and deployed truthful status. |
| R02 | Bounded specialist context and owned-target repair | Cross-path preference/memory/skill/lesson correctness and latency. |
| R03 | Handoff authorization, signed anchors and formal SQL | Restored production-shaped catalog, actual role/KMS and writer-fence proof. |
| R04 | Mounted signed handoff route and graph upgrades | Installed schema plus approved/denied/stale/uncertain requests through real callers. |
| R05 | Workflow outcome and saved-Research caller integration | Joined terminal authority, failure/refusal/lost-ACK recovery without repeated effects. |
| R06 | Shared agent contract and System model integration | Full chatbox/TG/background/delegation/System Workflow contract verification. |
| S01 | Original-aware room guards and legacy-safe default | Original transfer/storage/schema, old-worker exclusion and concurrent/late-worker UI proof. |
| N01 | Existing unmounted scanner/selector bridge | Durable cursor store, SQL qualification, old-worker drain and safe mounting. |
| G01 | Six-source attention dispatch/recovery composition | Current packet compatibility, six-kind terminal/checkpoint/provider recovery. |
| G02 | Producer inventory and cutover guards | Remaining notifications/event-bus/legacy exceptions; no duplicate interruptions. |
| D01 | Digest lifecycle, reservation and memory-write pieces | Joined original-attempt accounting/settlement/authenticated writes/recovery; keep execution held until qualified. |
| D02 | Embedding/compression/dreaming/conflict protections | Current-source ancestry, permissions, deadlines and late source-change qualification. |
| H01 | Existing history-before-state and CAS/SQL safeguards | Actual-role restored rehearsal, direct-writer coverage, installation and next-turn proof. |
| P01 | Owner-specific Guide/onboarding/readiness code | Current-source qualification, main-admin initial rollout and independent real readiness/recovery. |
| P02 | Link SDK/OAuth/grant cards and settled callback | Secure actual Stripe configuration, real connection and specifically authorized purchase qualification. |
| P03 | Migadu mailbox/ingress code and settled domain/provider | Approved subscription, credentials/DNS, real receiving and separately verified sending. |
| P04 | Private-computer source, privacy and takeover controls | Independent human reviewer/protected environment, approved image/host and live handback/expiry. |
| P05 | Phone/email/TG/location/friend-agent code | Exact authorized real journeys, revocation, dual consent and uncertain outcomes. |
| V01 | Frozen candidate and retained managed/macOS evidence | Missing native/schema/recovery, applicable hosted policy and final source provenance. |
| V02 | Local fixtures, baseline matrix and path inventory | Combined acceptance across all16 behaviors and supported paths; blocked cases remain visible. |
| L00 | Installed-ledger collectors and phased profiles | Fresh production roles/ledger, actual-role restored rehearsal and safe schema-before-app ordering. |
| L10 | Verified isolated prerequisites and implemented copied-disk resume adapter | Current-generation real app/DB/runner continuous admission/drain and recovery proof. |
| V00 | Exact application and partial profile evidence | Join application/native/schema/exclusion/recovery into one qualified inactive-release profile. |
| L11 | Backup/restore tools, reviewed repairs and old evidence | Fresh current standalone plan/approval and faithful data/ledger/role/catalog restore; join writer authority separately for full release. |
| L12 | Operator/controller adapters and reviewed fixtures | Real prepare/install/cutoff/backend-web observation, lost-ACK/competition/recovery qualification. |
| L01 | Qualified release tools; never deploy coordination branch by assumption | Merge/deploy the qualified inactive foundation and verify actual AWS image/source/schema/health. |
| L02 | Provider acceptance plans and independent readiness model | Authorized deployed provider tests and failure/recovery proof. |
| L03 | Existing activation, grants, version/history and cutover guards | Activate only qualified behavior; verify config/history/pause/revoke and producer readiness. |
| L04 | Live acceptance matrix and monitoring/recovery tooling | Independent live proof of all paths/all16 behaviors, provider outcomes and measured latency. |
| L05 | Evidence ledger and operating handoff | Reconcile accepted rows against deployed source and live/recovery proof; then close. |
| Z01 | Existing iMessage pilot and old scoped evidence | Deferred until after Telegram/chatbox release; do not spend this release's critical-path capacity here. |

### Qualification and evidence discipline

Before every expensive attempt, record the longest unresolved dependency chain and staff it first. Record the full-chain worst-case estimate separately from observed timings; never present an effect-only subtotal as the whole budget. Use stepwise admission for resumable qualification: each next effect must fit with its full existing transport and termination bounds, independent observation and protected recovery/shutdown reserve against every active deadline. Unstarted future phases need not all reserve their maximum timeout simultaneously. If the next safe phase does not fit, stop launching effects and reconcile/stop the current generation. An UNKNOWN outcome requires original-attempt process and receipt reconciliation before cleanup; never invent a quiescent handoff or replay. This permits useful execution without promising session completion, shortening tests or weakening acceptance. A later fresh-generation check is required after stopping, even when source and archive donors can be reused.

Test actual integrated paths: permission denial, failure, cancellation, concurrency, expired/revoked authority, lost acknowledgements and uncertain outcomes. Never weaken tests, budgets, signature/permission checks or acceptance to get green. Test embedded remote programs, not just the outer launcher. Check cross-controller artifact namespaces before staging. Preserve default/shared daemon identity and actual firewall invariants; do not hide drift. A bounded transition may join deterministic staging with execution only if the existing contract allows it; required prior independent gates remain required.

Keep one coherent frozen candidate. Only demonstrated blockers enter it; unrelated improvements wait. Record the changed source/dependencies and which checks they invalidate. Reuse unaffected evidence explicitly, retain original failures and require all applicable final gates. A new main commit does not automatically justify restarting every check; final deployed-source provenance still must qualify.

After the same blocker recurs twice without closing a dependency, stop repeating the attempt and perform a bounded root-cause/architecture review. Name the evidence gap, responsible owner, next discriminating check and restart condition. This is a planning rule, not permission to abandon scope or bypass a failed guard.

### External prerequisites and authority

Production capacity exceeded the unchanged85GiB floor at the2026-10-05T00:57:16Z observation; it is not reserved and must be rechecked before an attempt. Earlier low-disk snapshots do not justify repeating expansion work. Current writer-policy/CIDR and endpoint coverage remain unknown. Read-only inventory does not prove continuous writer exclusion. Network restrictions alone do not establish coverage of REST/Auth/Storage and every writer.

Do not serialize standalone backup preparation behind an unrelated access gate. The standalone capture path validates source/helper pins, known prior operations, container/database identity and read-only activity; it does not consume Supabase management-policy readback. A standalone backup-only run additionally needs the fresh reviewed plan, current capacity and specific shared-lock approval. The full release coordinator still requires continuous writer exclusion and heldWriters evidence. Preserve that distinction in the DAG: parallel preparation is permitted, joined release acceptance is not relaxed.

Prepare a fresh backup plan only after its inputs are valid; obtain the specific shared-lock approval required by its cross-project impact. Existing blanket migration authorization does not waive qualification or revive stale plans. No production effects follow from this documentation revision.

Preserve settled choices: Link for purchases, the existing registered application/callback, Migadu with mail.supraos.ai, Telegram/chatbox first. Do not restart provider selection or ask the owner to repeat completed setup. Distinguish an exported public PGP key from Stripe-issued credentials; use secure credential channels, never chat. Private-image publication requires a genuinely independent authorized reviewer; initiating-user self-review cannot satisfy it.

### Checkpoint, reporting and publication

At each checkpoint answer: which usable capability moved closer; which delivery dependency closed; what remains blocked, by whom and with what proof; are we finishing the current path or accumulating intermediate work? Report implementation, integration, tests, independent review, merge, deployment, activation and live verification separately. Do not convert task counts, number of tests or a subjective estimate into measured code completion.

Canonical inputs are `docs/agent-run/plan.json` (original62 acceptance rows), `docs/agent-run/execution-dashboard/progress.json` (32-package DAG and concise activity), this procedure, and `SupraOS-Universal-Agent-Completion-Handoff.md` (current narrative/source inventory). Do not manually maintain competing checklists. The original acceptance rows and package evidence are preserved when reordering work.

Regenerate with `python3 docs/agent-run/render-plan.py`, `python3 docs/agent-run/execution-dashboard/render.py` and `python3 docs/agent-run/render-public-handoff.py --update-private --output-dir <separate-output-directory>`. All views must retain this standing procedure. Validate package/task coverage and source references. Exercise changed dashboard behavior in a real browser. Documentation-only edits need renderer/link/sanitization checks, not a full application rebuild.

Publish authorized changes with normal non-force Git updates after checking existing work. The private coordination branch is codex/agent-run-execution-20260928 in jtobkin/suprafx-platform; it is not the deployable application branch. Publish only sanitized handoff/checklist/procedure to jtobkin/supraos-agent-completion-handoff and verify anonymous raw/rendered accessibility and exact bytes. Record private/public commit pairing. The old chatgpt.site artifact is historical. Preserve detailed private receipts by link rather than copying secrets, archives or host inventories publicly.

### Fresh-computer start and final acceptance

A new agent must not assume local memory, credentials, running workers or access. Read the public handoff/checklist; obtain private GitHub access through normal sign-in; fetch the canonical branch and explicit candidate/evidence refs; inspect status and processes; read root AGENTS.md, CONTEXT.md and required boot documents. Read this procedure, original ledger, package DAG, baseline matrix and latest terminal evidence before choosing work. The handoff supplies exact source pins, repository bootstrap and private data locations. Cloning does not copy private backups, disks or credentials.

Choose the first unresolved transition using current facts, assign the three lane contracts, prepare external asks and the complete runtime budget, then execute. Preserve others' work. Delete only your own merged, clean, inactive worktree under the owner's cleanup rule; never use forced removal or blanket pruning.

Finished means every required behavior is integrated into qualified deployed source, activated where appropriate, independently verified live and supported by monitoring and tested recovery. All16 baselines and every supported execution path remain in scope. An inactive release, passing build, completed native fixture or intermediate milestone is progress, never permission to redefine completion.
<!-- END STANDING EXECUTION POLICY -->

## Historical five-hour handoff — October 4, 2026

**Owner window:18:57:07–23:57:07UTC (October5 02:57–07:57HKT). Implementation and qualification effects are paused; final document verification/publication closes the window.** Both owned runtime layers are independently stopped as of23:20:26UTC. No application or database container was created. Shared infrastructure was not paused. This section supersedes all older active/“current” instructions below; dated historical evidence retains its original scope.

**Full project remains unshipped and inactive. Accepted:5/62(8.1%); pending:56/62(90.3%); deliberately dropped:1/62(1.6%).** These are accepted-task counts, not percentages of code, effort or production readiness. No production migration, backup attempt, shared deployment lock, deployment or activation ran during this window. Global attention remains off; `restoreVerified` remains false.

### Goal that remains unchanged

SupraOS agents should use one shared behavioral contract across chatbox, Telegram, delegation, background work and System Workflows: deterministic orchestration loads current scoped preferences and bounded relevant memory, skills and lessons; tools check permission before side effects and record truthful durable outcomes. Preference changes append before/after history to the hash chain before updating active state, so the next turn reads the latest saved value. Telegram is a communication channel, not a separate behavior engine.

Finished also requires all16 original baseline behaviors, resumable owner-specific onboarding, main-admin initial Guide authorization, independently earned capability readiness, qualified deployment/activation, live acceptance, monitoring and tested recovery. Preferences never silently grant permission. Simulated purchases, saved mailbox names and configured credentials do not establish capability readiness. iMessage stays deferred; the remaining32-package DAG below preserves the full agreed scope.

### What this window actually completed

1. **Isolated native foundation qualified.** A bounded smoke passed and stopped. A distinct18GiB/70GiB full guest independently proved its VM/kernel/network identity and resource/tool checks. Exact native Git2ff4ddb, all33538 tracked files and34 CODE pins passed guest readback and strict Git checks without alternates.
2. **Real private Docker prerequisites closed.** Signed offline Docker install, private daemon, private network, five pinned image IDs, Traefik/Node local tags, an actual side-effect-free probe build and byte-identical probe receipt projection all independently passed. Probe build audit a2e99832; projection c4178617. This is native release-rehearsal infrastructure, not deployment or testing of the full production application.
3. **Actual next caller inputs prepared.** The first native app/proxy packet was produced and independently verified (packet45f33804, auditc9ef0c79). At23:13:43 the actual app build was held because its full bound plus required shutdown checks no longer fit. All five app/proxy phases remain unexecuted. PostgreSQL baseline/bootstrap/PostgREST, runner, operator cutoff and recovery also remain unexecuted.
4. **Caller and portability gaps repaired.** Database seed/runner bridges bind actual receipt consumers and preserve their source/permission/deadline guards; the54KB seed is invoked through a checked-file-descriptor bridge without raising the broker source-size cap. Operator catalog/prepare/install/descriptor adapters and QA-only approval handling are source-reviewed/scoped-tested, not runtime-qualified. Fresh authenticated GitHub retrieval of root controls matched exact SHA/byte manifests and passed five scoped test commands.
5. **Additional candidate evidence preserved.** Exact-a9ab macOS contract tests30/30 and the unchanged officialNode refusal/no-child check independently passed, with donor-dependency limits recorded. Existing managed59,870unitPASS/0FAIL/252SKIP, PG2/2, Chromium45/45 and production build7steps are retained from the preceding candidate window; they were not rerun or newly earned here.
6. **Safe shutdown actually proved.** Private-daemon stop audit0e83c986 joins resultf74a0870; original daemon/containerd processes, socket and runtime are absent and data is preserved. Full-VM stop auditf0235234 joins result013297c7; original QEMU, QMP socket and listener are absent; the owned cgroup is empty or absent. The disk, seed, source, image cache and receipts are preserved. Exact firewall equality passed across both shutdowns. A separate earlier change in the shared host's existing Fail2ban SSH set is explicitly recorded; there is no claim that the host firewall stayed unchanged throughout the entire multi-hour window.

[Current window evidence and source map](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/evidence/resume-isolation-20261004/README.md) · [Root database/runner controls](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/evidence/resume-isolation-20261004/guest-post-app-controls/README.md) · [Fresh-directory GitHub retrieval proof](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/evidence/resume-isolation-20261004/portable-db-controls/README.md).

### Exactly what is saved and where

- **Frozen application:** `codex/agent-run-release-composition-20261004` at **a9ab52fe956e134b667d414a5b47f58cc5741e6b**, PR6168. At23:20:15UTC GitHub still reports open/unmerged, mergeable/clean, auto-merge null, both managed statuses successful. Main is5bd8d1f9ccd6d52cc6bf0c44ca83252d93a64f96. Six hosted startup failures were last observed earlier; hosted/macOS and required-check policy are not silently declared green.
- **Native runtime caller:** `feat/agent-run-full-native-guest-20261005` at **2ff4ddb18d852ad423f6094c1149e4a03097412b**, tree5143d45447bbdbd62e9d20bfb028de86db239ee4. Start with `scripts/qa/agent-run-cutoff-native-assemble.py`, `agent-run-cutoff-app-assemble.py`, `build-agent-run-cutoff-probe.py`, native runner and `money-release-operator.py`.
- **Portable host/tooling evidence:** `evidence/native-guest-tooling-20261005` at **85fa0401f1288a5e8527d087ed6a312d3453b3fc**. Start `FULL-GUEST-HANDOFF.md`, `manifest.json`, `full-guest-held/` and `audits/`;582 members verified. This branch preserves generation-bound controllers, intents, receipts, independent audits and the private-daemon stop. It contains no large disk/archive or private credential material.
- **Operator/VM integration and terminal shutdown:** `feat/agent-run-isolated-native-guest-smoke-20261005` at **0a4c7ba248cee6143661450a36969746656cdc8a**. Start `scripts/qa/README-held-native-guest-operator.md` and `README-native-kvm-guest-smoke.md`; final `scripts/qa/evidence/native-shutdown-20261005/` contains31 hashed artifacts plus manifest. Actual VM stop, raw firewall evidence and independent terminal audits are saved there.
- **Root coordination:** `codex/agent-run-execution-20260928`, this handoff, `docs/agent-run/plan.json`, `PLAN.md`, `EXECUTION-PLAN-20261001.md`, `execution-dashboard/progress.json` and `index.html`. Root PG/network/runner controls and tests are in the linked current evidence folder. The coordination branch is not the deployable application candidate.
- **Managed application logs:** `evidence/private-cutoff-r6-20261004` at4599bfd79a0006076452ddd7acb081208b600371, `ci/`. Evidence stays bound to recorded synthetic7c25/main9ee; unavailable original merge object and separately reconstructed tree are disclosed.

Public handoff/checklist/procedure are sanitized snapshots in `jtobkin/supraos-agent-completion-handoff`. They grant no private repository or host access. The private engineering inventory below explains historical machine paths, retained data, normal sign-in and explicit branch fetches for a fresh computer. No local memory or credential should be assumed.

### Next tasks, in dependency order

1. **Make safe guest recovery concrete.** The current launcher cannot resume the stopped disk: it demands a fresh root and creates a new overlay. A separately reviewed copied-disk resume adapter is missing. Bind preserved disk and stop evidence, use new VM/native identities, independently prove the new generation and requalify source/archive donors. Never restart the spent unit or reuse old phase receipts as live authority. This is a missing caller integration, not missing permission to replay.
2. **Complete the real native rehearsal chain.** Run the five app/proxy phases → PG baseline/bootstrap/PostgREST → actual operator/descriptor/QA marker/runner → continuous admission/cutoff/lost-ack and recovery proof. The “old app” is the side-effect-free release probe fixture; this does not replace real application/provider acceptance. The first packet and source-only adapters are already preserved; stop rebuilding completed primitives without a changed dependency.
3. **Resolve production recovery prerequisites in parallel.** At21:45:56UTC production has62,912,188,416bytes free,28,355,866,624bytes below the85GiB floor; volume remains300GiB. The existing snapshot/364GiB expansion approval is pending. Current Supabase allowed ranges and endpoint/writer-policy authority remain unknown; Claude is unauthenticated in this session. Obtain current authority through authorized access, then prepare/review a fresh backup plan and obtain that plan's specific cross-project lock approval. Old approvals and stale plans are not reusable. Prove faithful data, ledger, roles and catalog restoration.
4. **Join qualification before release.** Reconcile current installed migrations/roles, the exact phased profile and final candidate provenance. Main added desktop migration20261005010000; refresh the ledger/writer census rather than blindly replaying it. Complete native/schema/recovery/operator gates and applicable hosted policy, then qualified merge and inactive AWS deployment. Do not re-enable auto-merge while release holds remain.
5. **Activate and independently accept the full product.** Complete specifically authorized provider journeys, all16 baselines and every supported execution path, truthful readiness, monitoring and tested recovery. Link's actual configuration/authorized purchase, Migadu subscription/DNS/delivery and private-computer independent-review requirements remain separate dependencies. Preserve the complete scope until L05 is actually closed.

### How parallel work must continue

Root integrates and owns release decisions. Three workers cover the same delivery path: implementation plus actual caller integration; host/release prerequisites; independent review and end-to-end evidence. Each component needs a named caller, integration owner and true/false acceptance test. Keep one frozen candidate; only demonstrated blocker fixes enter it. Report built, integrated, tested, independently reviewed, merged, deployed, activated and live-verified separately.

The initial three Sol workers hit provider capacity around23:06; one retry also failed. Three replacement Codex workers reconciled actual one-use state and completed the remaining foundation/stop audits. Their reviews identify the replacement reviewer; no Grok worker ran during this window. Do not infer an audit from a timeout or unavailable model.

New execution lessons are applied in the updated procedure: test embedded remote programs, check cross-controller artifact names before staging, reserve complete shutdown/publication bounds, and define a valid resume path before provisioning. The stopped guest and source packets are retained; no branch was merged and no unmerged worktree was deleted. All remaining32 packages and original62 acceptance rows follow below.

## Historical pause checkpoint — 2026-10-04 16:17 UTC

The owner authorized a two-hour window from **14:30 to16:30UTC on October4** (22:30October4 to00:30October5 HKT), then a pause and detailed handoff for a fresh account/computer. **Implementation and host work are paused; all three Sol workers have completed their handbacks.** Only final document publication and anonymous verification are authorized during closeout. No new effects are admitted. Resume only after a new owner instruction and fresh source/access/state checks.

During this window, root plus three Sol workers completed the repaired application candidate's managed qualification, repaired actual native and downstream caller bindings, preserved the native UNKNOWN outcome, and independently checked evidence and fresh-computer portability. All10 bounded Grok jobs are terminal; their tracked PIDs were absent at16:06:50UTC. Current managed application jobs are terminal success. The R6 private daemon is stopped, confirmed by independent stop proof and a later read-only census. No private runtime or manual qualification worker is left running. Shared infrastructure and unrelated jobs were not stopped.

The content handoff/checklist received independent Sol review (`b9cf0e8c`) at exact private5760ef51/public16:12 snapshot, plus a bounded Grok consistency review whose material wording findings were corrected. Later pause/publication metadata and the16:13 GitHub paragraph are root closeout edits, not a claim of another independent runtime audit. Acceptance remains **5/62**; no full-project deployment or activation occurred. The prior checkpoints below retain historical evidence only.

### Results of this two-hour window

- **Application integration closed with scoped proof:** `codex/agent-run-main-successor-20261004-1430` contains source `6cb14f99032769286dc735ea071412f42b318023` (tree `b46933b7959f4598311d046b4da9d21ad684925a`), merging exact main `a89e2931af63de8b884f2a36b3ca0b8932f9d6a7` into frozen f0da. Five conflicts preserve owner isolation, cancellation and truthful run responses. Linux77/77 focused/real Chromium tests,151 changed-file types and generated runtime checks passed. Independent Sol audit `4e0b25f0` verifies source, parents, raw logs and terminal state; Grok source review also passes. Docs-only follow-up `a9ab52fe95` preserves evidence in `docs/agent-run/evidence/main-successor-20261004-1430/`. After independent review and a clean merge check against main9ee959, the docs-only successor **a9ab52fe956e134b667d414a5b47f58cc5741e6b** (tree **348151fccce5b159bb21f694a1c7cd6de1e1454d**) was fast-forwarded onto PR6168. It is now the frozen application candidate. Both managed jobs are now terminalPASS and independently verified: security51steps,59,870unitPASS/0failed/252skipped,PG2/2,Chromium45/45; build7stepsPASS. Both record synthetic merge7c25b6d7e0a17cb45b79bc934db8f76642928076 with main9ee959. Audit e9123f56 verifies host specs/results and identical full host/local log hashes24eefde6/744fb758. macOS Native Land was not run; build skips two hosted-runner disk/swap infrastructure steps. [Complete logs/specs/results and source provenance](https://github.com/jtobkin/suprafx-platform/blob/4599bfd79a0006076452ddd7acb081208b600371/ci/README.md) are committed separately without changing the frozen candidate. The synthetic object was unavailable at evidence capture; exact-input reconstructed tree297e65e1 and reachable GitHub merge provenance are preserved separately, not presented as a readback of the original object. Auto-merge is disabled; explicit release hold remains. Prior f0da full passes remain predecessor-only, not qualification for a9ab. Nothing was merged to main or deployed.
- **Native caller repair actually exchanged:** `feat/agent-run-cutoff-traefik-local-base-20261004` / `a2ea6db0b84f2b7c0f9dcfbddf30888cb3e0b125`, tree `6cab912a423a783158d2992803cd4b2d9fbba0ab`, binds the exact local Traefik tag/image and context receipts through the real five-phase caller. Four tests, Sol/Grok source review and actual host source-exchange audit `1cc4a950` pass. Old3c442 source is preserved. Inert context-v2 and seed-r8 source stages independently passed readback audits bb704350 and645939d6. R6 own-unit stop independently passed baf934: unit PID0, private processes/runtime/socket absent, shared Docker generation and full stop-firewall pair unchanged. Source/data and failed load evidence remain preserved.
- **Actual runtime blocker retained:** R6 daemon/network setup passed, but its four-image load is **UNKNOWN_NO_REPLAY**. Four exact image IDs are present, zero containers were observed, and no positive result exists. Independent audit `0a2a8a60` confirms two structural host firewall rules disappeared during the load. No fifth image, base tag, probe, application, PostgreSQL, runner or Money effect followed. Another identical attempt would not resolve the shared-host coordination problem. No enforceable current admission gate covers box-ci, separate Actions runners, prune timer and other Docker clients; no shared service was changed. The later unchanged stop-firewall pair proves only the stop caused no structural drift; it does not prove restoration of the two rules lost during the earlier load. No restoration was performed or claimed.
- **Downstream source prepared:** `evidence/agent-cutoff-post-app-a2ea-20261004` / `1967b86187f1d08c5135aa550116f838a3e60e42` preserves seed-r8/PG packet-r9/runner-r7 and the held gatekeeper caller pins/tests. Grok found that the runner accepted a real stale source; it now refuses exact prior3c442 and wrong builder IDs. Grok61 follow-up and Sol confirm the runner repair; gatekeeper source review also passes but remains unmounted. Source review is separate from blocked host execution.
- **Diagnostics improved without replay:** [held four-load diagnostic successor](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/evidence/four-load-diagnostics-20261004/README.md) retains bounded failed command and timeout/output-cap observations. Five tests and independent Sol/Grok source reviews pass. Its admission is unset; no new load ran and no UNKNOWN was reclassified.
- **Acceptance:** still **5/62 (8.1%)**, with **56 pending (90.3%)** and one deliberately dropped. These are accepted-task counts, not code or effort completion percentages. No production backup, migration, deployment or activation occurred in this window.

**Fresh GitHub readback at16:13:19UTC:** PR6168 still has exact heada9ab, is unmerged and mergeable/clean, and auto-merge is null. Both managed box-ci contexts are success. Six separate GitHub Actions runs report `startup_failure`; this is not an all-Actions-green claim and their cause is not established by this readback. Preserve the managed-versus-hosted distinction and verify any required branch-protection policy before a later qualified merge.

**Fresh read-only production observation:** public `/api/version` returned main `9ee959f0e01c37b142a8e2b3bdfbbc21dcf8fc6d` at15:41:09UTC; app/cron were running with zero restart counts at15:38:06. This was another main-branch deployment, not the Agent Run candidate. Backup filesystem free space was61,270,511,616bytes (~57.1GiB), below85GiB. No production changes were made by this session.

## Historical pause checkpoint — 2026-10-04 14:06 UTC

The owner requested a five-hour run from **09:13:30 to 14:13:30 UTC on October 4**, followed by this detailed handoff and a pause. Implementation and host effects are now stopped; final document publication and verification close out that window. A new session must explicitly resume, inspect current state and obtain its own normal access. Older active next-action instructions below are historical.

**Full project: unshipped and inactive.** Accepted tasks remain **5/62 (8.1%)**, with **56 pending (90.3%)** and **one deliberately dropped (1.6%)**. These are acceptance counts, not code completion or estimates of remaining effort. No full-project merge, deployment, migration, activation, backup attempt or shared deployment lock ran in this window.

- **Application qualification advanced.** Frozen PR6168 head `f0da37f75370ffdc9b701e1e983e7f1f4de27964` has green managed security and production-build contexts: 59,804 unit passes, zero failures, 252 skips; PostgreSQL 2/2; real Chromium fidelity 45/45; production build seven steps passed. Full raw logs were transferred, hashed and independently checked. Security used f0da/mainbd3c; build used test merge `d32f5056451410351da03ccc49f2258758877d67` against main `7ec9d4c72bd3288566030fb5a1f97e2e907e096f`. Preserve that source distinction. Native/schema/recovery and final release provenance remain open. [Evidence](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/evidence/ci-f0da-20261004/README.md).
- **Private native setup advanced through the real probe build.** Active native source remained `3c442b6fadeb847ad81b6fbb291cc65e69e49899`. R5 daemon readiness, private network, five exact images, Node tag, probe build and byte-identical receipt projection independently passed. This is disposable QA evidence, not production capability. Historical R4 fifth-load UNKNOWN was preserved and archived; it was never relabeled as success.
- **The first application build exposed the next concrete blocker.** BuildKit interpreted the untagged `FROM sha256:312671...` Traefik base as a Docker Hub repository and failed private DNS. R5 build-traefik remains `UNKNOWN_NO_REPLAY`: its intent and before-firewall snapshot exist, but no positive receipt, target image tag or IID. No later app, PG/REST, runner or Money cutoff phase ran. The exact local Traefik base tag/reference repair remains **unimplemented**. Diagnostics-only successor `faab397dd1225c0f2f04f2cf461966f3c658769b` passed two focused tests and independent Sol/Grok53 source reviews; it was not installed on the host and does not fix the base reference. Timeout/output-cap diagnostics remain outside that narrow repair.
- **The private environment is safely stopped.** Independent audit `8a99891d5eab77c713881f0bb39908cb264228df7da222b783389cca4474f2e9` confirms PID0, absent private processes/runtime/socket, no active phase client, unchanged shared daemon generation and equal full firewall structure. Zero containers and six images were observed before stop; the private API is unavailable afterward. Data, source, receipts and spent intents remain intact. [Current source/evidence index](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/evidence/native-generation-successor-20261004/README.md).
- **Recovery still blocks release.** Read-only AWS health at 13:14:25 UTC found healthy app/cron after an unrelated deployment, but only 61,698,498,560 bytes free (about 57.5 GiB), below the unchanged 85 GiB backup floor. Backup plan49c5 is stale and unrun. Resolve durable capacity and writer-policy authority, then capture/review a fresh plan and obtain its specific shared-lock approval. Prior cleanup and backup intents must not be replayed. Overall `restoreVerified` remains false; global attention remains off.
- **Fresh-account recovery is portable.** Host controllers and 42-file evidence manifest are pushed on `evidence/private-cutoff-r5-20261004` at `9e3911ff60c555afdb0f60107825127dc7ddc9f1`. Caller/projection/failure evidence and the diagnostic successor are on `evidence/app-build-diagnostics-20261004` at `945918d72e95eef0c4429d3287e71768a72ee0e6`. Seed, runner and unmounted gatekeeper sources have separate named branches below. Large private archives remain on the authorized hosts; their locations and hashes are documented. Public documentation grants no private repository or host access.

Parallel work used root plus three Sol lanes for caller integration, host qualification and independent review, with replenished bounded Grok reviews. Exact-source findings were triaged; cancelled, incomplete and contradicted reviews were never treated as approval. Workers are winding down into this handoff, with no further host effects admitted.

## Resume order reference

Use the five ordered tasks in the current final handoff above, together with the32-package DAG below. Earlier full-guest-ready instructions describe a generation that is now independently stopped. Preserved disk/source/archive bytes can be reused only through a separately reviewed fresh-generation recovery path; they do not authorize replay of old operations. The complete release/provider/live-acceptance scope is unchanged.

## Historical active checkpoint — 2026-10-04 10:40 UTC

**Run window:** October4 09:13:30–14:13:30UTC, then pause and publish a detailed fresh-account handoff/checklist. Root and three Codex Sol workers cover integration, host qualification, and independent verification. Grok workers receive bounded source reviews and blocker investigations. A timeout or cancelled review is never approval.

**Full project remains unshipped and inactive.** Accepted tasks remain5/62(8.1%),56pending(90.3%),1deliberately dropped(1.6%). These are acceptance counts, not effort or code-completion estimates.

**Application candidate:** `15bb94f9a86038ef77dc5d4a5980169aa23620c4`, tree `7a615d4fe29dea992bdd4f6581eea6fc50c7853d`, branch `codex/agent-run-release-composition-20261004`, [PR6168](https://github.com/jtobkin/suprafx-platform/pull/6168). Pushed, unmerged, release-held. It adds one demonstrated test-fixture race repair: temporary migration files now live in disposable Git repositories, avoiding deletion while a separate real repository scanner reads them. Production checker, assertions and budgets are unchanged. Both affected testfiles passed110/110 concurrently; Grok25 independently source-reviewed the exact patch. New managed CI is pending.

**Prior CI evidence remains source-specific:**458f first production build passed7steps and was independently verified; first full units59763PASS252skip/typesPASS, but securityRED on the180s PG integration budget. Managed retry on testmerge1c3c/main8c2f passed PG2/2 in67.39s, then terminalRED:59795unitPASS/1FAIL/252skip and browser fidelity44PASS/1FAIL. The unit failure is the race repaired above. Preserved real browser trace shows failed webpack download `ERR_NETWORK_CHANGED` and an unhydrated page. No UI or browser-test edit was made; a new managed browser pass is required. Retry build did not run after securityRED. [Evidence](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/evidence/ci-458f6-20261004/README.md).

**Native path:** corrected six-file QA source `ce50d579fa377d5a09fbbe50114108e9f4af80ef` / tree `e5c2d4a7c91ccf6fed0f5699e34f5161d07666da` is now the active private rehearsal checkout. Independent audit verified strict Git fsck, clean source, all33535files/745614495bytes and34CODE pins. Atomic exchange preserved oldee969 and failedr3 evidence; active swap audit e3d2e03d. The correction compares firewall structure while ignoring only validated packet/byte counters; unknown/malformed rule fields remain checked.13producer+3firewall testsPASS plus Sol/Grok source review. Stopped daemonr3 is preserved and fresh empty tree independently sealed9cfc0f44. Fresh daemon readiness remains pending; no images/network/app/PG effects yet.

**Prepared downstream:** inert seed-r3 source stage independently sealed34ad29d1, networkr4 source stage sealedf744cbc8, app/PG/runner controllers source-reviewed. Strategies context is independently sealed at77962members/~2.23GB, no image. Strategies is not a PG-start prerequisite. Gatekeeper's current untracked helper is source-reviewed only and deliberately outside frozence50; it cannot establish readiness.

**Recovery:** fresh read-only attempt `dfd40ff4-37d4-4fee-b7f9-8459be4311a4`, plan SHA `15756ae45fb521a6a15828a9554fc3403a9bae142fc0c4ea70db516bce376677`, captured09:37:42UTC, expires13:37:42UTC. Grok source review found it consistent. The reviewed107-ID allowlist cleanup removed only old unused immutable private regular BuildKit cache, recovering15.07GB. Terminal free space92447862784bytes (~86.1GiB) exceeds unchanged85GiB floor; effect-time recheck required. No images, containers, volumes or retained backups were removed. No backup or deployment lock ran. A new specific approval is required for this attempt's shared lock: up to127minutes holding plus30minutes waiting; both sites stay online, deployments wait; no migrations or activation. Prior approvals were consumed. The exact prepared invocation and safety limits are in the private evidence linked from the engineering plan.

**Next:** managed candidate checks; corrected private daemon→pinned images/probe→network→five actual app phases→PG/ninebaselinechecks/bootstrap/PostgREST; actual operator lost-ACK/continuous-drain proof; faithful recovery with fresh approval; qualified merge/deploy/activation/live acceptance. Historical browser/schema/full-suite passes remain scoped to their exact sources and controlled fixtures. No intermediate helper is counted as shipped capability.

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
| Universal Agent combined source | Current a9ab PR6168; independently verified51 managed security steps,59,870 units,45 Chromium cases,PG2/2 and7 build steps PASS | Native/macOS where applicable, schema/recovery, deployment and live acceptance remain open.252 unit skips remain unverified. |
| Global attention and new SQL | Cutover off; phased profile and installed ledger must be re-read | No implicit activation or migration from code presence |
| Backup/recovery | Coherent historical capture and many scoped checks | Overall restoreVerified=false; restored-copy/role/profile/writer-window qualification incomplete |

A fresh GitHub PR readback at 2026-10-03 19:31:16 UTC showed PR5862 **open, draft, unmerged and conflicted** (`mergeable:false`, `mergeable_state:dirty`), with coordination head `6f466ab8eaf6a346475b4dad44d1f978ae1e5bd1`. This PR does not point to the frozen f74 application candidate. Its API-reported base SHA is metadata for that PR, not a substitute for freshly reading `refs/heads/main`. A later merge/release proposal must use the actually composed, qualified application source; the coordination PR is not a deployable shortcut. No merge was attempted.

Latest retained public live-source observation names `9ee959f0e01c37b142a8e2b3bdfbbc21dcf8fc6d`, read at `2026-10-04T15:41:09Z`. The read-only public `/api/version` request through the QA host succeeded. This is a source stamp only, not authenticated behavior, running image/config equality or proof that the frozen Agent Run candidate is deployed. Main can advance independently.

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
| Current native guest qualification source | `feat/agent-run-full-native-guest-20261005`, **`2ff4ddb18d852ad423f6094c1149e4a03097412b`**, tree `5143d45447bbdbd62e9d20bfb028de86db239ee4` | the original private worktree (see engineering handoff); exact clean guest import independently passed. Source for the native assembler, app phases, probe, runner supervisor, Money operator and migration profile. Different source role from the application candidate. |
| Current portable guest operator adapters | `feat/agent-run-isolated-native-guest-smoke-20261005`, `0a4c7ba248cee6143661450a36969746656cdc8a` | Start with `scripts/qa/README-held-native-guest-operator.md`; fixture/catalog/prepare/install/descriptor adapters and scoped tests. Actual fixture passed; operator prepare/install remain pending. Later source-only additions must retain their own commit and audit scope. |
| Current root database/runner/network controls and audits | Canonical coordination branch, `docs/agent-run/evidence/resume-isolation-20261004/guest-post-app-controls/` | Generation-bound sources, tests, SHA manifest and independent audits. Exact local working sources under the original private worktree (see engineering handoff); do not execute after this guest stops. |
| Current frozen application candidate | `codex/agent-run-release-composition-20261004`, **`a9ab52fe956e134b667d414a5b47f58cc5741e6b`**, tree `348151fccce5b159bb21f694a1c7cd6de1e1454d`; PR6168 | Current matching root checkout is the original private worktree (see engineering handoff). The older release-composition local checkout remains at f0da; inspect/fetch rather than assuming it moved. Managed security/build independentlyPASS; release hold and auto-merge-off remain. |
| Current candidate source/evidence mirror | `codex/agent-run-main-successor-20261004-1430`; source `6cb14f99032769286dc735ea071412f42b318023`, tree `b46933b7959f4598311d046b4da9d21ad684925a` | the original private worktree (see engineering handoff); merges exact maina89e into f0da,77 focused/Linux browser tests,151 types and generated bundle pass. Independent review passed4e0b25f0; docs-only evidencea9ab52fe follows. No full-suite/build inheritance. |
| Historical native Traefik caller predecessor | `feat/agent-run-cutoff-traefik-local-base-20261004`; `a2ea6db0b84f2b7c0f9dcfbddf30888cb3e0b125`, tree `6cab912a423a783158d2992803cd4b2d9fbba0ab` | Exact local tag/image/context binding in real app caller,4 tests and Sol source review pass. Host exchange independently passed1cc4a950; actual application proof is blocked by the image-load UNKNOWN. Do not use the application successor as native source. |
| Previous native operator base | `feat/agent-run-operator-coordinator-mount-20261004`; `3c442b6fadeb847ad81b6fbb291cc65e69e49899`, tree `4d8b9af96ccffac2b09c3fbe63cc947ac5e0c103`; pushed, independently source-reviewed | the original private worktree (see engineering handoff); source/test work owned by Sol B/C, independent A; preserve untracked gatekeeper helper |
| Portable private R6 host controllers and current application CI evidence | `evidence/private-cutoff-r6-20261004`; current tip `4599bfd79a0006076452ddd7acb081208b600371`, native bundle predecessor `4a233465d287a471b31f011ceff52a3582bca5ea` | Native:35 SHA-verified small files, manifest1c40e64b, README-R6.md. Later `ci/` adds13 verified payloads, manifest45d60ea2, full current-a9ab logs/specs/results/audit and reconstruction provenance. Includes actual a2ea import/exchange, R6 load UNKNOWN and independent stopbaf934, plus shared-writer assessment. Full image archives/checkouts remain on authorized host; no private daemon is running. |
| Portable post-app source repairs | `evidence/agent-cutoff-post-app-a2ea-20261004`; `1967b86187f1d08c5135aa550116f838a3e60e42` | Seed-r8, PG packet-r9, runner-r7 and held gatekeeper caller with focused stale-input tests, plus exact next native caller/receipt/gap inventory. Source-only unless a stage is explicitly sealed; no application/PG/runner/gatekeeper effect. |
| Portable private R5 host controllers and evidence | `evidence/private-cutoff-r5-20261004`; `9e3911ff60c555afdb0f60107825127dc7ddc9f1` | 42 hashed source/receipt/audit members, manifest `a161c099ec411a5543a1b8dc230fbd548a9065564b41ae2f19f5efa224a6e123`; private QA only, preserves historical UNKNOWN. Large image/source archives remain on authorized host, locations listed in bundle README. |
| App-build diagnostic successor, not active | `evidence/app-build-diagnostics-20261004`; `faab397dd1225c0f2f04f2cf461966f3c658769b`, tree `b0a57f4c5f9693a2bcb9db7b068dc15fd1b8e4c7` | Narrow source-only nonzero-build diagnostic retention, two focused tests passed; Sol and Grok53 independently source-reviewed. Branch head `945918d72e95eef0c4429d3287e71768a72ee0e6` additionally preserves caller/projection/UNKNOWN/stop evidence under `qa-evidence/cutoff-r5-handoff/`, manifest `f6497a1617d4dee1b8015012b038195280345b0ddd5ad542132ed8b4ba106e29`. Active host source remained3c442. Does not repair Traefik base reference and was never run on host. |
| Portable seed entrypoint repair | `evidence/seed-r7-20261004`; `c7bb97ebbf8818a1ca9e9bcdc464aa785445b81b` | Exact QA seed/app stagers and launchers, actual-entry and packet-contract tests, manifest and README; source-only evidence branch, independent source/stage audits, no database effect. At that historical capture runtime Git was3c442; that historical native source was a2ea with R6 stopped; current full-guest source is2ff. |
| Portable runner and unmounted gatekeeper | `evidence/zero-runner-r5-source-20261004` at `b7809130b72eddaea102680c04243a34487ae76d`; `evidence/gatekeeper-listener-source-20261004` at `873fd8d030246686ac2aaf814f104c26ffa50783` | Source-only retained components; no runner, gatekeeper or production effect. Caller integration remains gated by real runtime evidence. |
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

**L10 — continuous writer exclusion.** Old direct database writers share the postgres role and can reconnect. A REST admission flag, NOLOGIN, one idle connection census or absence of recent effects does not prove exclusion for the full migration window. Actual network restrictions and process/ingress authority must be identified, then continuously verified. Owner reported restrictions enabled but current IPv4/IPv6 CIDRs and UTC readback are unknown. Claude was requested for this; a fresh read-only `claude auth status` at2026-10-04~12:18UTC still reports loggedIn:false in this session. Another Terminal/account login cannot be assumed accessible here. Do not claim Claude or Grok evidence that did not happen.

**L11 — restore fidelity.** The helper matched 826/826 tables, rows/ledger and role/data authority, but the wrapper rejected an expression-catalog fingerprint. That archive covers public and supabase_migrations, excluding managed auth/storage/vault schemas; it was coherent but taken while application writers remained active, not a drained release-window or whole-cluster backup. Overall restoreVerified remains false; old statements that role fidelity itself still failed are superseded by this narrower diagnosis. Reviewed lossless expression framing is composed in `scripts/qa/agent-run-production-backup.py` and staged with `scripts/qa/agent-run-standalone-backup.py`. Read [current capture preparation and exact helper hashes](https://github.com/jtobkin/suprafx-platform/blob/codex/agent-run-execution-20260928/docs/agent-run/evidence/l11-next-capture-readiness-20261002/README.md) before preparing a successor; it distinguishes expired plans from a fresh authorized attempt. The old 75455 plan expired and must not be replayed. Latest retained AWS space at2026-10-04 15:38:06UTC was61,270,511,616bytes (~57.1GiB), below85GiB admission; recheck. The app and cron were running with zero restart counts; this readback did not establish Agent Run readiness. A fresh bounded source-pinned capture/plan and its concrete shared-lock approval are required. Prior lock approval was consumed; sites stay online while deployments wait. Standalone restore alone does not close migration-role and writer-drain rehearsal.

**L12 — release coordination.** Retained reopen authority, journal ownership, lost ACK, contenders, schema transition, backend/cron/web observation and recovery must compose into one reviewed real operator. Current observers explicitly do not establish complete health or continuous writer exclusion. Qualify on restored-copy/native transport before production.

**Owner authorization.** Automatic migrations were expressly approved on 2026-10-02. Do not ask again merely for routine qualified migration. This does not bypass current technical gates or grant an unbounded shared cross-project deployment lock.

**Providers.** Link is settled; application and live Stripe account exist, but actual approved client configuration and Stripe-delivered credentials remain unverified. Partner-generated public `.asc` is not the provider secret. Callback `https://supraos.ai/api/vms/link-agent-wallet/callback`. Migadu/mail.supraos.ai is settled; subscription, securely installed credentials, authorized DNS and real delivery remain. Independent human browser-image publication reviewer/protected environment remains unresolved; initiating jtobkin self-review is insufficient. Never request secrets in chat, restart Privacy.com, make purchases, alter DNS or send consumer tests without their specific authorization.

## Immediate blockers by type and next owner

This table is a resume order, not a reduced definition of finished. The full 32-package graph and original 62-task acceptance ledger follow it.

| Delivery dependency | Type | Next owner | Proof that closes this dependency |
|---|---|---|---|
| Application managed checks closed; remaining final-source provenance | Evidence preservation and qualification boundary | Root and independent reviewer | Exact-a9ab51 security/7 build steps independentlyPASS e9123f56. Same recorded7c25/main9ee merge; full raw logs retained. Preserve synthetic-object reconstruction limit and remaining native/macOS/schema/recovery gates. |
| Remaining actual browser/native and 17-packet schema proof | Evidence and host capacity | Qualification worker | Real required paths and role-bound forward/rollback/reapply/invariants under unchanged resource floors; skipped environment gates do not pass |
| Continuous writer exclusion and old-web cutoff | Code, access and evidence | Implementation worker, authorized operator | Real production constructor/callers, actual network-policy readback, all-origin admission/drain proof through the complete migration interval |
| Faithful restored-copy rehearsal | Capacity approval and evidence | Release operator, independent reviewer | Fresh concrete source-pinned plan, sufficient disk, specific shared-lock authority, complete role/catalog/data fidelity and tested recovery; earlier consumed approvals never replay |
| Joined release operator | Code/integration and evidence | Root with implementation worker | Same original journal coordinates ingress, writer barrier, schema transition, backend/web observations and retained reopen/unknown recovery; qualify restored-copy transport before production |
| Provider readiness and browser publication | External configuration and specific authorization | Authorized provider/admin owners | Actual approved Link configuration, secure credentials and authorized qualification; Migadu subscription/DNS/delivery; eligible independent publication review |
| Deployment, activation, all paths and all 16 baseline behaviors | Integrated release/live evidence | Root, operator and independent verifier | Qualified phased release, actual configuration/source readback, authenticated live cases, monitoring and recovery; no task acceptance based on code presence |

QA and production capacity are separate dependencies. Recheck exact applicable floors at every new admission; never lower them. Historical October3 build/native measurements are superseded by the current host receipts. AWS production had67,403,169,792freebytes (~62.8GiB) at12:05UTC onOctober4, below85GiB backup start floor. The pending production-volume capacity proposal does not increase Hetzner QA disk. Local Mac disk recovered5.3GiB after removal of only two completed reproducible model clones; preserve project worktrees and evidence.

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

**Remaining:** Linux managed security/build and subsequent scoped macOS contract checks passed for their exact source. Complete joined native/schema/recovery and final release provenance; establish required hosted-check policy. Existing donor dependencies mean local macOS proof is not a clean hosted job. Original synthetic commit unavailable; reconstructed tree is distinct evidence.

**Acceptance:** Current required contexts green plus independent exact-source Sol review and actual UI; older full build cannot qualify new source.

**Source:** `scripts/ci/box-ci/merge-if-green.sh`, `tests/native-qualification/`.

**Evidence:** implemented Reviewed main-conflict repair6cb + evidencea9ab now frozen on PR6168 via verified fast-forward fromf0da. Native QA is separate; automatic merge disabled and release hold retained.; tested Current a9ab managed:59,870 unitsPASS/0failed/252skip; PG2/2; Chromium45/45;51 security steps and7 production build steps success on recorded7c25/main9ee. Prior scoped6cb77tests/151types/bundle alsoPASS. macOS Native Land unrun; two hosted-runner disk/swap build steps skipped by design. Resume exact-a9ab local Darwin: HomebrewNode22.23.2/uv1.52.1 two required files30/30PASS; officialNode22.23.2/uv1.51.0 refusalPASS (no child). Initial wrong-build path RED preserved; no assertion changes.; independently reviewed Independent Sol audit e9123f5637144f565a5c519a8af8e02b1c3b6c35f1e199e910349f3cf1cb270a directly reads host spec/result and hashes host/local logs24eefde6/744fb758. Both contexts same recorded source inputs and successful terminal. Scope does not include native/schema/recovery/live. Independent Sol directly matches four source SHA to a9ab, unit log, official archive manifest/binary and refusal log. Local donor-dependency scope only; hosted-check policy/native release remains open.; merged False; deployed False; live verified False.

### V02 — Joined contract and baseline local acceptance

**Owner:** unassigned. **State:** blocked. **Dependencies:** R06, N01, G02, D02, H01, P01.

**Remaining:** Run integration across all included features, 16 original behaviors and all supported paths. Reconcile failed receipts and schema dependencies; never sum overlapping tests as coverage.

**Acceptance:** Each original behavior has exact local source/evidence, truthful blocked external cases, reviewed integration and browser proof; live acceptance is L04.

**Source:** `docs/agent-run/BASELINE-BEHAVIORS.md`, `docs/agent-run/evidence/BASELINE-16-RELEASE-ACCEPTANCE.md`.

**Evidence:** implemented see evidence; tested Partial: ed6 historical fulltypes/715SystemPASS;2160 release rehearsalPASS;5fa signedResearch2PASS;c41 legacy729unitPASS5skip and9nativePASS. Fullunitf7RED remains recorded; final joined matrix pending.; independently reviewed pending exact joined source; merged False; deployed False; live verified False.

### L00 — Reconcile installed ledger and phased profile

**Owner:** Claude gatekeeper (2026-10-05): L00 = RELEASE-MIGRATION-ORDER-20261005 Phase A/S; V00/L01 = box-ci green + merge-if-green + deploy-main flag-off. **State:** in_progress. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Fresh production01:53UTC readback confirms six editor/activation RPC names and provisional ledger IDs absent. Actual-role restored-production-copy rehearsal, writer exclusion, phased profile application, current target recheck and final image/recovery qualification remain. Populated workflow/history prevents reverse; do not promise automatic schema/image downgrade. Old backup2db pins are stale; preserve unrun attempt. Research ledger/factory/readiness remain separate before activation.

**Acceptance:** Exact installation preconditions and safe disabled-code schema ordering, native forward/VERIFY/rollback/reapply; full plan independently audited.

**Source:** `scripts/qa/agent-run-release-profile.py`, `scripts/qa/agent-run-packet-rehearsal.py`.

**Evidence:** implemented Headless and ordinary editor/activation numbered packets composed; inactive expand order headless→editor→activation. Activation remains disabled.; tested Headless packet/readback2/2PASS atd7c; editor/activation canonicalpair1/1PASS at91e; postmergeda567 sourcehash validation all3profilesPASS; focused45PythonPASS. Disposable reducedschema does not qualify productionrestore.; independently reviewed Independent Sol source and composition audits clear for included headless/editor/activation packets; full live release audit pending.; merged False; deployed False; live verified False.

### L10 — Finish continuous admission and drain proof

**Owner:** superseded for this release (gatekeeper decision 2026-10-05): the normal platform release path replaces the isolated native rehearsal / standalone backup plan / custom live coordinator; not completion of the original acceptance rows. **State:** deferred. **Dependencies:** none for independent drafting; actual resource/authority gates still apply.

**Remaining:** Resume only with fresh exact identities after current owned shutdown. Complete five real app/proxy phases, PG/schema/PostgREST, operator/runner continuous admission and drain, cutoff and recovery; zero app phases completed in this window. Retain independently verified prerequisites as historical evidence, not live authority.

**Acceptance:** Actual isolated host/PostgREST lab, continuous hold/drain/recovery, old-worker and late-effects negatives; no unknown operation discarded.

**Source:** `scripts/qa/agent-run-release-host.py`, `scripts/qa/money-release-operator.py`.

**Evidence:** implemented Copied-disk resume adapter implemented; fresh VM/native source/images/network/common/probe build independently verified. Probe projection source staged only; first app packet pair local only. Zero app/PG or operator install/bind/caller/cutoff effects; fixture/common inputs were staged. Owner paused; final owned shutdown evidence in pause inventory.; tested Historical stopped donor generation: Actual isolated smoke and full guest readiness, exact Git/blob census, offline archive census, Docker install/readback, private daemon isolation/API/default-daemon/firewall checks, and source/input stages passed. Application/database/runner/operator/recovery tests remain pending. Actual private network and four-image load now independently passed; all four IDs inspected, zero containers, phase/current firewall unchanged. Fifth image independently passed; inventory exactly five full IDs, zero containers, firewall unchanged. Actual Traefik/Node tags and probe build/projection independently pass. Native daemon and fullVM shutdown independently passed; no app/PG/runner/operator effect was launched.; independently reviewed Historical stopped donor generation: Independent Sol: full guest8786853a, Gitfcc8c664, Docker344dd3c7, private daemon3b8cc009 + firewall843d4399, seed8d3e33b6, HBA31a6ead0, operator fixture426ae19c. These establish prerequisites only. Network0c1be2a9 and four-image8fa03f03 independently passed. Fifth image dcba8d2e and probe context edbe2242 independently passed. Tags3f755284/54bdf4bc, probea2e99832 and projectionc4178617. Native stop0e83c986 and VMstopf0235234; scoped immediate firewall equality, with earlier host Fail2ban set delta recorded.; merged False; deployed False; live verified False.

### V00 — Qualify the included inactive release profile

**Owner:** Claude gatekeeper (2026-10-05): L00 = RELEASE-MIGRATION-ORDER-20261005 Phase A/S; V00/L01 = box-ci green + merge-if-green + deploy-main flag-off. **State:** blocked. **Dependencies:** V01, L00, L10, L12.

**Remaining:** Application a9ab/PR6168 managed security/build independentlyPASS on recorded7c25/main9ee. Join final release source with actual native continuous exclusion, installed-role schema/profile and faithful recovery qualification. Preserve source-specific scopes; no release before remaining gates.

**Acceptance:** Exact included-source full checks, actual UI/native where relevant, profile-specific independent audit and tested recovery. No schema or safety gate is waived for phased release.

**Source:** `scripts/qa/agent-run-release-profile.py`, `docs/agent-run/EXECUTION-PATH-ACCEPTANCE.md`.

**Evidence:** implemented partial; tested aef5497 private schema-only canonical rehearsal independently PASS17 packets/51 results+catalog checks/9 baseline checks. Production-data restore and exact final-source qualification remain distinct.; independently reviewed Independent Sol expect f7a5cddf and canonical43eb18bc; sealed76members, terminalexit0, empty cgroup/private containers. Original a88d RED retained.; merged False; deployed False; live verified False.

### L11 — Qualify faithful backup and restored copy

**Owner:** superseded for this release (gatekeeper decision 2026-10-05): the normal platform release path replaces the isolated native rehearsal / standalone backup plan / custom live coordinator; not completion of the original acceptance rows. **State:** deferred. **Dependencies:** L00.

**Remaining:** Fresh capture25418/plan5ff14ca is preserved, expires2026-10-05T05:56:29Z, not run or approved. On resume recheck expiry/source/container/capacity; refresh if changed. Obtain this plan's specific shared-lock approval, run once and prove rows/ledger/roles/catalog fidelity. Full release independently requires continuous writer authority.

**Acceptance:** Fresh coherent rows/ledger/roles/catalog match, snapshot/lock cleanup and exact packet rehearsal; prior approval consumed. No lock/migration implied by this plan. Restored-copy migration/ACL rehearsal under the actual migration role joins L00/V00; synthetic superuser/NOLOGIN fixtures do not prove production authority.

**Source:** `scripts/qa/agent-run-production-backup.py`, `docs/agent-run/evidence/backup-prior-reconciliation-20260930/STAGING-AND-CAPTURE.md`.

**Evidence:** implemented Fresh exact-source capture and separately read-back plan25418 saved; completed independent launch/plan source review PASS_WITH_SCOPE. Specific owner approval absent; no lock/backup/migration/activation ran.; tested Root and independent Sol reviewed unchanged guards;26 focused tests pass. Consumed attempt6d79 refused before helper/archive, lock released. Fresh restore remains unproved.; independently reviewed Grok38 static49c5 binding PASS_WITH_SCOPE; root independently rehashed plan/launcher. Grok39 correctly distinguishes preflight READ ONLY from server policy. Host generation/capacity subsequently changed; no current release admission or restoration result.; merged False; deployed False; live verified False.

### L12 — Implement the qualified live release coordinator

**Owner:** superseded for this release (gatekeeper decision 2026-10-05): the normal platform release path replaces the isolated native rehearsal / standalone backup plan / custom live coordinator; not completion of the original acceptance rows. **State:** deferred. **Dependencies:** L00, L10.

**Remaining:** Reviewed operator lifecycle/recovery sources pushed4a2ec5a;36 local tests pass, no runtime effect. Complete actual prepare/install, runner/companions, seven-step cutoff, terminal/final-ACK recovery and cleanup. Resolve contender launch-receipt timing without delaying baseline; a missed overlap is unproven.

**Acceptance:** Native lost-ack/contender/stale-generation/stop/schema-COMMIT/launch/health tests and independent source audit. A running container or REST-only barrier cannot establish complete writer exclusion. Production use additionally requires fresh backup/profile/authorization.

**Source:** `scripts/qa/agent-run-release-profile.py:270`, `scripts/qa/agent-run-release-host.py:303`, `scripts/qa/agent-run-admission-barrier.py`, `scripts/qa/agent-run-live-coordinator.py`, `scripts/qa/test-agent-run-live-coordinator.py`, `scripts/qa/agent-run-live-journal.py`, `scripts/qa/test-agent-run-live-journal.py`.

**Evidence:** implemented Current2ff contains the composed native/operator callers. This window adds reviewed guest fixture, read-only catalog and actual prepare/install adapters; fixture staging is independently verified. No prepared bundle, installed operator or native cutoff acceptance yet.; tested child identity7/7, owner filesystem6/6, joined journal/port/host3/3 native;090 actual-role disposablePG6/6. Separate7015 cron distinct-process recovery4/4 independently PASS (orderly exit and SIGKILL, injected effect log), not real Docker/power loss. Fresh canonicalbcc0 joined Money preflight with actualPG17/090 passes1/1, zero skips; first ownership setup RED retained. No broad writer/ingress or live proof.; independently reviewed Independent exact7015 source and four process tests clear. Root+Sol conflict-free canonical projection verified; two extra canonical backup files match reviewed39f23. Native08aa proof carries four exact inputs only; staged7c full packet differs through cron aggregate and has no terminal result yet. Freshbcc0 33-blob packet and stage-only ownership repair reviewed; root+Sol verify3/3 terminal receipts, manifesta33f0b97. Older7c packet remains unrun and is not relabeled.; merged False; deployed False; live verified False.

### L01 — Deploy qualified inactive foundation

**Owner:** Claude gatekeeper (2026-10-05): L00 = RELEASE-MIGRATION-ORDER-20261005 Phase A/S; V00/L01 = box-ci green + merge-if-green + deploy-main flag-off. **State:** blocked. **Dependencies:** V00, L11.

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

Use root plus **up to three workers**, each with an isolated worktree or nonoverlapping owned files. Prefer the requested Sol model when available; otherwise record the actual model and preserve task-specific reviewer acceptance requirements. Package owner labels below preserve historical assignments; a new session must assign current workers explicitly and must not assume old agent IDs or processes still exist:

1. **Root integration owner:** maintain one candidate, review actual callers and dependencies, integrate only audited blocker fixes, keep the plan/handoff synchronized, and own final release decisions.
2. **Implementation worker:** finish current ingress/operator and real caller integration. Every component names its production caller, integration owner and true/false acceptance test. A tested composite with no production constructor remains incomplete.
3. **Qualification worker:** finish immutable whole-run terminal collection, exact-source browser/native/schema/build checks and resource/host prerequisites. It may prepare independent packets while a long run executes, but cannot mutate active inputs or cancel for unrelated changes.
4. **Independent trailing reviewer:** review exact source and receipt hashes, challenge environment/proof claims, exercise real failures/unknowns/recovery, and audit integration. Source approval is never promoted to native/live proof.

Shortest remaining path: preserve independently passed a9ab managed checks and exact tested source/merge provenance (f0da passes remain historical) → complete isolated native source/transport, app/PG/schema, continuous drain and recovery qualification → compose the actual production release operator and phased migration profile → qualified migrations/inactive deployment → approved provider qualification, activation, all16 behaviors/all supported callers live, monitoring and tested recovery. The old f74-only build instructions below are historical; do not launch them. New main changes alone do not justify restarting unaffected checks; only demonstrated blockers or final-source differences require scoped requalification.

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
git fetch origin refs/heads/codex/agent-run-release-composition-20261004:refs/remotes/origin/codex/agent-run-release-composition-20261004
git worktree add --detach ../supraos-agent-qualification a9ab52fe956e134b667d414a5b47f58cc5741e6b
git -C ../supraos-agent-qualification rev-parse HEAD
```

For the separately tested main-merge repair, current native source and portable controllers, fetch the corresponding explicit refs before creating inspection worktrees:

```sh
git fetch origin refs/heads/codex/agent-run-main-successor-20261004-1430:refs/remotes/origin/codex/agent-run-main-successor-20261004-1430
git fetch origin refs/heads/feat/agent-run-full-native-guest-20261005:refs/remotes/origin/feat/agent-run-full-native-guest-20261005
git fetch origin refs/heads/feat/agent-run-isolated-native-guest-smoke-20261005:refs/remotes/origin/feat/agent-run-isolated-native-guest-smoke-20261005
git fetch origin refs/heads/evidence/native-guest-tooling-20261005:refs/remotes/origin/evidence/native-guest-tooling-20261005
```

Pin the source commit from the table, not an assumed latest branch tip. Evidence-only successor commits may follow tested source without changing runtime files. Sparse `evidence/*` branches preserve files and receipts, not necessarily a complete runnable application. Compare their manifests before composition.

The qualification checkout intentionally pins the named current application candidate; check the latest published source table before creating it. Compare with the lane pin in this document. A detached inspection tree is not permission to bypass outstanding gates or overwrite another worker's source. Create an explicitly owned implementation branch when further changes are needed.

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

Native lanes need PostgreSQL 17 binaries (`PG_BIN` containing `initdb`, `pg_ctl`, `psql`) and the exact PostgREST binary pinned by the lane (`TASK_POSTGREST_BIN`); do not silently replace a retained PostgREST13 fixture with14.18. Some fixtures also require `SUPRAOS_TEST_LOCAL_POSTGRES=1`. Read each lane's runner/config; use only an owned disposable database/socket, never a production DSN. The staged host runner/source/receipt hashes are in the host queue checkpoint. Historical packet admission cutoffs belong to their original attempts and are not current authority, whether this coordination session is active or paused. After an explicit resume, establish a fresh bounded window, recheck source/HEAD, resource floors and scratch ownership, and retain new evidence under a distinct attempt path; never overwrite a prior receipt or reuse an expired production plan. Docker-backed tests additionally need the approved daemon/image and their own disk floor.

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

Review all diffs and public content. Commit the private documents to the canonical coordination branch using an explicit non-force refspec. In a separately authenticated checkout of `jtobkin/supraos-agent-completion-handoff`, inspect existing status, copy only the four reviewed generated files, commit and push normally. Preserve others' edits. Finally fetch the public files without authentication and compare bytes/commit pins, then record the private/public checkpoint pair. This window records that pair in `docs/agent-run/evidence/resume-isolation-20261004/final-pause/publication-receipt.json` after publication; the receipt commit follows the document commit without changing the application candidate. The original workstation's QA publisher is a historical convenience, not a dependency for a new account. Public documentation access does not grant private source or infrastructure access.

## What Finished means, end to end

Every required implementation is integrated into the actual deployed source; exact-source tests and independent reviews pass; correct schema/graph versions are installed in the prescribed order; eligible capabilities are activated with real per-owner readiness; and all applicable execution paths are independently exercised live after deployment. Monitoring, retained recovery and faithful backup restoration work. No required implementation, release or baseline gate remains open.

The 16 original behaviors are: quiet morning; personal reply style; visible shopping; an approved real call; appropriate initiative; private in-chat computer handoff; one useful loose end; mail follow-up with ignored-thread suppression; friend sharing with both consents; an actual agent mailbox; exact authorized payment; trustworthy marks linked to durable evidence; useful bounded personal recall; honest stops; attention protection; and tone/length informed by real context. The baseline evidence matrix defines exact proofs.

Across chatbox, Telegram, background, delegation and System Workflows, demonstrate current scoped preferences, bounded context, history-before-state, fresh permission-before-effect and truthful outcomes. Lost acknowledgements, restarts, retries, absent providers and revoked consent must not invent success or duplicate effects. A partial inactive release is a milestone, not project completion.

## Suggested prompt for the next session

> Resume the SupraOS Universal Agent project from this public handoff and its linked private checklist. Assume no local history, credentials or repository access. Obtain access through normal sign-in, fetch the canonical coordination branch and the explicitly named current application/repair branches, inspect status and running jobs before editing, and read all required boot documents. Preserve the complete scope and62-task ledger. Use root plus up to three independent lanes for integrated implementation, release prerequisites, and independent review. Prefer requested Sol workers when available; record actual reviewer identity and preserve original task-specific acceptance requirements. Follow the current dependency order; preserve failed evidence, resource floors and original-attempt recovery. Keep code, tests, audit, merge, deploy, activation and live acceptance separate. Do not claim completion until all16 baselines and all supported paths are live-verified with tested recovery. Report actual current state and any concrete external access/approval gap, then execute the shortest path to a usable release.

## Historical five-hour pause and process ownership

At the prior checkpoint, implementation was paused for the owner-requested14:13:30UTC session handoff. The final two-hour pause at the top supersedes this process-status description. At that historical pause, new host effects were stopped and only publication/link verification remained. Use the newest terminal census at the top when resuming, never an old ready receipt.

R5 own-QA stop independently PASS8a99891d: unit PID0; own daemon/containerd PIDs, runtime/socket and active phase clients absent; zero containers observed before stop; shared daemon generation and full firewall structure unchanged. Six private images were observed before stop; API unavailable afterward. All private data, receipts and UNKNOWN intents retained. No new host effects admitted. Managed application checks are terminal success. First app build-traefik remains UNKNOWN_NO_REPLAY with confirmed untagged-base registry-resolution failure. No subsequent app/PG/runner/Money effects, production backup, shared lock, migration, deployment or activation ran. Sol B and C have completed their portable handoffs; Sol A has independently verified the host stop and reviews the final evidence index. The diagnostics source has separate Sol/Grok53 review. Original3c442 host source was never replaced by the diagnostic successor.


Grok workers are bounded read-only reviews. Current process manifests, independent stop/census and final publication receipts take precedence over older activity counts. Do not infer old agents or CLI sessions still exist on a new computer.
