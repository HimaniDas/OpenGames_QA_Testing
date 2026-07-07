# Requirements Traceability Matrix (RTM)

Maps the client's stated testing requirements to the sections/test case IDs in [Test_Plan.md](Test_Plan.md) that cover them, so coverage can be verified at a glance and gaps are visible instead of assumed.

| # | Client Requirement | Covered By (Test Plan) | Coverage Notes |
|---|---|---|---|
| 1 | Android app testing | Sections 5, 6, 7, 8, 9, 10, 17 (all Android-side smoke/account/settings/bot/regression/performance cases) | Primary platform, covered across nearly every section |
| 2 | Browser testing | Section 15 (HM-WEB-01–05), HM-SMK-02 | Includes mobile-web layout and direct game links |
| 3 | Android vs Android multiplayer | HM-ONQ-01, private match section 12 (played device-to-device) | |
| 4 | Android vs Browser multiplayer | HM-ONQ-02, HM-WEB-04, HM-MOR-03 | Cross-platform parity is a named focus area |
| 5 | Quick Match | Section 11 (HM-ONQ-01–07) | |
| 6 | Private Match | Section 12 (HM-PRI-01–06) | |
| 7 | Ladder / League mode | Section 13 (HM-LAD-01–13) | Flagged in Test_Plan.md as one of the most important areas |
| 8 | Bot behaviour | Section 8 (HM-BOT-01–05), HM-CHK-01/02/03, HM-MOR-01/02/03 | Covers freezing, illegal/off-turn moves, difficulty, king promotion, mill logic |
| 9 | Gameplay bugs | Sections 9, 10 (Checkers & Nine Men's Morris regression), plus any bug surfaced during Sections 5–15 | Not a single section — tracked via bug-reports/Bug_Reports.md whenever found |
| 10 | UI/UX issues | Section 16 (HM-UX-01–08) | Also captured ad hoc in notes/Exploratory_Notes.md |
| 11 | Stability after restart | HM-SET-01 (setting persistence), HM-PERF-03 (background/resume), HM-LAD-12 (restart after ranked result) | See also expanded edge cases in notes/Exploratory_Notes.md |
| 12 | Reconnect behaviour | HM-ONQ-07 (reconnect), HM-PERF-04 (network interruption) | See also expanded edge cases in notes/Exploratory_Notes.md |
| 13 | Detailed bug reports | Process: templates/Bug_Report_Template.md → bug-reports/Bug_Reports.md | Every confirmed bug uses the full template, no shortcuts |
| 14 | Professional PDF report | Process: templates/Test_Report_Template.md → reports/ (Markdown) → exported to PDF | See README "Client Deliverables" section for the export step |

## Gaps / Watch Items

- Requirement 9 ("gameplay bugs") and 10 ("UI/UX issues") are cross-cutting — they aren't satisfied by ticking one section, they depend on bugs actually being found and logged during execution of every other section. Tracked via the bug log, not a fixed ID range.
- Requirements 11 and 12 (restart/reconnect) have baseline coverage in the formal test plan but are worth deeper exploratory testing given the client called them out explicitly — see the "Stability & Reconnect Edge Cases" section in notes/Exploratory_Notes.md.
