<h1 align="center">VAC: Coupling Temporal Planning and Velocity Filtering<br>for Quadruped Navigation</h1>

<p align="center">
  <img src="assets/images/teaser.jpg" width="100%" alt="VAC: real-world experiments and simulated navigation"/>
</p>

<p align="center">Quadruped navigation in dynamic environments.</p>

<p align="center">
  <a href="#dynamic-preview">Demos</a>
  &nbsp; · &nbsp;
  <a href="#ten-method-comparison">Comparison</a>
  &nbsp; · &nbsp;
  <a href="#method">Method</a>
  &nbsp; · &nbsp;
  <a href="#simulation-and-real-world-results">Results</a>
  &nbsp; · &nbsp;
  <a href="#narrated-overview">Video</a>
</p>

## Dynamic preview

Outdoor Go2 navigation through static obstacles and a moving pedestrian, alongside VAC navigation in simulation.

![Real-world experiments at 1× and VAC simulation at 6×](assets/previews/hero.gif)

**Real-world: 1× · Simulation: 6×.** Two demonstration excerpts; the opening real-world still is a time montage.

## Ten-method comparison

**Dynamic scene · 30 × 10 m · 58 static obstacles · 9 moving obstacles.** Both rows share a **6× playback** clock, with START below and GOAL above.

<!-- VIDEO_SLOT: simulation_comparison -->
![Ten methods in the same dynamic scene, shown in two synchronized rows](assets/previews/comparison.gif)

One recorded run per method. Shorter recordings hold their final frame.

![VAC example run: zero static collisions, zero dynamic collisions, goal reached, 87.5 seconds](assets/images/single_run_highlights.svg)

**Among these ten recordings, VAC is the only method that reaches the goal without a collision.**

### Single-run outcomes

| Method | Static collisions ↓ | Dynamic collisions ↓ | Goal reached | Run time (s) ↓ |
| :--- | :---: | :---: | :---: | :---: |
| Nav2 (DWB) | 3 | 5 | **Yes** | 151.4 |
| NeuPAN | **0** | 5 | **Yes** | 84.6 |
| DPCBF | **0** | 7 | **Yes** | 109.9 |
| RVO2 (ORCA) | **0** | 1 | **Yes** | 105.3 |
| FAR | **0** | **0** | No | 180.0 (timeout) |
| ABS | **0** | 10 | **Yes** | 72.8 |
| NavRL | 1 | 10 | **Yes** | 101.4 |
| REASAN | **0** | 4 | **Yes** | **67.3** |
| SEA-Nav | **0** | 8 | **Yes** | 90.9 |
| **VAC (ours)** | **0** | **0** | **Yes** | 87.5 |

**Bold:** best value in each column, including ties. Collision counts are **final event totals for each displayed run**, including repeated events. Time is measured before playback acceleration. Goal arrival alone does not imply collision-free success.

## Method

<p align="center">
  <img src="assets/images/architecture.png" width="100%" alt="VAC architecture: planning, temporal revalidation, and velocity filtering"/>
</p>

- **Temporal planning.** Exploration and braking tracks provide candidate motions. The Safe-Time Contract revalidates their execution timing.
- **Age-aligned velocity filtering.** PALB aligns obstacle tracks to control time and projects the requested velocity subject to obstacle and actuator constraints.
- **Delayed backup analysis.** Separation and execution-coverage conditions specify when filtered execution can share a common delayed backup.

The analysis is conditional on a feasible relative-braking backup and full execution coverage. These conditions are not yet certified online.

## Simulation and real-world results

**Aggregate results reported in the paper**, separate from the illustrative recordings above.

### Simulation

Matched-filter evaluation with **240 trials per filter**.

| Evaluation | Reported result |
| :--- | :---: |
| VAC with PALB: collision-free goal-reaching rate | **87.9%** |
| Gain over the delay-aware CBF variant | **+5.0 percentage points** |
| PALB computation time: 95th percentile | **8.9 ms** |

**VAC demonstration · synchronized top-down and oblique views**

<!-- VIDEO_SLOT: vac_simulation_top, vac_simulation_oblique -->
![Complete VAC simulation run: synchronized top-down and oblique views at 6×](assets/previews/simulation.gif)

The complete **87.5 s** run is shown at **6×**. Both views depict the same trial.

### Real-world experiments

**Outdoor Go2 course · 10 methods · 30 valid trials per method.**

![Complete ten-method comparison of real-world success and manual takeover rates](assets/images/real_world_results.svg)

VAC records the **highest observed success rate (93.3%)**, the **lowest dynamic collision total (1)** and **lowest manual takeover rate (3.3%)**, with **zero static collisions**.

| Method | Success (%) ↑ | Static collisions ↓ | Dynamic collisions ↓ | Manual takeover (%) ↓ |
| :--- | :---: | :---: | :---: | :---: |
| Nav2 / DWA | 73.3 | 2 | 4 | 16.7 |
| NeuPAN | 80.0 | 1 | 3 | 13.3 |
| DPCBF | 83.3 | **0** | 2 | 13.3 |
| RVO2 | 76.7 | 1 | 4 | 13.3 |
| NavRL | 80.0 | 1 | 3 | 10.0 |
| REASAN | 86.7 | **0** | 2 | 6.7 |
| SEA-Nav | 86.7 | **0** | 2 | 10.0 |
| ABS | 83.3 | 1 | 2 | 10.0 |
| FAR | 73.3 | 1 | 2 | 16.7 |
| **VAC (ours)** | **93.3** | **0** | **1** | **3.3** |

**Table V, complete.** Bold marks the best result, including ties. Success means goal arrival **without collision or manual takeover**. Static and dynamic collisions are **event totals across all 30 trials per method**, not counts from the example video; repeated events in a trial are included. Manual takeover is the percentage of trials requiring intervention.

**Real-world demonstration · pedestrian-crossing excerpt at 1×**

<!-- VIDEO_SLOT: outdoor_full -->
<p align="center">
  <img src="assets/previews/outdoor.gif" width="360" alt="Outdoor Go2 pedestrian-crossing excerpt, 14.4–24.9 seconds of the source recording, shown at 1×; faces anonymized"/>
</p>

**10.5 s at 1×**, covering **14.4–24.9 s** of the approximately 25-second outdoor recording.

## Narrated overview

The full presentation covers the problem, geometric intuition, method, simulation comparison and real-world experiments in **2 min 59.9 s**, with English narration and embedded subtitles.

<!-- VIDEO_SLOT: overview -->
![Silent 18-second excerpt montage from the narrated VAC overview](assets/previews/overview_preview.gif)

*Silent preview: six 3-second excerpts from the presentation, each at its original speed.*

## Code availability

This repository provides anonymous demonstration materials for peer review. **The source code will be released upon acceptance of the paper.**
