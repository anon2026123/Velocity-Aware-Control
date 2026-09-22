<h1 align="center">VAC: Coupling Temporal Planning and Velocity Filtering<br>for Quadruped Navigation</h1>

<p align="center">
  <img src="assets/images/teaser.jpg" width="100%" alt="VAC: real-world experiments and simulated navigation"/>
</p>

<p align="center"><b>Quadruped navigation among moving obstacles under command delay and braking constraints.</b></p>

<p align="center">
  <a href="#code-availability"><img src="assets/images/review_status.svg" width="414" height="28" alt="Anonymous review materials; code will be released upon acceptance"/></a>
</p>

<p align="center">
  <a href="assets/videos/overview.mp4"><b>Overview video</b></a>
  &nbsp; · &nbsp;
  <a href="#dynamic-preview">Preview</a>
  &nbsp; · &nbsp;
  <a href="#ten-method-comparison">Comparison</a>
  &nbsp; · &nbsp;
  <a href="#method">Method</a>
  &nbsp; · &nbsp;
  <a href="#simulation-and-real-world-results">Results</a>
  &nbsp; · &nbsp;
  <a href="#videos">All videos</a>
</p>

---

**VAC** couples temporal planning with age-aligned velocity filtering for quadruped navigation in dynamic scenes.

> [!IMPORTANT]
> This anonymous repository provides demonstration videos and visual results for review.
> **The source code will be released upon acceptance of the paper.**

---

## Dynamic preview

Outdoor Go2 navigation through static obstacles and a moving pedestrian, alongside VAC navigation in simulation.

[![Real-world experiments at 1× and VAC simulation at 6×](assets/previews/hero.gif)](assets/videos/overview.mp4)

**Preview speeds:** real-world **1×**; simulation **6×**. These are two demonstration excerpts. The real-world image in the opening figure is a time montage.

[Real-world full recording · 25 s](assets/videos/outdoor_full.mp4) · [VAC simulation · oblique view · 87.5 s](assets/videos/vac_simulation_oblique.mp4) · [Top-down view · 87.5 s](assets/videos/vac_simulation_top.mp4)

---

## Ten-method comparison

**30 × 10 m** · **58 static obstacles** · **9 moving obstacles**. Both rows share a **6× playback** clock, with START below and GOAL above.

[![Ten-method dynamic-scene comparison in two synchronized rows](assets/previews/comparison.gif)](assets/videos/simulation_comparison.mp4)

**[Watch or download the comparison · 31 s](assets/videos/simulation_comparison.mp4)**

One recorded run per method. Counts are **final collision-event totals** for the displayed run; shorter recordings hold their final frame. Goal arrival does not necessarily mean a collision-free arrival.

<details>
<summary><b>Single-run outcomes and recording details</b></summary>

| Method | Static collisions | Dynamic collisions | Goal reached | Run time (s) |
| :--- | :---: | :---: | :---: | :---: |
| Nav2 (DWB) | 3 | 5 | Yes | 151.4 |
| NeuPAN | 0 | 5 | Yes | 84.6 |
| DPCBF | 0 | 7 | Yes | 109.9 |
| RVO2 (ORCA) | 0 | 1 | Yes | 105.3 |
| FAR | 0 | 0 | No | 180.0 (timeout) |
| ABS | 0 | 10 | Yes | 72.8 |
| NavRL | 1 | 10 | Yes | 101.4 |
| REASAN | 0 | 4 | Yes | 67.3 |
| SEA-Nav | 0 | 8 | Yes | 90.9 |
| **VAC (ours)** | **0** | **0** | **Yes** | **87.5** |

Time is elapsed run time before playback acceleration. Collision counts include repeated events. These individual runs are separate from the paper's aggregate evaluation.

The standalone VAC views and its comparison panel depict the same run. The outdoor preview is an excerpt of the full outdoor recording. Views and excerpts are not additional trials.

The simulation videos replay recorded navigation states; they are not new physics rollouts or a validation of contact dynamics. Each top-down panel uses the same complete-course crop and orientation. The oblique recording retains its full frame. Faces in the real-world material are anonymized.

</details>

---

## Method

<p align="center">
  <img src="assets/images/architecture.png" width="100%" alt="VAC architecture: planning, temporal revalidation, and velocity filtering"/>
</p>

- **Temporal planning.** Exploration and braking tracks provide candidate motions. The Safe-Time Contract revalidates their execution timing.
- **Age-aligned velocity filtering.** PALB aligns obstacle tracks to control time and projects the requested velocity subject to obstacle and actuator constraints.
- **Delayed backup analysis.** Separation and execution-coverage conditions specify when filtered execution can share a common delayed backup.

The analysis is conditional on a feasible relative-braking backup and full execution coverage. These conditions are not yet certified online.

---

## Simulation and real-world results

**Aggregate results reported in the paper**, separate from the illustrative recordings above.

### Simulation

Matched-filter evaluation with **240 trials per filter**.

| Evaluation | Reported result |
| :--- | :---: |
| VAC with PALB: collision-free goal-reaching rate | **87.9%** |
| Gain over the delay-aware CBF variant | **+5.0 percentage points** |
| PALB computation time: 95th percentile | **8.9 ms** |

### Real-world experiments

Outdoor Go2 evaluation with **30 trials per method**, across **ten methods**.

| Evaluation | VAC result |
| :--- | :---: |
| Success rate | **93.3%** |
| Manual takeover rate | **3.3%** |

---

## Videos

| Video | Duration | Playback / content |
| :--- | :---: | :--- |
| [Narrated overview](assets/videos/overview.mp4) | 2 min 59.9 s | Theory, simulation, and real-world experiments; English narration and embedded subtitles |
| [Ten-method comparison](assets/videos/simulation_comparison.mp4) | 31 s | All methods at 6×; shorter runs hold their final frame |
| [Real-world experiments](assets/videos/outdoor_full.mp4) | 25 s | Full outdoor recording at 1× |
| [VAC simulation: top-down](assets/videos/vac_simulation_top.mp4) | 87.5 s | Full VAC run at 1×; START below, GOAL above |
| [VAC simulation: oblique](assets/videos/vac_simulation_oblique.mp4) | 87.5 s | Same VAC run at 1× from the oblique view |

GIFs are silent previews. Open the MP4 links for full-quality playback or download.

---

## Code availability

This repository currently contains demonstration materials. **The source code will be released upon acceptance of the paper.**
