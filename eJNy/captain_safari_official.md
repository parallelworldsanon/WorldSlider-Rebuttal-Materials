# Head-to-head on Captain Safari's own showcased clips

These are the five Captain Safari clips that are public **together with their real footage**: the official demo and the four clips on its supplementary comparison page. The Captain Safari videos below are **the authors' own published outputs**; we did not re-run them.

**Setup**
- **WorldSlider** starts from the same first frame (the centre-square view) and follows the same camera trajectory. It uses no scene memory and runs a single pass.
- **Target trajectory**
  - Official demo: the camera poses the authors released.
  - The four comparison clips: the authors did not release poses, so the trajectory is recovered from the real clip.
- **Scoring**: the same protocol as Table 1 of the paper. ViPE recovers the camera path of each generated video, and we compare it with the camera path of the real clip:
  - rotation error in degrees (↓);
  - length-normalised translation error (↓);
  - AUC@30 (↑).
  - Captain Safari is scored on its full 16:9 output and shown centre-cropped.

| Clip | Rot. ↓ (WorldSlider / Captain Safari) | Trans. ↓ | AUC@30 ↑ |
|---|---|---|---|
| Official demo `0bb4eeb9_0` | **5.29** / 7.37 | **0.042** / 0.059 | **0.850** / 0.688 |
| `1cc10a3e_5` | **6.58** / 34.02 | **0.041** / 0.188 | **0.870** / 0.283 |
| `99421ffe_10` | **0.83** / 6.77 | **0.028** / 0.127 | **0.926** / 0.791 |
| `b67f708a_10` | **2.14** / 9.63 | **0.018** / 0.125 | **0.954** / 0.643 |
| `cb9a1f18_10` | **2.33** / 4.96 | **0.030** / 0.196 | **0.896** / 0.263 |
| **Mean (5 clips)** | **3.44** / 12.55 | **0.032** / 0.139 | **0.899** / 0.534 |

WorldSlider is better on every metric for all five clips.

**Video layout** (each row; slowed 2×; click a preview for the MP4)
- Columns, left to right: numbers | 3D camera paths | top view | WorldSlider | Captain Safari (authors' output).
- Black is the target camera path. Blue (WorldSlider) and purple (Captain Safari) are the camera paths recovered from each generated video.

### Official demo `0bb4eeb9_0`
[![demo](captain_safari_official/os_1_demo_0bb4eeb9_0.gif)](captain_safari_official/os_1_demo_0bb4eeb9_0.mp4)

### `1cc10a3e_5`
[![1cc10a3e_5](captain_safari_official/os_2_1cc10a3e_5.gif)](captain_safari_official/os_2_1cc10a3e_5.mp4)

### `99421ffe_10`
[![99421ffe_10](captain_safari_official/os_3_99421ffe_10.gif)](captain_safari_official/os_3_99421ffe_10.mp4)

### `b67f708a_10`
[![b67f708a_10](captain_safari_official/os_4_b67f708a_10.gif)](captain_safari_official/os_4_b67f708a_10.mp4)

### `cb9a1f18_10`
[![cb9a1f18_10](captain_safari_official/os_5_cb9a1f18_10.gif)](captain_safari_official/os_5_cb9a1f18_10.mp4)

All five clips in one synchronized grid: [all_5_clips.mp4](captain_safari_official/all_5_clips.mp4)
