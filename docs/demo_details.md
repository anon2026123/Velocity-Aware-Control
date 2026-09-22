# Demonstration details

## Recording scope

The comparison contains one recording per method in a 30 × 10 m dynamic scene with 58 static and 9 moving obstacles. Results in this document describe those individual recordings. They are not the aggregate evaluation in the paper.

Static and dynamic values count collision events, including repeated events. Goal indicates whether the run reached its goal, irrespective of collisions. Time is elapsed run time in seconds, not the duration of the accelerated comparison video. FAR terminated at the timeout limit.

| Method | Static events | Dynamic events | Goal reached | Time (s) |
| :--- | ---: | ---: | :---: | ---: |
| Nav2 | 3 | 5 | Yes | 151.4 |
| NeuPAN | 0 | 5 | Yes | 84.6 |
| DPCBF | 0 | 7 | Yes | 109.9 |
| RVO2 | 0 | 1 | Yes | 105.3 |
| FAR | 0 | 0 | No (timeout) | 180.0 |
| ABS | 0 | 10 | Yes | 72.8 |
| NavRL | 1 | 10 | Yes | 101.4 |
| REASAN | 0 | 4 | Yes | 67.3 |
| SEA-Nav | 0 | 8 | Yes | 90.9 |
| VAC | 0 | 0 | Yes | 87.5 |

The displayed method labels and statistics follow the corrected recording annotations. The standalone VAC views and its comparison panel represent the same run; they should not be counted as independent trials.

## Playback and processing

| Video | Playback | Processing |
| :--- | :---: | :--- |
| Overview | Mixed; labeled in each scene | English narration, theory animation, simulation and hardware footage |
| Ten-method comparison | 6× for every method | Same course crop and orientation; final-frame holds after shorter recordings finish |
| VAC top-down run | 1× | Full course crop, 90-degree rotation, resize; full recorded duration retained |
| VAC oblique run | 1× | Resize; full frame and recorded duration retained |
| Outdoor full recording | 1× | Original portrait framing; face anonymization; no original audio |
| Outdoor pedestrian interaction | 1× | Excerpt at 14.4–24.9 s of the same outdoor recording |

The simulation images are rendered replays of recorded states; they are not a new physics rollout. Navigation evidence should be interpreted together with the paper's protocol and aggregate results.

## Availability

This repository currently contains demonstration materials. The source code will be released upon acceptance of the paper.
