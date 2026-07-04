# OpenGames User Testing Guide for Himani

Date: 2026-06-23
Tester: Himani
App: OpenGames - Board Games
Platforms to test: Android app, Web browser version

## 1. Testing Goal

The app has already been tested by the developer for basic game rules and basic actions such as placing pieces, selecting fields, and making normal moves. You do not need to spend most of your time re-testing only the simplest moves.

Please focus on real user experience, online multiplayer, bots, edge cases, settings, account flows, and whether anything feels confusing, slow, broken, unfair, or unfinished.

The most valuable feedback is:

- Anything that crashes, freezes, hangs, or blocks progress.
- Any online multiplayer flow that does not work between two devices.
- Any Ladder/League issue where a player cannot progress, level up, gain points, lose points correctly, or see updated ranking/stats.
- Any bot that gets stuck, makes illegal moves, becomes too slow, or plays at the wrong time.
- Any issue where undo/back/reset leaves the game in a broken state.
- Any confusing screen, unclear message, bad layout, missing feedback, or comfort/usability problem.
- Any difference between Android and Web behavior.

## 2. Important Notes for the Tester

- Basic piece placement and normal move rules have already been tested.
- Please still report rule problems if you notice them naturally.
- Do not assume a bug is too small. UX confusion is also useful feedback.
- Please record short videos for online, bot, undo, crash, or freeze issues.
- Please actively note comfort improvements, for example fewer taps, clearer labels, better waiting/loading feedback, or screens that should explain the next action better.
- For every bug, write the exact game, mode, device, and steps.

## 3. Test Environment

Please test with as many of these as possible:

| Environment | Required? | Purpose |
|---|---:|---|
| Android phone with the latest app build | Yes | Main native app test. |
| Second Android phone or tablet | Strongly recommended | Android-vs-Android multiplayer. |
| Web version in Chrome/Edge | Yes | Android-vs-Web multiplayer and browser UI. |
| Two user accounts | Yes | Online matches, League/Ladder, stats. |
| Stable Wi-Fi | Yes | Normal online behavior. |
| Brief network interruption | Optional | Disconnect/reconnect behavior. |

Web URL:

```text
https://opengames.vip
```

## 4. Priority Levels

| Priority | Meaning |
|---|---|
| P0 | Critical: crash, frozen app, online mode unusable, match cannot continue. |
| P1 | Serious: wrong winner, wrong turn, bot stuck, leaderboard/points wrong, broken account flow. |
| P2 | Medium: confusing UX, layout issue, slow response, bad text, missing feedback. |
| P3 | Minor: cosmetic issue, small visual polish, typo. |

## 5. Quick Smoke Test

| ID | Priority | Area | Steps | Expected Result |
|---|---|---|---|---|
| HM-SMK-01 | P0 | Android launch | Install/open the Android app. | App opens without crash. |
| HM-SMK-02 | P0 | Web launch | Open `https://opengames.vip`. | Web app loads and shows game selection. |
| HM-SMK-03 | P0 | Game selection | Open each game and go back. | No crash, back navigation works. |
| HM-SMK-04 | P0 | Offline bot | Start one bot match in any game. | Bot makes a move and the game remains playable. |
| HM-SMK-05 | P0 | Online menu | Open online options in at least two games. | Quick Match, Private Match, and League/Ladder are visible or login is requested clearly. |

## 6. Account and Login Tests

| ID | Priority | Test Case | Steps | Expected Result |
|---|---|---|---|---|
| HM-ACC-01 | P0 | Create/login account | Register or log in with Account A. | User profile, level, or account info appears correctly. |
| HM-ACC-02 | P1 | Logout/login switch | Log out Account A, then log in Account B. | No data from Account A appears under Account B. |
| HM-ACC-03 | P1 | Guest offline play | Log out and start an offline bot game. | Offline play works without login. |
| HM-ACC-04 | P1 | Online requires account | While logged out, try League/Ladder or online features. | App clearly asks for login and does not get stuck. |
| HM-ACC-05 | P2 | Error messages | Enter wrong login data or interrupt login. | Error message is understandable and app remains usable. |

## 7. Settings and First User Experience

