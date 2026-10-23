# ClickDungeon Documentation Index

Reference guide to the project documentation currently maintained in this repository.

**Last Updated**: 2026-05-26
**Current Version**: 1.0.0 | **Status**: launch hardening; Android lane passed in latest documented local audit; backend check/test/audit passes after targeted non-force dependency overrides; local Firebase Android config present; physical-device smoke evidence, Gate 4 screenshots/hosting, Play Console, Firebase console/event verification, and connected-service backend enablement pending

---

## Start Here

| Document | Purpose |
|----------|---------|
| [README.md](../README.md) | Project overview, features, and current status |
| [LAUNCH_PLAN.md](LAUNCH_PLAN.md) | Gate-by-gate v1 launch status and next steps |
| [AUDIT_2026-05-04.md](AUDIT_2026-05-04.md) | May 4 launch audit record with current-state notes and verification commands |
| [GATE4_CHECKLIST.md](GATE4_CHECKLIST.md) | Store asset/legal checklist and remaining external blockers |
| [ROADMAP.md](ROADMAP.md) | Verified feature coverage, gaps, and dependency-ordered phases |
| [NEXT_PHASE_PLAN.md](NEXT_PHASE_PLAN.md) | Current execution order across Track 1-4 work |
| [DEVELOPER_SETUP.md](DEVELOPER_SETUP.md) | Local environment setup, build, and test commands |

---

## Architecture & Systems

| Document | Purpose |
|----------|---------|
| [ANIMATION_ARCHITECTURE.md](ANIMATION_ARCHITECTURE.md) | Sprite-sheet and animation-state notes |
| [ASSET_IMPORT_GUIDE.md](ASSET_IMPORT_GUIDE.md) | Import workflow for art/audio assets |
| [PERFORMANCE_PLAN.md](PERFORMANCE_PLAN.md) | Performance targets and optimization plan |
| [TELEMETRY_EVENTS.md](TELEMETRY_EVENTS.md) | Event naming and telemetry schema |
| [SECURITY.md](../SECURITY.md) | Save security, encryption, and integrity notes |

---

## Testing & QA

| Document | Purpose |
|----------|---------|
| [TEST_GAP_BACKLOG.md](TEST_GAP_BACKLOG.md) | Remaining automated-test gaps |
| [TRACK1_TRIAGE.md](TRACK1_TRIAGE.md) | Track 1 harness triage checklist and commands |
| [qa/PHYSICAL_DEVICE_SMOKE.md](qa/PHYSICAL_DEVICE_SMOKE.md) | Physical-device smoke workflow and evidence rules |
| [qa/smoke_evidence/README.md](qa/smoke_evidence/README.md) | Blank physical-device smoke evidence template; not a completed run |
| [`scripts/release_smoke_check.ps1`](../scripts/release_smoke_check.ps1) | PowerShell helper to install, clear data, launch, and prefill smoke evidence |
| [`scripts/capture_play_screenshots.ps1`](../scripts/capture_play_screenshots.ps1) | PowerShell helper to validate the capture plan and capture Play screenshots from a connected phone |
| [`scripts/prepare_store_assets.ps1`](../scripts/prepare_store_assets.ps1) | Read-only PowerShell helper to validate required Play assets and captured screenshot metadata with repository path guards |
| [`scripts/run_online_tests.ps1`](../scripts/run_online_tests.ps1) | PowerShell helper to run `:app:testDebugUnitTest` and collect reports |

> `app/src/online/java` is currently compiled into the standard unit-test source set, so online smoke tests run through `:app:testDebugUnitTest`.

---

## Connected Services & Release Prep

| Document | Purpose |
|----------|---------|
| [FIREBASE_SETUP.md](FIREBASE_SETUP.md) | Current Firebase / Play provisioning steps for Track 2 |
| [CI_SECRETS.md](CI_SECRETS.md) | Secure handling of `google-services.json` and Play service-account keys in CI |
| [BACKEND_DEPENDENCY_AUDIT_DECISION.md](BACKEND_DEPENDENCY_AUDIT_DECISION.md) | Backend Functions audit remediation decision and follow-up policy |
| [`track-2-firebase-play.md`](../.github/ISSUE_TEMPLATE/track-2-firebase-play.md) | Actionable GitHub issue template for Track 2 rollout work |

---

## Archived Docs

| Document | Status | Note |
|----------|--------|------|
| [archives/BUGS_V0.2_OBSOLETE.md](archives/BUGS_V0.2_OBSOLETE.md) | Archived | Historical v0.2 bug list |

---

## Documentation Status

- This index references only documentation files that are present in the repository.
- The primary planning docs are `README.md`, `LAUNCH_PLAN.md`, `ROADMAP.md`, and `NEXT_PHASE_PLAN.md`.
- Track 1 Android verification passed as of 2026-05-20: debug APK builds, `:app:testDebugUnitTest` passes, `:app:lintDebug` passes, `:app:bundleRelease` passes, and `:app:build` passes.
- Backend dependency audit passes as of 2026-05-26: raw `npm audit --omit=dev` and `npm run audit:known-exception` report zero production vulnerabilities after targeted `http-proxy-agent`, `qs`, and `uuid` overrides.
- Backend Functions currently expose the tested `health` endpoint plus safe-by-default `verifyPurchase`, `syncCloudSave`, and `leaderboard` seams; these validate request metadata but do not grant purchases, store cloud saves, or store/return leaderboard scores.
- Physical-device smoke evidence remains pending until a completed device/date-specific run file exists in `docs/qa/smoke_evidence/`; the directory README is only a template.
- Gate 4 is blocked only by external phone screenshots in `docs/screenshots/output/`, hosted privacy URL, and Play listing URL entry.
- Gate 5 and Gate 6 are now primarily external Console/Firebase verification work; in-repo scaffolding and local Android config are present.

When adding a new documentation file, update this index at the same time so links remain accurate.

## License

**License:** These original ClickDungeon planning and policy documents are proprietary commercial materials, **not open source**. Redistribution, modification, and commercial use require written permission from the owner. See [LICENSE](LICENSE).
