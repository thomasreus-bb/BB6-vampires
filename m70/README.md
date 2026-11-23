# Programs for no. 70 (`1RB1RF_1LC1RD_1LA1LC_1RA0RE_1RD1LA_---0LE`)

| file | content |
|---|---|
| `sim70dc.c` | **main simulator**: exact Bell map, rules learned on the fly by direct simulation of the TM; x advanced by divide and conquer with GMP; the deep part of the stack in the file `sim70dc.stack`; checkpoint `sim70dc.ck`; every block 7, 5, 3, 1 near the front of the stack is logged in `events70dc.txt` |
| `sim70.c` | the same without GMP and without disk (simpler, much slower for large x) |
| `macro70.py`, `lev70.c` | the rule learner in Python (used by `watch70.py`; `lev70` is compiled automatically) |
| `watch70.py` | long-run estimator: real run plus injection tests (a block 1, 3, 5, 7 or 9 put into the real stack, 300 Bells with random parities), gives the halting rate per Bell with an interval and a stationarity test |

## sim70dc

    sudo apt install libgmp-dev                  # once
    gcc -O3 -march=native -o sim70dc sim70dc.c -lgmp
    ./sim70dc -f -t 4663800                      # test, about 2 s
    ./sim70dc                                    # continues from the checkpoint; Ctrl-C stops after the current block

The test must print

    check values at Bell 4663800: bits 2728153, x mod 2^64 = 0x58106550ccb57c0e, stack 2616485 entries, hash 884327361506333381

Options: `-t BELL` stop at this Bell, `-f` start fresh, `-r SEC` report interval (60), `-s SEC` checkpoint interval (1800), `-M MB` RAM for the stack front (512), `-b B` Bells per block.

Every report shows the Bell number, the size of x and of the stack, the speed, and how often odd blocks 9, 7, 5, 3, 1 have appeared near the front (the way to HALT is 9 → 7 → 5 → 3 → 1 → HALT).

Resources: about 1.5–3.5 million Bells/s on one core. The stack needs about 2.2 bytes per Bell on disk (22 GB at 10¹⁰ Bells); keep `sim70dc.stack` together with `sim70dc.ck`. x needs 0.073 bytes per Bell in RAM, the divide and conquer about three times that.

## sim70

    gcc -O2 -o sim70 sim70.c
    ./sim70 -f -n 4663800                        # same check values
    ./sim70                                      # checkpoint sim70.ck, events in events70.txt

## watch70.py

    python3 watch70.py --minutes 15              # rounds of 15 minutes; report in watch70_report.txt