| ID | Priority | Test Case | Steps | Expected Result |
|---|---|---|---|---|
| HM-SET-01 | P1 | Bot level is remembered | Change bot level in one game, close/reopen app, return to same game. | The selected bot level is still selected. |
| HM-SET-02 | P1 | Bot level per game | Set different bot levels in two different games. | Each game keeps its own setting. |
| HM-SET-03 | P1 | Random starting player | Start several new local games with default settings. | Starting player varies when random is selected. |
| HM-SET-04 | P1 | Starting player setting | In local bot game, set Player 1 starts, Player 2 starts, Random. | Selected starting option is respected. |
| HM-SET-05 | P2 | Language switch | Switch app language and inspect game screens. | Text updates consistently; no missing labels. |
| HM-SET-06 | P2 | Theme switch | Try several themes. | UI remains readable; pieces are still easy to see. |

## 8. Offline Bot Testing

Please test at least these games against bots:

- Checkers
- Nine Men's Morris
- Chess
- One quick game from Reversi, Connect Four, or Tic-Tac-Toe

| ID | Priority | Test Case | Steps | Expected Result |
|---|---|---|---|---|
| HM-BOT-01 | P0 | Bot does not freeze | Play at least 10 turns against a bot. | Bot always responds or game gives clear feedback. |
| HM-BOT-02 | P0 | Bot moves only on its turn | Watch bot after your move and after undo/reset. | Bot does not move twice unexpectedly and does not move on your turn. |
| HM-BOT-03 | P1 | Bot difficulty feels reasonable | Try low and high levels in the same game. | Lower level feels easier; higher level does not freeze or take too long. |
| HM-BOT-04 | P1 | Bot vs bot stability | Start bot-vs-bot in one game and watch for 30-60 seconds. | Game continues without crash or frozen state. |
| HM-BOT-05 | P1 | New game after bot match | During/after bot game, start new game. | Board and turn state reset correctly. |

## 9. Checkers Regression Tests

These are important because previous issues were found in Checkers.

| ID | Priority | Test Case | Steps | Expected Result |
|---|---|---|---|---|
| HM-CHK-01 | P0 | Undo returns one full round | Play against bot, make a move, let bot move, press undo. | Both your move and bot move are reverted; it is your turn again. |
| HM-CHK-02 | P0 | Undo after multi-capture | Create or wait for a bot multi-capture, then press undo. | State remains consistent; game does not hang; it becomes your turn. |
| HM-CHK-03 | P0 | Bot king promotion | Let bot reach the opposite side, especially corner if possible. | Bot piece becomes king and game does not crash. |
| HM-CHK-04 | P1 | Continue after undo | After undo, continue playing several turns. | Bot continues normally; no stuck turn. |
| HM-CHK-05 | P1 | Reset/back during bot turn | Press reset/back while bot is thinking. | No crash; no delayed bot move corrupts the new game. |

## 10. Nine Men's Morris Regression Tests

These are important because Web and Android should both use the trained/native engine behavior.

| ID | Priority | Test Case | Steps | Expected Result |
|---|---|---|---|---|
| HM-MOR-01 | P0 | Bot forms mill and removes stone | Play against bot until bot forms a mill. | Bot removes a legal opponent stone and game continues. |
| HM-MOR-02 | P1 | Bot performance | Play against medium/high bot level. | Bot does not freeze or take unreasonably long. |
| HM-MOR-03 | P1 | Android vs Web engine feel | Play Morris bot on Android and Web. | Both work; Web bot does not fail to move. |
| HM-MOR-04 | P1 | Undo after mill/removal | Form a mill, remove a stone, then use undo if available. | State remains consistent; no missing pieces or wrong turn. |
| HM-MOR-05 | P2 | Clear removal UI | When a mill is formed, inspect the UI. | It is clear which stones can be removed. |

## 11. Online Quick Match Tests

Run these with two accounts. Ideally test Android-vs-Android and Android-vs-Web.

| ID | Priority | Test Case | Steps | Expected Result |
|---|---|---|---|---|
| HM-ONQ-01 | P0 | Quick Match Android-vs-Android | Start Quick Match on two Android devices. | Both users enter the same match. |
| HM-ONQ-02 | P0 | Quick Match Android-vs-Web | Start Quick Match on Android and Web. | Both users enter the same match. |
| HM-ONQ-03 | P0 | Move synchronization | Make moves on both sides. | Moves appear quickly and correctly on the other device. |
| HM-ONQ-04 | P0 | Wrong player cannot move | Try to move from the device that is not on turn. | Move is blocked. |
| HM-ONQ-05 | P1 | Finish online match | Finish a short online game. | Both devices show the same winner/draw. |
| HM-ONQ-06 | P1 | Leave match | One player leaves the game. | Other player gets clear status; app does not hang. |
| HM-ONQ-07 | P1 | Reconnect | Refresh Web or background Android briefly. | Game either reconnects cleanly or shows clear disconnect state. |

