

# 👁️NavGS: A 6-DoF Navigation Dataset and Record-n-Replay Software for Real-World 3DGS Scenes in VR

Zihao Ding¹, Cheng‑Tse Lee², Mufeng Zhu¹, Tao Guan¹, Yuan‑Chun Sun², Cheng‑Hsin Hsu², Yao Liu¹<br>
¹ Rutgers University | ² National Tsing Hua University<br>
\| [Webpage](https://symmru.github.io/EyeNavGS/) | ~~Full Paper~~ (link will be updated here soon)

-------------------------------------------------------------------------------------------------------

## Overview

The `👁️NavGS(EyeNavGS)` Dataset provides high-fidelity, 6-Degrees-of-Freedom (6-DoF) head pose and eye gaze traces recorded from 46 participants exploring twelve real-world scenes reconstructed using 3D Gaussian Splatting (3DGS). Collected with Meta Quest Pro headsets in free world-standing mode across two sites (Rutgers University and National Tsing Hua University), this dataset enables research in viewport prediction, adaptive streaming, 3D saliency, and foveated rendering in immersive VR environments.

---

## Repository Structure

```text
EyeNavGS_Rutgers_Dataset/
├── scene_setting.csv
└── dataset/
    ├── alameda/
    │   ├── user101_alameda.csv
    │   ├── user102_alameda.csv
    │   └── ...
    ├── berlin/
    │   ├── user101_berlin.csv
    │   ├── user102_berlin.csv
    │   └── ...
    └── ... (10 other scene folders)
```

* **scene\_setting.csv**: Metadata for each scene, including initial orientation, scale, and starting position.
* **dataset/**: Directory containing per-scene folders; each folder holds individual user trace CSV files named `{userID}_{scene}.csv`.

---

## Scene Settings (`scene_setting.csv`)

| Scene_Name | Quaternion (X,Y,Z,W)            | Scale | Initial\_Position (x, y, z) |
| ---------- | ------------------------------- | ----- | --------------------------- |
| truck      | -0.0896, 0.0000, 0.0000, 0.9960 | 0.76  | 0,2.1,-4                    |
| treehill   | -0.1961, 0.0000, 0.0000, 0.9806 | 1     | 2,1.4,2                     |
| train      | 0.0499, 0.0000, 0.0100, 0.9987  | 0.36  | 2,-1,6                      |
| stump      | -0.3950, 0.0000, 0.0000, 0.9187 | 1     | -1,2.65,-2.5                |
| room       | -0.2334, 0.0000, 0.0000, 0.9724 | 2     | 0,1.15,0                    |
| playroom   | -0.1961, 0.0000, 0.0000, 0.9806 | 2.7   | 0,0.88,0                    |
| drjohnson  | -0.3699, 0.0000, 0.5976, 0.7114 | 1     | 0,1.5,0                     |
| bicycle    | -0.1142, 0.0000, 0.0000, 0.9935 | 1.25  | 1.5,1.1,0                   |
| nyc        | -0.1483, 0.0000, 0.0000, 0.9888 | 0.64  | -1.6,4.4,4                  |
| london     | 0, 0, 0, 1                      | 0.53  | 18,12,-11                   |
| berlin     | 0.0299, 0.0000, -0.0599, 0.9978 | 0.8   | -1,1.8,-1.3                 |
| alameda    | -0.1867, 0.0000, 0.0000, 0.9824 | 0.64  | 3,2.6,-1                    |

* **Quaternion**: Corrects scene tilt and aligns with gravity.
* **Scale**: Maps virtual scene to real-world size.
* **Initial\_Position**: Starting camera offset for each scene.

---

## CSV Trace Format

Each `{userID}_{scene}.csv` file contains per-frame, per-eye records with the following columns:

* `ViewIndex` (0: left eye, 1: right eye)
* `FOV1`,`FOV2`,`FOV3`,`FOV4`: Field of view angles (radians) for left, right, top, bottom extents
* `PositionX`,`PositionY`,`PositionZ`: Eye position (i.e., head position offset by half of IPD) in the world space.
* `QuaternionX`,`QuaternionY`,`QuaternionZ`,`QuaternionW`: Head orientation quaternion in world space
* `GazePosX`,`GazePosY`,`GazePosZ`: Eye gaze position in world space
* `GazeQX`,`GazeQY`,`GazeQZ`,`GazeQW`: Eye gaze orientation quaternion in world space
* `Timestamp`: Time offset (milliseconds) from recording start

---

## Usage

1. **Download** this repository or **clone**:
   
   ```bash
   git clone https://github.com/symmru/EyeNavGS_Rutgers_Dataset.git
   ```

2. Use `scene_setting.csv` to retrieve scene initialization parameters.

3. **Visualize** or **replay** sessions via the open-source 👁️NavGS Record-n-Replay Software: [https://github.com/symmru/EyeNavGS_Software](https://github.com/symmru/EyeNavGS_Software).

---

## 👁️NavGS (EyeNavGS) BibTex

If you use this 👁️NavGS datase in your research, please cite:

```textile
@inproceedings{EyeNavGS,
    title={{EyeNavGS: A 6-DoF Navigation Dataset and Record-n-Replay Software for Real-World 3DGS Scenes in VR}},
    author={{Zihao Ding and Cheng-Tse Lee and Mufeng Zhu and Tao Guan and Yuan-Chun Sun and Cheng-Hsin Hsu and Yao Liu}},
    year={2025},
    month={May},
}
```

## License

This dataset is released under the Apache License, Version 2.0.
You may obtain a copy of the license at:

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software and data distributed under this license are distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the license for the specific language governing permissions and limitations under the license.
