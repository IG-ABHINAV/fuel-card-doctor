# Good first issues

Seeded issues for new contributors. File each one on GitHub with
the `good first issue` and `help wanted` labels.

## 1. Add a per-unit tank capacity file

Title: Let fleets supply tank capacities per unit

Description: Add a --tanks flag that reads a CSV file of unit
number and tank capacity in gallons (one row per unit) and
uses it instead of the single --tank-capacity value, so a
fleet with single-tank day cabs and dual-tank sleepers can
audit both correctly in one run. Units missing from the file
fall back to --tank-capacity.

Difficulty: Easy

Acceptance criteria: a tanks file with U-101 at 120 gallons
flags a 130-gallon fill on U-101 and does not flag a 200
gallon fill on a unit listed at 240; without the flag the
single --tank-capacity still applies; a test covers both
cases; README documents the flag.

## 2. Add a per-driver summary table

Title: Show totals and flags per driver

Description: Add a --by-driver flag that prints, after the
per-unit table, one line per driver with fills, gallons,
amount, and the count of error findings on that driver's
transactions, sorted with the most errors first, so a
manager can see which drivers need a conversation instead
of digging through the finding list.

Difficulty: Easy

Acceptance criteria: the sample file shows Rosa Diaz at the
top with 2 error findings; a test checks the ordering;
README documents the flag.

## 3. Support the EFS weekly statement format

Title: Accept EFS weekly statement CSV exports directly

Description: EFS weekly statements use different column
names (CARD, TRNS DATE, TRNS TIME, VEHICLE, ODOMETER,
QTY, AMT, PRICE, PROD) and a MM/DD/YYYY date. Add these
aliases and the date format if any are missing, and add a
test with a small EFS-shaped file that produces the same
findings as the equivalent standard file.

Difficulty: Medium

Acceptance criteria: the EFS-shaped sample produces the same
finding counts as the standard sample; a test covers the
aliases; README documents the supported export shapes.

## 4. Add a suggested-action line per finding

Title: Print what to do about each flagged transaction

Description: Each finding already says what is wrong. Add a
short suggested action to the text output, for example
"call the card provider to dispute the charge" for a
shared-card finding or "ask the driver for the receipt" for
a price mismatch, so a fleet manager who is not a fraud
analyst knows the next step. The JSON output gains an
"action" field per finding.

Difficulty: Medium

Acceptance criteria: the sample file shows an action for every
finding; the JSON findings carry the action field; a test
covers the mapping; README documents the actions.