## 12. Private Match Tests

| ID | Priority | Test Case | Steps | Expected Result |
|---|---|---|---|---|
| HM-PRI-01 | P0 | Create private match | Account A creates private game. | 6-digit game code appears. |
| HM-PRI-02 | P0 | Join private match | Account B enters the code. | Both users join the same game. |
| HM-PRI-03 | P1 | Invalid code | Enter a wrong/expired code. | Clear error, no crash, user can try again. |
| HM-PRI-04 | P1 | Share invite | Use share/invite option if available. | Shared text includes game code and useful link. |
| HM-PRI-05 | P1 | Host waiting state | Host creates a game and waits for 60 seconds. | Waiting screen remains stable and can be cancelled. |
| HM-PRI-06 | P1 | Third user attempt | Optional: third account tries same code. | App handles this cleanly and does not corrupt the match. |

## 13. Ladder / League Mode Tests

This is one of the most important areas.

Before testing, write down or screenshot:

- Account A points, level, wins/losses/draws.
- Account B points, level, wins/losses/draws.

| ID | Priority | Test Case | Steps | Expected Result |
|---|---|---|---|---|
| HM-LAD-01 | P0 | League requires login | Try League while logged out. | App asks for login; no anonymous ranked game starts. |
| HM-LAD-02 | P0 | Find League match | Account A and B start League/Ladder in same game. | Match is created/found and both users enter it. |
| HM-LAD-03 | P0 | Points after win | Finish League match with a clear winner. | Winner/loser stats and points update correctly. |
| HM-LAD-04 | P0 | No double scoring | Refresh/reopen after match result. | Points/stats are not counted twice. |
| HM-LAD-05 | P0 | Player can progress/level up | Play enough Ladder/League games to trigger progress if possible, or verify progress indicators after each result. | Player progress moves forward visibly; level/rank/points do not stay stuck without explanation. |
| HM-LAD-06 | P0 | Leaderboard update | Open leaderboard after ranked match on both devices and Web if possible. | Updated points/level/rank are visible and consistent. |
| HM-LAD-07 | P1 | Stats consistency | Compare profile, match result screen, leaderboard, and any home/ranking screen. | Wins/losses/draws, points, level, and rank show the same values or sync after a clear refresh. |
| HM-LAD-08 | P1 | Progress feedback | Finish a ranked match and observe the result screen. | User clearly sees what changed: win/loss, points gained/lost, new level/rank if applicable, and next goal. |
| HM-LAD-09 | P1 | Leave ranked match | Try to leave an active League match. | Warning appears; if confirmed, result is handled clearly. |
| HM-LAD-10 | P1 | Fair matching | If possible, test accounts with different levels. | App does not create obviously unfair match without clear reason. |
| HM-LAD-11 | P1 | Draw in League | Create draw in Tic-Tac-Toe or Reversi if practical. | Draw stats/points update correctly. |
| HM-LAD-12 | P1 | Restart after ranked result | Finish a Ladder/League match, fully close and reopen the app, then check profile/leaderboard. | Latest progress is still saved and shown correctly. |
| HM-LAD-13 | P2 | Ladder comfort | Start from home screen and try to understand how to climb the ladder without guidance. | The flow is understandable; report any confusing label, missing explanation, or unnecessary tap. |

## 14. Direct Challenge Tests

| ID | Priority | Test Case | Steps | Expected Result |
|---|---|---|---|---|
| HM-CHL-01 | P1 | Send challenge | Account A opens leaderboard and challenges Account B. | B receives challenge notification/dialog. |
| HM-CHL-02 | P1 | Accept challenge | B accepts. | Both users enter the correct game. |
| HM-CHL-03 | P1 | Decline challenge | B declines. | A/B states are clear; no stuck challenge. |
| HM-CHL-04 | P2 | Challenge timeout | Leave challenge unanswered. | It expires or remains clearly pending. |

## 15. Web Version Tests

