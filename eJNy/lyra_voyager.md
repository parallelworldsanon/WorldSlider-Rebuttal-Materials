# Comparison with Lyra 2.0 and Voyager

**Methods**
- **Lyra 2.0:** per-frame 3D cache, built on Wan2.1-14B.
- **Voyager:** frame-0 point cloud, about 13B, released code.
- **WorldSlider:** ours, 2B.

**Protocol**
- **Clips:** the first nine clips of each evaluation list (MotionScape, Sekai, TartanAir).
- **Settings:** seed 0 and each method's official default inference settings, run on one H200.
- **Metric:** ViPE recovers each generated video's camera path, which is compared with the target path. Values are mean ± 1×SE.
  - Rotation error in degrees, lower is better.
  - Length-normalised translation error, lower is better.
- **Path length:** both baselines reconstruct the first frame with scale-free monocular depth (MoGe).
  - TartanAir: the metric target path is converted into each method's scene units.
  - MotionScape and Sekai: each method's default path length is used.

| Method | MS Rot. ↓ | MS Trans. ↓ | SK Rot. ↓ | SK Trans. ↓ | TA Rot. ↓ | TA Trans. ↓ | Visual collapses |
|---|---|---|---|---|---|---|---|
| Lyra 2.0 (14B) | **3.00±1.15** | **0.104±0.050** | **0.41±0.11** | **0.037±0.014** | 16.68±5.26 | 0.165±0.026 | 1 / 27 |
| Voyager (13B) | 12.66±4.45 | 0.147±0.035 | 1.01±0.31 | 0.043±0.018 | 29.24±5.92 | 0.379±0.034 | 6 / 27 |
| **WorldSlider (Ours, 2B)** | 5.04±3.03 | 0.108±0.049 | 1.26±0.33 | 0.099±0.049 | **5.26±1.03** | **0.087±0.012** | – |

ViPE recovered a camera path for every video. A visual collapse means the scene is lost in the video, for example fog, noise, a black frame or a frozen view. Collapsed videos are kept in the means.

## Generation cost (one H200, model load excluded)

| Method | Output | Sampling | Generation time / video (s) | Model load (s) | Peak GPU memory (GiB) |
|---|---|---|---|---|---|
| Lyra 2.0 (14B) | 161 frames @ 16 fps | 2 chunks × 35 steps, CFG | 848 | 51 | 74.6 |
| Voyager (13B) | 45 frames @ 24 fps | 50 steps, CFG | 552 | 32 | 74.2 |
| **WorldSlider (Ours, 2B)** | 93 frames @ 10 fps | 4 steps | **22.2** (denoising 8.7) | 89.6 | **58.7** |

## Examples

Each example shows trajectory errors, WorldSlider (blue border), Lyra 2.0 and Voyager. Click a preview to open the MP4.

### MotionScape (real drone footage)

[![ms](lyra_voyager/ms_Captivating_Autumn_Leaves_A_Visual_Feast_-_4K_FPV_Drone__segment_000.gif)](lyra_voyager/ms_Captivating_Autumn_Leaves_A_Visual_Feast_-_4K_FPV_Drone__segment_000.mp4)

[![ms](lyra_voyager/ms_CINEMATIC_FPV_MIXED_SPOTS_-_SWITZERLAND_GOPRO_HERO7_HYPERSMOOTH_MOJO_COLORED__segment_001.gif)](lyra_voyager/ms_CINEMATIC_FPV_MIXED_SPOTS_-_SWITZERLAND_GOPRO_HERO7_HYPERSMOOTH_MOJO_COLORED__segment_001.mp4)

[![ms](lyra_voyager/ms_Autumn_Adventure_Capturing_Fall_s_Finest_with_DJI_Action_5__segment_004.gif)](lyra_voyager/ms_Autumn_Adventure_Capturing_Fall_s_Finest_with_DJI_Action_5__segment_004.mp4)

[![ms](lyra_voyager/ms_Cloud_Chasing_A_Small_Drone_s_Journey_Skyward__segment_004.gif)](lyra_voyager/ms_Cloud_Chasing_A_Small_Drone_s_Journey_Skyward__segment_004.mp4)

[![ms](lyra_voyager/ms_Diving_The_Tallest_Skyscraper_in_China_Shanghai_FPV__segment_004.gif)](lyra_voyager/ms_Diving_The_Tallest_Skyscraper_in_China_Shanghai_FPV__segment_004.mp4)

[![ms](lyra_voyager/ms_Cinematic_FPV_Drone_Compilation_2026_DJI_AVATA_2_Best_Shots__segment_002.gif)](lyra_voyager/ms_Cinematic_FPV_Drone_Compilation_2026_DJI_AVATA_2_Best_Shots__segment_002.mp4)

### Sekai (real drone footage)

[![sk](lyra_voyager/sk_z6vdgE0RGkk_0053882_0054182.gif)](lyra_voyager/sk_z6vdgE0RGkk_0053882_0054182.mp4)

[![sk](lyra_voyager/sk_4XDxC4RtPcE_0054136_0054436.gif)](lyra_voyager/sk_4XDxC4RtPcE_0054136_0054436.mp4)

[![sk](lyra_voyager/sk_p4JFjhkZPUw_0179060_0179360.gif)](lyra_voyager/sk_p4JFjhkZPUw_0179060_0179360.mp4)

[![sk](lyra_voyager/sk_mRb4sFiHMPU_0196265_0196565.gif)](lyra_voyager/sk_mRb4sFiHMPU_0196265_0196565.mp4)

[![sk](lyra_voyager/sk_y3kqpvy7BhA_0041870_0042170.gif)](lyra_voyager/sk_y3kqpvy7BhA_0041870_0042170.mp4)

[![sk](lyra_voyager/sk_fH5IQKOuGFg_0210959_0211259.gif)](lyra_voyager/sk_fH5IQKOuGFg_0210959_0211259.mp4)

### TartanAir

[![ta](lyra_voyager/ta_SeasonalForestAutumn_P001_s01155.gif)](lyra_voyager/ta_SeasonalForestAutumn_P001_s01155.mp4)

[![ta](lyra_voyager/ta_Apocalyptic_P003_s00595.gif)](lyra_voyager/ta_Apocalyptic_P003_s00595.mp4)

[![ta](lyra_voyager/ta_WaterMillDay_P006_s00385.gif)](lyra_voyager/ta_WaterMillDay_P006_s00385.mp4)

[![ta](lyra_voyager/ta_BrushifyMoon_P003_s04235.gif)](lyra_voyager/ta_BrushifyMoon_P003_s04235.mp4)

[![ta](lyra_voyager/ta_GothicIsland_P001_s01575.gif)](lyra_voyager/ta_GothicIsland_P001_s01575.mp4)

[![ta](lyra_voyager/ta_CastleFortress_P002_s01855.gif)](lyra_voyager/ta_CastleFortress_P002_s01855.mp4)
