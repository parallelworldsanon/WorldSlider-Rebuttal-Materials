# Trajectory fidelity on five Captain Safari examples

On five examples from Captain Safari's demo and supplement, WorldSlider achieves a mean **AUC@30 of 0.899 vs. 0.534** using the trajectory-following metric reported in their paper. Mean **rotation error is 3.44° vs. 12.55°** and **translation error is 0.032 vs. 0.139** (WorldSlider / Captain Safari). We reproduced the Captain Safari results using its official example code.

## Synchronized video comparisons

### `1cc10a3e_5`

[![1cc10a3e_5](captain_safari_official/os_2_1cc10a3e_5.gif)](captain_safari_official/os_2_1cc10a3e_5.mp4)

Black is the reference path, blue is WorldSlider, and purple is Captain Safari. Click any preview for the MP4, or [watch all five clips together](captain_safari_official/all_5_clips.mp4).

### Official demo `0bb4eeb9_0`

[![demo](captain_safari_official/os_1_demo_0bb4eeb9_0.gif)](captain_safari_official/os_1_demo_0bb4eeb9_0.mp4)

### `99421ffe_10`

[![99421ffe_10](captain_safari_official/os_3_99421ffe_10.gif)](captain_safari_official/os_3_99421ffe_10.mp4)

### `b67f708a_10`

[![b67f708a_10](captain_safari_official/os_4_b67f708a_10.gif)](captain_safari_official/os_4_b67f708a_10.mp4)

### `cb9a1f18_10`

[![cb9a1f18_10](captain_safari_official/os_5_cb9a1f18_10.gif)](captain_safari_official/os_5_cb9a1f18_10.mp4)

## Per-clip results

Each cell lists **WorldSlider / Captain Safari**.

| Clip | AUC@30 ↑ | Rotation error (°) ↓ | Translation error ↓ |
| --- | ---: | ---: | ---: |
| Official demo `0bb4eeb9_0` | **0.850** / 0.688 | **5.29** / 7.37 | **0.042** / 0.059 |
| `1cc10a3e_5` | **0.870** / 0.283 | **6.58** / 34.02 | **0.041** / 0.188 |
| `99421ffe_10` | **0.926** / 0.791 | **0.83** / 6.77 | **0.028** / 0.127 |
| `b67f708a_10` | **0.954** / 0.643 | **2.14** / 9.63 | **0.018** / 0.125 |
| `cb9a1f18_10` | **0.896** / 0.263 | **2.33** / 4.96 | **0.030** / 0.196 |
| **Mean (5 clips)** | **0.899** / 0.534 | **3.44** / 12.55 | **0.032** / 0.139 |

Captain Safari generates convincing egocentric flight. In the recovered-path overlay for `1cc10a3e_5`, its camera path visibly deviates from the reference.

## Evaluation setup

Rotation and translation errors follow the evaluation protocol in our paper. [Captain Safari example code](https://github.com/johnson111788/Captain-Safari/blob/main/captain_safari/examples/wanvideo/model_training/validate_lora/Wan2.2-Fun-5B-Control-Camera_Captain-Safari.py) · [AUC@30 in Captain Safari, Table 1](https://arxiv.org/html/2511.22815v1)

The official demo uses the released camera poses. The four supplementary clips use trajectories reconstructed from the source footage. [Captain Safari demo](https://johnson111788.github.io/open-safari/) · [Supplementary comparisons](https://johnson111788.github.io/captain-safari-supp/#comparisons)
