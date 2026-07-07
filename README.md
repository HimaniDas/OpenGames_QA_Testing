# OpenGames — Manual QA Testing Project

This repository documents a real-world manual QA engagement for **OpenGames**, a cross-platform board games app (Android + Web) offering classic games such as Checkers, Nine Men's Morris, Chess, Reversi, Connect Four, and Tic-Tac-Toe, with offline bots and online multiplayer (Quick Match, Private Match, League).

It is maintained by **Himani**, acting as the manual QA tester for the client, testing on Android (Realme C11, Redmi Note 7 Pro) and at [opengames.vip](https://opengames.vip) (Chrome, Firefox).

## What this project demonstrates

- Writing and following a structured **test plan** covering smoke, functional, regression, integration (online multiplayer), and non-functional (performance, UX) testing
- **Cross-platform testing** (Android vs. Web) and multi-device/multi-account online testing
- **Regression testing** on previously buggy areas (Checkers undo/multi-capture, Nine Men's Morris mill logic)
- Translating and consolidating raw bilingual (Bangla/English) testing notes into structured findings
- Matching every finding against screenshot and video evidence, and merging duplicate reports of the same root cause across devices/browsers into single, traceable bugs
- Writing a **professional, client-ready bug report** with realistic Severity/Priority triage (not everything marked critical)
- Producing a final report suitable for direct delivery to the client, in both Word and PDF form

## Repository Structure

```
├── README.md                              # This file
├── docs/
│   ├── Test_Plan.md                       # Master test plan: 78 test cases across 13 functional areas
│   └── Requirements_Traceability_Matrix.md   # Maps client requirements to test plan coverage
├── bug-reports/
│   └── OpenGames_Final_Bug_Report.pdf     # Client-facing PDF export of the final bug report
├── reports/
│   ├── README.md
│   └── OpenGames_Final_Bug_Report_updated - Copy.docx  # Master Word source of the final bug report
├── screenshots/                           # Evidence referenced by bug ID throughout the final report
├── videos/                                # Screen recordings referenced by bug ID throughout the final report
└── notes/
    └── Exploratory_Notes.md               # Exploratory testing ideas and observations outside the formal test plan
```

The Word file in `reports/` is the editable master; the PDF in `bug-reports/` is the client-facing export of that same, finalized report — both reflect the same content.

## Testing Approach

1. **Smoke test** the app on Android and Web to confirm it's stable enough to test further.
2. **Functional and regression testing** on single-device flows: account/login, settings, offline bots, Checkers and Nine Men's Morris regressions.
3. **Integration testing** across devices: Online Quick Match, Private Match, Android-vs-Web parity.
4. **League/Ladder testing** — verified as its own priority area, since correct scoring, ranking, and progression are critical to the product.
5. **Non-functional testing**: UX/usability, performance, and stability over extended sessions.
6. Findings from both Android and Web sessions, and from raw bilingual tester notes, were consolidated and cross-checked against 24 screenshots and 30 screen recordings before merging duplicate reports into a final, client-ready bug list.

## Client Requirements

This engagement was scoped directly against the client's stated requirements: Android app testing, browser testing, Android-vs-Android multiplayer, Android-vs-Browser multiplayer, Quick Match, Private Match, League mode, bot behaviour, gameplay bugs, UI/UX issues, stability after restart, reconnect behaviour, detailed bug reports, and a professional PDF report. See [docs/Requirements_Traceability_Matrix.md](docs/Requirements_Traceability_Matrix.md) for exactly which test cases satisfy each requirement.

## Client Deliverables

- **Final Bug Report** — [reports/OpenGames_Final_Bug_Report_updated - Copy.docx](<reports/OpenGames_Final_Bug_Report_updated - Copy.docx>) (master) and [bug-reports/OpenGames_Final_Bug_Report.pdf](bug-reports/OpenGames_Final_Bug_Report.pdf) (client-facing export). Includes a Test Environment section, per-bug Feature/Environment/Preconditions/Steps/Expected/Actual fields, Severity and Priority, and matched screenshot/video evidence for every bug where evidence exists.
- **Evidence** — every bug in the report that has supporting evidence links back to specific files in [screenshots/](screenshots/) and [videos/](videos/).

## Priority Levels

| Priority | Meaning |
|---|---|
| P0 | Critical — crash, frozen app, online mode unusable, match cannot continue |
| P1 | Serious — wrong winner/turn, bot stuck, leaderboard/points wrong, broken account flow |
| P2 | Medium — confusing UX, layout issue, slow response, missing feedback |
| P3 | Minor — cosmetic issue, small visual polish, typo |

See [docs/Test_Plan.md](docs/Test_Plan.md) for the full test plan.
