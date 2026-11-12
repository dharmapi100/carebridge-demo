# CareBridge — recorded demo

**This is a recorded demo, not a live service.** It is a single static page showing the CareBridge
interface with its responses captured from a real local run and baked in. There is no server, no
database, and no network activity of any kind.

Live: **https://dharmapi100.github.io/carebridge-demo/**

---

## What CareBridge is

Labor-compliance and payroll infrastructure for South Korea's institutional elder-care market.
It encodes Korean labour law into deterministic software: statutory severance (퇴직금), the 4 Major
Public Insurances (4대보험), the monthly wage-income-tax withholding table (근로소득 간이세액표,
소득세법 시행령 별표 2), visa-category eligibility, and nursing-hospital subsidy-eligibility scoring.

It is a B2B compliance product, sold to facilities and agencies that already hold licensing
standing. It is **not** a consumer caregiver-matching app, and it is **not** an employer-of-record or
visa-sponsor service.

## What you are looking at

Every button works and every card returns a real result — computed by the engine, recorded, and
replayed here. Press **감사 실행 / Run audit** or the other numbered panels to see the flows.

The technical claims the interface makes are test-backed in the private repository:

- **32 test suites, all passing**, including the withholding table checked cell-for-cell against the
  gazetted 별표 2 PDF.
- **Hash-chained audit log.** Every record links to the one before it, so a record *deleted* from the
  middle of the log breaks the chain. Per-record AES-GCM authentication alone detects modification
  but not removal.
- **Key-versioned encryption.** Every key ever generated is retained and addressable by a
  deterministic id, so rotating a key never orphans earlier records.

## What this demo is not

- **Not a live system.** Nothing here persists, computes, or accepts input. Typing in a field changes
  nothing — the responses are fixed.
- **Not connected to any Korean government system.** Visa checks are a local approved-list
  comparison, not a Ministry of Justice query.
- **Not legal advice.** The engine returns statutory determinations; it does not practise law.
- **No customers.** This is a pre-pilot product. The market thesis is unvalidated, and the honest
  position is that it has not yet been sold to anyone.

## Known limits, stated rather than hidden

- **No database.** State is file-backed JSON, regenerated on first run.
- **Authentication is a single shared token**, not per-user accounts. It demonstrates; it is not yet
  deployable to a hospital.
- **Audit-chain truncation is not fully provable.** The chain proves continuity of the middle. Proving
  the *tail* was not truncated needs an anchor the log's writer cannot reach, which does not exist
  yet — a weekly checkpoint publishes the chain head to a chat log, which is a weak substitute.

---

Source is private. This page contains no source code and no personal data.
