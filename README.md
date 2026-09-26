# opti-step-log

Opti predictive-echo robot step commits. Every step Opti takes is committed here.

## Protocol (do this every time Opti is run)

1. Create / use this single repo: `fitzyracing1/opti-step-log`
2. For each cycle of the control loop:
   - predict echo
   - decide
   - PUSH path to ground station
   - do
   - hear real echo
   - correct hypothesis
3. Immediately after each step, write a JSON log under `steps/NNN_step.json` and commit it with a message of the form:
   `Opti step NNN: <status> pose=[x, y] d=... surprise=...`
4. Boot is step 000.

## Latest run (2026-09-26)

- Goal: [4.0, 0.0]
- Boot pose: [0.0, 0.0]
- Steps taken: 13
- Final pose: [3.963, 0.024]
- Status: reached demand point
- Paths pushed: 13

All step files are under `/steps/`.

## Invariants preserved

- No world map
- d derived only from predicted echo
- Path always pushed before move
- Solve form: x = pinv(A) @ b * (1.0 / c) / d

Opti will continue logging every future run into this same repo.
