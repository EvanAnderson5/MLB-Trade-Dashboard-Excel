# MLB Buy-Low Trade Dashboard | Excel

## Overview

![MLB-Trade-Dashboard-Excel](MLBDashboard.png)

- The dashboard uses a player's expected and actual stats to find players who could be considered buy-low trade targets.
- This dashboard could be used by any baseball fan or front office to understand which players may be lucky or unlucky during the season.
- It shows which players can be expected to slow down in production versus players who may improve.
- The data is just a snapshot, taken during the 2026 MLB season prior to the MLB trade deadline.

## Key Findings
- Players like Bryson Stott, Masyn Winn, Nico Hoerner and Cam Smith were considered to be buy-low trade targets (low wRC+ but better expected stats than actual stats).
- Players like Pete Crow-Armstrong, Junior Caminero and Otto Lopez had higher actual stats than expected stats but because of their overall run production they were still considered elite run producers, rather than lucky hitters.
- Ernie Clement was the luckiest hitter with a wOBA of 0.326 and an xwOBA of 0.275 (-0.051 difference). The unluckiest hitter was Yordan Alvarez with a wOBA of 0.439 and an xwOBA of 0.476 (+0.037 difference).

## Data
- Source: raw data from FanGraphs.
- Stats used: wOBA, xwOBA, wRC+, wOBA_Diff (calculated).
- Qualified hitters only (FanGraphs minimum PA threshold).
- *Data is included in the Excel file.*

## How It Works
- I used a player's xwOBA and subtracted their wOBA from it to create the wOBA_Diff column.
  - Positive wOBA_Diff = Unlucky (higher xwOBA than wOBA).
  - Negative wOBA_Diff = Lucky (higher wOBA than xwOBA).
- I used a long nested IF statement to decide where players belonged.

| Category | wRC+ | wOBA_Diff |
|---|---|---|
| `Buy Low/Unlucky And Below Average Production` | <=100 | Positive |
| `Unlucky, Yet Above Average Production` | 101-124 | Positive |
| `Solid Contributor` | 91-124 | Negative |
| `Elite Player/Run Producer` | >=125 | Either |
| `Lucky Hitter With Low Production` | <91 | Negative |

- The user is able to use a dropdown of player names to search for specific players' wOBA, xwOBA, wRC+ and their trade value (whether they are Buy Lows, Solid Contributors, Elite Players, etc).
- There is also an interactive pivot table and chart that can be changed to see the average statistics for each level of trade value.

## Dashboard Sheets
| Sheet | Description |
|---|---|
| `Trade_Board` | This is the main dashboard with all the findings, the interactive elements, and the pivot chart/graph. |
| `Raw_Fangraphs` | Raw public FanGraphs data. |

## Limitations
- The model doesn't use salary or team control, which are important factors when it comes to deciding who to trade for.
- There are few filters for the user, such as salary or position.
- It is a single snapshot and wasn't updated after the trade deadline.
- It only uses qualified players from FanGraphs, so some players with fewer plate appearances may be excluded.

## Next Steps
- Add more interactive elements so the user can find players of specific positions, salary limits, years-of-control, etc.
- Add another classification so coaches or front office members know who should be traded away. This could be a sell-high feature for players with much higher actual stats compared to expected stats.

## Repository Files
| File | Description |
|---|---|
| `README.md` | Project documentation |
| `MLB_Analysis.xlsx` | The dashboard |
| `MLBDashboard.png` | The dashboard screenshot |

## How to Use
- Download and open `MLB_Analysis.xlsx` in Excel.
- Click the dropdown in cell H2 to toggle the different players.
- The final list appears directly underneath the name of the player you selected.