| ID | Priority | Test Case | Steps | Expected Result |
|---|---|---|---|---|
| HM-WEB-01 | P0 | Web loads | Open `https://opengames.vip`. | Game selector loads. |
| HM-WEB-02 | P1 | Mobile Web layout | Open web version on mobile browser. | Text/buttons/boards do not overlap. |
| HM-WEB-03 | P1 | Direct game links | Open `/muehle`, `/checkers`, `/chess` if available. | Correct game opens or app routes correctly. |
| HM-WEB-04 | P1 | Web online match | Play Android-vs-Web online match. | Sync works both ways. |
| HM-WEB-05 | P2 | Browser refresh | Refresh during a non-critical game state. | App recovers or returns to a clear state. |

## 16. UX and Visual Quality Checks

Please report anything that feels confusing, even if it technically works.

| ID | Priority | Test Case | Steps | Expected Result |
|---|---|---|---|---|
| HM-UX-01 | P2 | First impression | Open app as a new user and describe what you think the app offers. | The value should be clear: free classic board games, offline AI, online friends. |
| HM-UX-02 | P2 | Button clarity | Inspect online, bot, settings, leaderboard buttons. | Button purpose is clear. |
| HM-UX-03 | P2 | Small-screen layout | Use a smaller phone or narrow Web viewport. | Text is readable; no important UI is cut off. |
| HM-UX-04 | P2 | Error recovery | Trigger an error, such as invalid code or no internet. | User can recover without restarting app. |
| HM-UX-05 | P3 | Text quality | Look for typos, odd wording, mixed languages. | Text feels natural and consistent. |
| HM-UX-06 | P2 | Waiting/loading feedback | Use matchmaking, private match, Ladder, and reconnect flows. | Waiting states explain what is happening and allow cancel/retry where appropriate. |
| HM-UX-07 | P2 | Comfort improvements | Play for 15 minutes and write every moment that feels unnecessarily slow, hidden, confusing, or too many taps. | Tester provides concrete improvement ideas, not only bug reports. |
| HM-UX-08 | P2 | Result clarity | Finish bot, online, and Ladder games. | Result screen clearly shows winner, next action, rematch option if available, and any points/progress change. |

## 17. Performance and Stability

| ID | Priority | Test Case | Steps | Expected Result |
|---|---|---|---|---|
| HM-PERF-01 | P0 | No crashes | Use app for 20-30 minutes across several games. | No crash. |
| HM-PERF-02 | P1 | No long freezes | Switch games and play bots. | UI does not freeze for a long time. |
| HM-PERF-03 | P1 | App background/resume | Put app in background and return. | Game state remains stable. |
| HM-PERF-04 | P1 | Network interruption | Briefly disable internet during online game. | App shows clear state and does not crash. |

## 18. Recommended Minimum Test Run

If time is limited, please prioritize:

1. HM-SMK-01 to HM-SMK-05.
2. HM-ACC-01 to HM-ACC-04.
3. HM-SET-01 to HM-SET-04.
4. HM-CHK-01 to HM-CHK-05.
5. HM-MOR-01 to HM-MOR-04.
6. HM-ONQ-01 to HM-ONQ-06.
7. HM-PRI-01 to HM-PRI-04.
8. HM-LAD-01 to HM-LAD-13.
9. HM-WEB-01 to HM-WEB-04.
10. HM-PERF-01 to HM-PERF-04.

## 19. Bug Report Template

Please use this format for every issue:

```text
Bug title:
Test case ID:
Priority: P0 / P1 / P2 / P3
Platform: Android / Web / Android-vs-Android / Android-vs-Web
Device and OS:
Browser, if Web:
App version/build:
Game:
Mode: Offline / Bot / Quick Match / Private Match / League / Challenge
Account(s):

Steps to reproduce:
1.
2.
3.

Expected result:
Actual result:
How often does it happen: Always / Often / Sometimes / Once
Screenshot or video attached: Yes / No
Comfort/usability suggestion, if any:
Notes:
```

## 20. Final Test Summary Template

At the end, please send a short summary:

```text
Tester:
Date:
Devices used:
Accounts used:
Total testing time:

Overall impression:

Critical issues found:
- 

Serious issues found:
- 

UX/confusing areas:
- 

Comfort/usability improvement ideas:
- 

Games/modes tested:
- Android offline:
- Android online:
- Web:
- Android-vs-Web:
- League/Ladder:

Ladder/League findings:
- Can players progress/level up correctly?
- Are points, rankings, wins/losses/draws saved correctly?
- Is the progress/result feedback clear enough?

Release recommendation:
[ ] Ready
[ ] Ready after minor fixes
[ ] Not ready, critical issues found

Additional notes:
```
