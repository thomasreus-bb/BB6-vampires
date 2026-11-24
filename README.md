# BB6-vampires

For vampires in BB6 holdouts.

## Overview: Vampire-like TMs in BB6 (23 Nov 2026)

Machines whose Bell map is driven by the digits of one large number n (n' ≈ q·n, with q = 3/2 or 4/3) and a short word or tail, so that a HALT needs a certain sequence of residues of n ("lottery"). The expected values come from a Markov estimate (random residues) and are heuristics, not proofs.

**Status:** *simulated to HALT* = the HALT was found by exact simulation of the Bell map; *+ proof* = in addition a formal Rocq proof; *open* = no HALT found yet.

| no. | machine | type | status | expected HALT (Markov) | computing time to HALT | steps of the original TM |
|---|---|---|---|---|---|---|
| <a id="t8"></a>[8](#8) | `1RB0RB_1LC1RF`<br>`0RD0LB_0RA1LE`<br>`1LD---_0RB0RC` | vampire, 4/3, closed table (192 words) | **simulated to HALT + proof** (Bell 298,793,335, 21 Oct; Rocq proof busycoq PR #41, accepted) | 1.6·10⁻⁹ per Bell → ≈ 6·10⁸ Bells | ≈ 2 min on one core (`belldc3`) | ≈ 10^(7.5·10⁷) |
| <a id="t1"></a>[1](#1) | `1RB0RF_1LC---`<br>`1RD0LC_0RE0RD`<br>`1LF1LC_1LE1RA`<br>(TM1-F, orbit O2) | vampire family, 3/2, closed table (2,880 words) | **simulated to HALT** (Bell 731,899,010,932, Ahmer Raza, 30 Oct; confirmed by Thomas Reus) | 8.9·10⁻¹³ per Bell → ≈ 1.1·10¹² Bells (median 7.8·10¹¹) | 23 h 42 min on 8 cores (AMD EPYC 9655, `belldco`); ≈ 13–14 days on a notebook | ≈ 10^(2.58·10¹¹) |
| <a id="t2"></a>[2](#2) | `1RB---_1LC0RB`<br>`0LD0LC_1RE1RB`<br>`1RD1LF_1LA0LE`<br>(TM1, O1) | as no. 1 | **simulated to HALT** (Bell 747,242,483,684, Ahmer Raza, 30 Oct) | as no. 1 | 24 h 29 min on 8 cores | ≈ 10^(2.63·10¹¹) |
| <a id="t3"></a>[3](#3) | `1RB0LA_0RC0RB`<br>`1LD1LA_1LC1RE`<br>`1RF0RD_1LC---`<br>(TM2, O2) | as no. 1 | **simulated to HALT** (orbit O2, as no. 1) | as no. 1 | as no. 1 | ≈ 10^(2.58·10¹¹) |
| <a id="t4"></a>[4](#4) | `1RB0RE_1RC---`<br>`0RD0RC_1LE1LF`<br>`1LD1RA_1RC0LF`<br>(TM2', O2) | as no. 1 | **simulated to HALT** (orbit O2, as no. 1) | as no. 1 | as no. 1 | ≈ 10^(2.58·10¹¹) |
| <a id="t5"></a>[5](#5) | `1RB0LA_0RC0RB`<br>`1LD1LA_1LC1RE`<br>`1RF0RD_1LA---`<br>(TM2a, O3) | as no. 1 | **simulated to HALT** (Bell 1,961,935,897,288, Ahmer Raza, 30 Oct) | as no. 1 | 79 h on 8 cores (65 h of new progress) | ≈ 10^(6.91·10¹¹) |
| <a id="t6"></a>[6](#6) | `1RB---_0RC0RB`<br>`1LD1LE_1LC1RF`<br>`1RB0LE_1RA0RD`<br>(TM2b, O4) | as no. 1 | **simulated to HALT** (Bell 1,941,376,761,248, Ahmer Raza, 1 Nov) | as no. 1 | several days on 8 cores | ≈ 10^(6.84·10¹¹) |
| <a id="t7"></a>[7](#7) | `1RB0RF_1LC---`<br>`1LF1LD_1RE0LD`<br>`0RC0RE_1LC1RA`<br>(TM2b', O4) | as no. 1 | **simulated to HALT** (orbit O4, as no. 6) | as no. 1 | as no. 6 | ≈ 10^(6.84·10¹¹) |
| <a id="t70"></a>[70](#70) | `1RB1RF_1LC1RD`<br>`1LA1LC_1RA0RE`<br>`1RD1LA_---0LE` | vampire-like, 3/2, HALT needs an odd stack block to shrink 9 → 7 → 5 → 3 → 1 | **open** (50,132,149,704 Bells, about 10^(1.77·10¹⁰) steps, no HALT; closest approach: block 5 near the front, 460 times; block 7 221,440 times) | about 10⁻¹⁹ to 10⁻²⁰ per Bell, → median about 10¹⁹ Bells or more; HALT with probability 1 in the model | out of reach (x alone would need about 7·10¹⁷ bytes) | ≈ 10^(3.5·10¹⁸) |
| <a id="t86"></a>[86](#86) | `1RB0RE_1RC0RF`<br>`1LD1RA_1LB1LD`<br>`1RA1LB_---0LD` | in lockstep with no. 70 (same left part, only a frozen right end differs); no. 70 is exactly no. 86 started in B | **open** (as no. 70, as long as the lockstep holds) | as no. 70 | as no. 70 | as no. 70 |
| <a id="t105"></a>[105](#105) | `1RB1LF_1LC0RD`<br>`---1LA_0LA0RE`<br>`1LA1RA_1LB0LD` | vampire-like, 4/3, small tail counter; 35-level residue path to HALT | **open** (100,000 levels without HALT) | 1.1·10⁻¹⁴ per level → ≈ 9·10¹³ levels (median 6·10¹³) | ≈ 5,000× the TM2 run: about 200 years on a notebook, a few years on a large cluster (simulator still to be written) | ≈ 10^(2.25·10¹³) |
| <a id="t51"></a>[51](#51) | `1RB0RE_1LC0RA`<br>`1LA1LD_1LC1LF`<br>`0LC0LB_1LE---` | 8/3 map, memory word r as a stack (table **not** closed); 108-step path to HALT from r = empty | **open** (probviously halting cryptid; 400 macro steps, about 10^320 TM steps, no HALT; closest approach 102 macro steps) | about 3^−80 per reset of r (wiki, Racheline) | out of reach | ≈ 10^10^38 (wiki, heuristic) |
| <a id="t61"></a>[61](#61) | `1RB---_0RC0RE`<br>`1RD1RF_1LE0LB`<br>`1RC0LD_1RC1RA` | same machine as no. 51, start state F (in the naming of no. 51); reaches C(12, [6]) after 111 steps | **open** (probviously halting cryptid; 400 macro steps without HALT, closest approach 103 macro steps) | as no. 51 | out of reach | ≈ 10^10^38.1 (wiki, heuristic) |
| <a id="t71"></a>[71](#71) | `1RB1RD_1LC0LE`<br>`1RA0LB_1RA1RF`<br>`0RA0RC_1RE---` | same machine as no. 51, start state C; reaches C(16, empty) of no. 51 after 95 steps | **open** (400 macro steps, about 10^320 TM steps, no HALT; closest approach 101 macro steps) | as no. 51 | out of reach | ≈ 10^10^38 (as no. 51) |
| <a id="t93"></a>[93](#93) | `1RB0LC_1RC1RE`<br>`1LA0LD_0RB0RA`<br>`1RB1RF_1RD---` | same machine as no. 51, start state B; reaches C(6, empty) of no. 51 after 18 steps | **open** (400 macro steps, about 10^320 TM steps, no HALT; closest approach 103 macro steps) | as no. 51 | out of reach | ≈ 10^10^38 (as no. 51) |
| <a id="t31"></a>[31](#31) | `1RB1RF_1RC0LD`<br>`1LB1RA_1RE1LE`<br>`0RC0LB_0RB---` | vampire-like, 4/3, nested sub-process (prefix table mod 6); table with several blocks, not closed | **open** (202 Bells, 10³⁵·⁵ steps without HALT) | below 2·10⁻⁶ per Bell (measured upper bound) | unknown | – |
| <a id="t32"></a>[32](#32) | `1RB1LB_0RC0LD`<br>`1LD1RE_1RC0LA`<br>`1RD1RF_0RD---` | as no. 31 (very probably equivalent) | **open** | as no. 31 | unknown | – |
| <a id="t113"></a>[113](#113) | `1RB0LC_1LC0RE`<br>`1LD1LB_1LA1LD`<br>`1RF0RA_---1RE` | odometer (binary counter of fuel tanks (011)ⁿ); same table as #581 = bbchallenge id 172044, which halts; HALT needs the top tank to run empty with a "bad" leftover word (still to be proved that it is a vampire) | **open** (about 10¹²⁵ visits, about 10²⁵¹ steps, no HALT; the two small top tanks ran empty without HALT) | probability 1 in the model; next chance at about 10⁶⁶⁰⁰ visits | out of reach | ≥ about 10¹³⁰⁰⁰ |

Not included:
- No. 19: it has the scan signature "vampire-like", but a closer look shows a two-number system that is probably non-halting.
- The tetrational cryptids (nos. 60, 62–66) and the needle-like machines (e.g. nos. 42, 45/52): HALT there needs an exact value of a counter, not a residue pattern.

More machines can be added here as they are found.



## Machines

<a id="8"></a>
### [8](#t8). `1RB0RB_1LC1RF_0RD0LB_0RA1LE_1LD---_0RB0RC`

<img src="diagrams/1RB0RB_1LC1RF_0RD0LB_0RA1LE_1LD---_0RB0RC.png" alt="space-time diagram" height="350">

<a id="1"></a>
### [1](#t1). `1RB0RF_1LC---_1RD0LC_0RE0RD_1LF1LC_1LE1RA`

<img src="diagrams/1RB0RF_1LC---_1RD0LC_0RE0RD_1LF1LC_1LE1RA.png" alt="space-time diagram" height="350">

<a id="2"></a>
### [2](#t2). `1RB---_1LC0RB_0LD0LC_1RE1RB_1RD1LF_1LA0LE`

<img src="diagrams/1RB---_1LC0RB_0LD0LC_1RE1RB_1RD1LF_1LA0LE.png" alt="space-time diagram" height="350">

<a id="3"></a>
### [3](#t3). `1RB0LA_0RC0RB_1LD1LA_1LC1RE_1RF0RD_1LC---`

<img src="diagrams/1RB0LA_0RC0RB_1LD1LA_1LC1RE_1RF0RD_1LC---.png" alt="space-time diagram" height="350">

<a id="4"></a>
### [4](#t4). `1RB0RE_1RC---_0RD0RC_1LE1LF_1LD1RA_1RC0LF`

<img src="diagrams/1RB0RE_1RC---_0RD0RC_1LE1LF_1LD1RA_1RC0LF.png" alt="space-time diagram" height="350">

<a id="5"></a>
### [5](#t5). `1RB0LA_0RC0RB_1LD1LA_1LC1RE_1RF0RD_1LA---`

<img src="diagrams/1RB0LA_0RC0RB_1LD1LA_1LC1RE_1RF0RD_1LA---.png" alt="space-time diagram" height="350">

<a id="6"></a>
### [6](#t6). `1RB---_0RC0RB_1LD1LE_1LC1RF_1RB0LE_1RA0RD`

<img src="diagrams/1RB---_0RC0RB_1LD1LE_1LC1RF_1RB0LE_1RA0RD.png" alt="space-time diagram" height="350">

<a id="7"></a>
### [7](#t7). `1RB0RF_1LC---_1LF1LD_1RE0LD_0RC0RE_1LC1RA`

<img src="diagrams/1RB0RF_1LC---_1LF1LD_1RE0LD_0RC0RE_1LC1RA.png" alt="space-time diagram" height="350">

<a id="70"></a>
### [70](#t70). `1RB1RF_1LC1RD_1LA1LC_1RA0RE_1RD1LA_---0LE`

<img src="diagrams/1RB1RF_1LC1RD_1LA1LC_1RA0RE_1RD1LA_---0LE.png" alt="space-time diagram" height="350">

**Equivalence.** No. 70 is exactly no. 86 started in state B: the two machines differ in two transitions, which are only used together in a 3-step detour that ends in the same configuration in both. No. 86 started in A (the real holdout) runs in lockstep with no. 70 after about 3.5·10⁵ steps; only a short frozen part at the right end of the tape differs.

**Bells.** A Bell starts when state A reaches a new leftmost cell with the tape

    1 0^x 1^m 0^g1 1^b1 0^g2 1^b2 ...      (blocks of ones b_i, gaps of zeros g_i)

During a Bell the left block grows by 6 and the gap x shrinks by 4 per sweep, so the next Bell has

    x' = 3x/2 + c

with a small constant c. The list S = [m, g1, b1, g2, b2, ...] is a **stack**: each Bell rewrites only its first few entries (at most 4 pairs), and how it does so depends only on S's front and on x mod 12. In the run x is always divisible by 6, so **one bit per Bell** (x/6 even or odd) drives the stack, as in the vampires (Hydra-like parities). The rules are not a short closed table (more than 60,000 different ones by 2·10⁹ Bells); the simulator learns each rule by direct simulation when it is first needed.

**Way to HALT.** HALT needs a block of length 1 in the stack that is then hit (about 6 % chance). Blocks of length 1 only arise when an odd block shrinks step by step: 9 → 7 → 5 → 3 → 1. Blocks 9 are frequent, every further step is rare. During the simulation, the smallest block seen so far indicates how close the run has come to HALT (simulation progress), similar to the role of the distance D for the vampires (nos. 1–8).

**Data** (simulation with [`sim70dc`](m70/README.md) on a notebook, Thomas Reus, 23–24 Nov 2026; exact, 50,132,149,704 Bells, about 10^(1.77·10¹⁰) TM steps, x has 2.9·10¹⁰ bits, no HALT):

| quantity | value |
|---|---|
| blocks 9 near the front | 9,928,622 (2.0·10⁻⁴ per Bell) |
| blocks 7 | 221,440 (4.4·10⁻⁶ per Bell) |
| blocks 5 | 460 (0.9·10⁻⁸ per Bell; about a quarter of them are the same block coming back into the first three positions) |
| blocks 3 / 1 | 0 / 0 |
| counts per 8·10⁸ Bells | constant over the whole run (stationary) |

**Why the last steps are so rare.** A new small odd block always appears directly behind a large gap: the front of the stack is then `4 |G| v 3 4 6 …`. At a shrink step the block has gap 4 in front and the new gap is G = m + 4, where m is the front block, which grows while nothing is pushed. A block that survives long near the front therefore shrinks only when m is large. New 7s sit behind G ≈ 67, new 5s behind G = 91–147; a typical gap in the stack is about 6. Whether a block shrinks further depends almost only on this gap, in the same way for every step (7 → 5, 5 → 3, 3 → 1, and HALT for a block 1). The values are measured on real fronts with the gap set to the test value, 300 Bells with random parities ([`fate70.py`, `gap70.py`, `gapv70.py`](m70/README.md)):

| gap in front of the block | 1 | 4–10 | 20 | 40 | 67 | 91 | 115 | ≥ 130 |
|---|---|---|---|---|---|---|---|---|
| P(next step) | ≈ 50 % | 0 | 3.3 % | 1.3 % | 0.3 % | 0.035 % | 0.005 % | 0 of 20,000 |

Continuing the real fronts gives P(7 → 5) = 0.15 % (the run itself gives 0.2 %) and P(5 → 3) = 0 of 6,800 (below about 0.05 %). The earlier injection tests had put the block behind a typical small gap and gave 0.7 % and 0.8–1 %, far too high. So no block 3 after 460 blocks 5 is just what is expected.

**Expected HALT (Markov-type estimate).** Rate ≈ 2·10⁻⁴ (new 9) · 2.2 % (9 → 7) · 0.2 % (7 → 5) · about 2·10⁻⁴ (5 → 3) · ≤ 10⁻⁴ (3 → 1) · ≤ 10⁻⁴ (1 → HALT) ≈ **10⁻¹⁹ to 10⁻²⁰ per Bell**, median about **10¹⁹ Bells or more** (about 10^(3.5·10¹⁸) TM steps). The earlier value (3·10⁻¹⁴ per Bell, median 2·10¹³ Bells) used the injection values and was too optimistic.

**No way out except HALT.** Nothing in the run points to a way to avoid the HALT for ever:
- the deep part of the stack is never read again, so the machine is a front of a few stack entries driven by one parity bit per Bell, and the parities behave like random bits;
- the rates of new blocks 9, 7 and 5 stay constant over 5·10¹⁰ Bells; there is no drift, no cycle and no invariant that would forbid small blocks;
- every link of the chain 9 → 7 → 5 → 3 → 1 → HALT has a small but positive probability, also behind large gaps (the gap curve falls fast, but not to zero).

In this model the machine halts with probability 1; it only takes far longer than first estimated. This is a heuristic, not a proof.

**Computing time to HALT.** `sim70dc` ran at 0.7–1.4 million Bells/s on the notebook (slowly falling, because x grows by 0.585 bits per Bell). At the new median of about 10¹⁹ Bells, x alone would have about 7·10¹⁷ bytes: out of reach for any computer. The deep stack need not be stored (`sim70dz -d`).

<a id="86"></a>
### [86](#t86). `1RB0RE_1RC0RF_1LD1RA_1LB1LD_1RA1LB_---0LD`

<img src="diagrams/1RB0RE_1RC0RF_1LD1RA_1LB1LD_1RA1LB_---0LD.png" alt="space-time diagram" height="350">

<a id="105"></a>
### [105](#t105). `1RB1LF_1LC0RD_---1LA_0LA0RE_1LA1RA_1LB0LD`

<img src="diagrams/1RB1LF_1LC0RD_---1LA_0LA0RE_1LA1RA_1LB0LD.png" alt="space-time diagram" height="350">

<a id="51"></a>
### [51](#t51). `1RB0RE_1LC0RA_1LA1LD_1LC1LF_0LC0LB_1LE---`

<img src="diagrams/1RB0RE_1LC0RA_1LA1LD_1LC1LF_0LC0LB_1LE---.png" alt="space-time diagram" height="350">

<a id="61"></a>
### [61](#t61). `1RB---_0RC0RE_1RD1RF_1LE0LB_1RC0LD_1RC1RA`

<img src="diagrams/1RB---_0RC0RE_1RD1RF_1LE0LB_1RC0LD_1RC1RA.png" alt="space-time diagram" height="350">

<a id="71"></a>
### [71](#t71). `1RB1RD_1LC0LE_1RA0LB_1RA1RF_0RA0RC_1RE---`

<img src="diagrams/1RB1RD_1LC0LE_1RA0LB_1RA1RF_0RA0RC_1RE---.png" alt="space-time diagram" height="350">

<a id="93"></a>
### [93](#t93). `1RB0LC_1RC1RE_1LA0LD_0RB0RA_1RB1RF_1RD---`

<img src="diagrams/1RB0LC_1RC1RE_1LA0LD_0RB0RA_1RB1RF_1RD---.png" alt="space-time diagram" height="350">

<a id="31"></a>
### [31](#t31). `1RB1RF_1RC0LD_1LB1RA_1RE1LE_0RC0LB_0RB---`

<img src="diagrams/1RB1RF_1RC0LD_1LB1RA_1RE1LE_0RC0LB_0RB---.png" alt="space-time diagram" height="350">

<a id="32"></a>
### [32](#t32). `1RB1LB_0RC0LD_1LD1RE_1RC0LA_1RD1RF_0RD---`

<img src="diagrams/1RB1LB_0RC0LD_1LD1RE_1RC0LA_1RD1RF_0RD---.png" alt="space-time diagram" height="350">

<a id="113"></a>
### [113](#t113). `1RB0LC_1LC0RE_1LD1LB_1LA1LD_1RF0RA_---1RE`

<img src="diagrams/1RB0LC_1LC0RE_1LD1LB_1LA1LD_1RF0RA_---1RE.png" alt="space-time diagram" height="350">
