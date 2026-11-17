# UCF Qiskit Fall Fest 2026 — quanTA Challenge Submission

Verified Bell-pair delivery at designated ports on three processor models
(5-qubit ports 0,4; 9-qubit ports 0,7; 13-qubit ports 0,12), evaluated in
9 cases: ideal, noisy, and noisy + protection per model. Fidelity is
F = (1 + <XX> - <YY> + <ZZ>) / 4, computed from Aer density-matrix
simulation. Noise model: two-qubit depolarizing error 0.02 after each CX.
Exactly one protection strategy is used: a ZZ parity check with
postselection.

## Headline results

| Model | CX (noisy baseline) | Noisy F | Protected F | Acceptance |
|---|---|---|---|---|
| 2016-inspired reference (5q) | 7 | 0.9147 | 0.9414 | 91.7% |
| Contemporary IBM-style (9q) | 19 | 0.7949 | 0.7692 | 84.8% |
| Hyperbolic-inspired (13q) | 13 | 0.8515 | 0.8467 | 89.2% |

Noisy-baseline fidelity follows the two-qubit gate count exactly. The
parity check pays only where its ancilla is adjacent to both ports with
no routing (2016 model: +2 CX, 0 added SWAPs). Where routing is required,
the check's own gate cost consumes the gain. Design recommendation: a
dedicated parity-check ancilla adjacent to both ports.

Full per-case depth, gate counts, SWAP overhead, and qubit usage are in
`results_table.csv`; the executed notebook (`quanta_bell_submission.ipynb`)
contains the coupling graphs with ports marked, the transpiled circuits,
the comparison, interpretation, and limitations.

## Run

Python environment with Qiskit 2.6.2 and Qiskit Aer 0.18.2. Open the
notebook and run all cells; all assertions are checked in-notebook.

## Files

- `quanta_bell_submission.ipynb` — the submission notebook (executed, with outputs)
- `results_table.csv` — the 9-case quantitative comparison
- `video_script.md` — script for the accompanying walkthrough video (max 15 min)

Author: Muntaser Syed (Florida Institute of Technology), for the UCF
IBM Qiskit Fall Fest 2026 quanTA challenge (submission by email, due
Nov 18, 2026).
