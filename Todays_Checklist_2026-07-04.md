# Today's Testing Checklist — 2026-07-04

Tester: Himani
Source: opengames-himani-user-testcases-en.md
Scope for today: Phase 1 of the Recommended Minimum Test Run (Section 18) — the tests that need only one device/one account and unlock everything else.

Check each box only after you have actually run the step and confirmed the result with me. I will not mark anything Passed on your behalf.

## Phase 1a — Quick Smoke Test (must pass before anything else)

- [ ] HM-SMK-01 (P0) — Install/open Android app → opens without crash
- [ ] HM-SMK-02 (P0) — Open https://opengames.vip → game selection loads
- [ ] HM-SMK-03 (P0) — Open each game, go back → no crash, back nav works
- [ ] HM-SMK-04 (P0) — Start one bot match, any game → bot moves, game stays playable
- [ ] HM-SMK-05 (P0) — Open online options in ≥2 games → Quick Match / Private / League visible or login prompt is clear

## Phase 1b — Account and Login

- [ ] HM-ACC-01 (P0) — Register/login Account A → profile/level/info correct
- [ ] HM-ACC-02 (P1) — Logout A, login B → no data bleed between accounts
- [ ] HM-ACC-03 (P1) — Logout, start offline bot game → works without login
- [ ] HM-ACC-04 (P1) — Logged out, try League/Ladder or online → clear login prompt, not stuck
- [ ] HM-ACC-05 (P2) — Wrong login data / interrupted login → error is understandable, app usable

## Phase 1c — Settings and First User Experience

- [ ] HM-SET-01 (P1) — Change bot level, close/reopen app → level still selected
- [ ] HM-SET-02 (P1) — Different bot levels in two games → each game keeps its own
- [ ] HM-SET-03 (P1) — Several new local games, default settings → starting player varies
- [ ] HM-SET-04 (P1) — Set P1 starts / P2 starts / Random → each respected
- [ ] HM-SET-05 (P2) — Switch app language → text updates consistently, no missing labels
- [ ] HM-SET-06 (P2) — Try several themes → UI stays readable, pieces visible

## Phase 1d — Offline Bot Testing (start of regression coverage)

Games to cover: Checkers, Nine Men's Morris, Chess, and one of Reversi/Connect Four/Tic-Tac-Toe.

- [ ] HM-BOT-01 (P0) — 10+ turns vs bot → bot always responds or gives clear feedback
- [ ] HM-BOT-02 (P0) — Watch bot after your move / after undo/reset → no double move, no off-turn move
- [ ] HM-BOT-03 (P1) — Try low and high bot levels → difficulty feels right, no freeze
- [ ] HM-BOT-04 (P1) — Bot-vs-bot for 30-60s in one game → no crash/freeze
- [ ] HM-BOT-05 (P1) — Start new game during/after bot match → board/turn reset correctly

---

## Not scheduled for today (needs two devices/accounts or longer session — see full tracker)

- Section 9 Checkers Regression (HM-CHK-01–05)
- Section 10 Nine Men's Morris Regression (HM-MOR-01–05)
- Section 11 Online Quick Match (HM-ONQ-01–07)
- Section 12 Private Match (HM-PRI-01–06)
- Section 13 Ladder/League (HM-LAD-01–13)
- Section 14 Direct Challenge (HM-CHL-01–04)
- Section 15 Web Version (HM-WEB-01–05)
- Section 16 UX (HM-UX-01–08)
- Section 17 Performance (HM-PERF-01–04)

All of these remain listed in `Test_Execution_Tracker.md` as Not Executed and are not being skipped — they are queued for the next sessions once a second device/account is available and once today's foundation passes.
