# Exploratory Testing Notes

Freeform observations, ideas, and questions that fall outside the formal test cases in [docs/Test_Plan.md](../docs/Test_Plan.md). Anything that turns into a confirmed bug gets promoted to [bug-reports/Bug_Reports.md](../bug-reports/Bug_Reports.md) using the [Bug Report Template](../templates/Bug_Report_Template.md).

## Ideas to explore

- Rapid tapping/spamming moves or buttons (double-submit protection)
- Rotating device orientation mid-game (Android)
- Backgrounding the app mid-matchmaking or mid-move
- Switching network (Wi-Fi to mobile data) during an online match
- Extremely long games (many turns) for performance drift
- Simultaneous actions from both players at the same instant in online play
- Very long or unusual display names/usernames in leaderboard and challenge UI

## Stability & Reconnect Edge Cases

Called out explicitly by the client (see [docs/Requirements_Traceability_Matrix.md](../docs/Requirements_Traceability_Matrix.md) items 11–12) — worth going beyond the baseline test plan coverage (HM-SET-01, HM-PERF-03/04, HM-LAD-12, HM-ONQ-07):

- Force-kill (swipe away, not just background) the Android app mid-move in an online match, then relaunch — does the match resume, show a clear disconnect state, or corrupt?
- Force-kill during matchmaking/waiting screen (Quick Match and Private Match) — does the app recover to a sane state on relaunch, or get stuck "still searching"?
- Kill and relaunch mid-bot-turn (bot is "thinking") — does the bot move get lost, duplicated, or does the game hang?
- Kill and relaunch mid-Ladder/League match specifically — does it count as a loss/abandon, stay resumable, or leave stats in an inconsistent state?
- Toggle Airplane Mode on/off mid-match instead of a clean app kill (tests reconnect logic, not just cold start)
- Let the connection drop and stay dropped for an extended period (1-2 minutes) before reconnecting — does the app time out gracefully or hang indefinitely?
- Background the app (not kill) during reconnect countdown/waiting UI — confirm state on foreground return
- Restart the device entirely (not just the app) mid-match
- Web: refresh the browser tab mid-match (not just "non-critical state" as in HM-WEB-05) and mid-reconnect
- Two rapid reconnect attempts in a row (flaky network simulation) — confirm no duplicate session/match state

## Session notes

(Append dated observations below as testing progresses.)
