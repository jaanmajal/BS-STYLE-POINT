# BS-STYLE POINT RC TIME ATTACK - Rules and Scoring v2

**Release:** v27.6.0 dry-run package  
**Brand:** TECH-ARTS CRAWLER  
**Format:** Points Championship - one attempt per driver per Special Stage

## 1. Competition format

- The default event has four Special Stages: SS1, SS2, SS3 and SS4.
- Default time cutoffs are SS1 10 minutes, SS2 12 minutes, SS3 15 minutes and SS4 10 minutes. The organiser may configure them before racing.
- Each stage has a configured total gate count. The default is 10 gates per stage.
- The draw order must be generated and locked before a stage is opened.
- A stage result is recorded once. A replacement attempt requires the organiser's correction/overwrite workflow.
- One active marshal device may hold a stage lock at a time.

## 2. Position points

| Position | Base points |
|---:|---:|
| 1 | 100 |
| 2 | 95 |
| 3 | 90 |
| 4 | 87 |
| 5 | 84 |
| 6 | 81 |
| 7 | 78 |
| 8 | 75 |
| 9 | 72 |
| 10 | 69 |
| 11 | 66 |
| 12 | 63 |
| 13 | 60 |
| 14 | 58 |
| 15 | 56 |
| 16 | 54 |
| 17 | 52 |
| 18 | 50 |
| 19 | 48 |
| 20 | 46 |
| 21 | 45 |
| 22 | 44 |
| 23 | 43 |
| 24 | 42 |
| 25 | 41 |
| 26 | 40 |
| 27 | 39 |
| 28 | 38 |
| 29 | 37 |
| 30 | 36 |
| 31 | 35 |
| 32 | 34 |
| 33 | 33 |
| 34 | 32 |
| 35 | 31 |
| 36 | 30 |
| 37 | 29 |
| 38 | 28 |
| 39 | 27 |
| 40 and below | 26 |

Finishing position is determined by raw elapsed time. Point deductions do not change raw-time order.

## 3. Penalties

| Infraction | Deduction / result |
|---|---:|
| Touch | -10 points per tap |
| Special Gate | -5 points per tap |
| Outrack | -3 points per tap |
| Jump Gate | DNF |

- Penalty taps are recorded against the selected driver and stage.
- Each tap stores the point value that applied when it was recorded.
- Updating the shared penalty preset affects future taps only. Existing recorded tap values are preserved.
- A Jump Gate violation is recorded using the DNF control, then the marshal enters the number of gates cleared.

## 4. DNF, FINISH and DNS scoring

Let:

- `DNF base = max(20, points for the last registered position - 20)`
- `G = total gates configured for the stage`
- `g = gates cleared by the driver before DNF`
- `P = total penalty-point deductions for the stage`

**DNF points**

`DNF points = max(0, round(DNF base x g / G) - P)`

A DNF at zero gates can score zero. Gate progress must be entered from 0 through the configured total before a new DNF result can be saved.

**FINISH points**

`FINISH points = max(round(DNF base / G), position base points - P)`

A FINISH result cannot fall below the Gate-1 DNF base floor.

**DNS points**

`DNS = 0 points`

When stage points are equal, FINISH ranks above DNF; DNF ranks above DNS. Historical DNF records with no saved gate count must be reviewed and corrected by the organiser rather than assumed to have cleared all gates.

## 5. Overall championship tie-breakers

If drivers have equal total net points, apply these tie-breakers in order:

1. Higher net points in the final Special Stage.
2. FINISH above DNF above DNS in the final Special Stage.
3. More stages with a recorded result.
4. Lower cumulative raw elapsed time across FINISH results.
5. Lower race number.

## 6. Marshal and data handling

- The marshal must enter and save a marshal name before timing or recording penalties.
- The marshal reviews the captured time and penalties with the driver, confirms STOP, then saves the result.
- DNF gate progress is required before saving.
- A marshal link is event-specific and can be closed by the organiser.
- New stages cannot be claimed while Firebase is offline. If connectivity drops after a stage lock is acquired, the current run may continue locally and queue its result. The stage lock remains held until Firebase confirms the saved result after reconnection.
- The public results page is read-only.

## 7. Historical records and migration

- Do not delete or rewrite historical results as part of this release.
- The organiser's **Apply final penalty preset** action changes shared rules for future taps only. Historical taps retain their saved point values.
- Legacy penalty records without a stored point value use compatibility fallbacks for their historical names. Any old Jump Gate record that is not already marked DNF must be reviewed manually.
- Export a JSON backup before applying the new Firebase rules or starting the dry run.

---

**Document status:** v2 supersedes the older v1 scoring PDF in the repository. Do not distribute the v1 PDF for this dry run.
