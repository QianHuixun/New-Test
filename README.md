---
license: apache-2.0
language:
  - en
  - zh
task_categories:
  - robotics
tags:
  - RoboCOIN
  - LeRobot
frame_range: 1K-10K
configs:
- config_name: default
  data_files: data/*/*.parquet
---

# G1edu-u3_place_plastic_bowl_ag

## 📋 Overview

This dataset uses an extended format based on LeRobot and is fully compatible with LeRobot.

**Robot Type:** `G1edu-u3`
 | **Codebase Version:** `v2.1`
**End-Effector Type:** `three_finger_hand`

## 🏠 Scene Types

This dataset covers the following scene types:
- `home`


## 🤖 Atomic Actions

This dataset includes the following atomic actions:
- `pick`
- `place`


## 📊 Dataset Statistics

| Metric | Value |
|--------|-------|
| **Total Episodes** | 38 |
| **Total Frames** | 7219 |
| **Total Tasks** | 1 |
| **Total Videos** | 38 |
| **Total Chunks** | 1 |
| **Chunk Size** | 39 |
| **FPS** | 30 |
| **Dataset Size** | 116.0MB |


## 👥 Authors

### Contributors
This dataset is contributed by:
- [RoboCOIN](https://flagopen.github.io/RoboCOIN/) - RoboCOIN Team


## 🔗 Links

- **🏠 Homepage:** [https://flagopen.github.io/RoboCOIN/](https://flagopen.github.io/RoboCOIN/)
- **📄 Paper:** [https://arxiv.org/abs/2511.17441](https://arxiv.org/abs/2511.17441)
- **💻 Repository:** [https://github.com/FlagOpen/RoboCOIN](https://github.com/FlagOpen/RoboCOIN)
- **🌐 Project Page:** [https://flagopen.github.io/RoboCOIN/](https://flagopen.github.io/RoboCOIN/)
- **🐛 Issues:** [https://github.com/FlagOpen/RoboCOIN/issues](https://github.com/FlagOpen/RoboCOIN/issues)
- **📜 License:** apache-2.0

## 🏷️ Dataset Tags

- `RoboCOIN`
- `LeRobot`


## 🎯 Task Descriptions

### Primary Tasks
Pick up the crumpled paper
Pick up the empty bottle
Pick up the leftover food
Pick up the metal bowl
Pick up the metal bowl
Pick up the plastic bowl
Pick up the plastic bowl
Place the metal bowl
Place the metal bowl
Place the plastic bowl
Place the plastic bowl

### Sub-Tasks
This dataset includes 4 distinct subtasks:

1. **End** 
2. **null** 
3. **Place the plastic bowl on the table with left gripper** 
4. **Place the plastic bowl on the table with right gripper** 


## 🎥 Camera Views

This dataset includes 1 camera views.

## 🏷️ Available Annotations

This dataset includes rich annotations to support diverse learning approaches:

### Subtask Annotations
- **Subtask Segmentation**: Fine-grained subtask segmentation and labeling
### Scene Annotations
- **Scene-level Descriptions**: Semantic scene classifications and descriptions
### End-Effector Annotations
- **Direction**: Movement direction classifications for robot end-effectors
- **Velocity**: Velocity magnitude categorizations during manipulation
- **Acceleration**: Acceleration magnitude classifications for motion analysis


### Gripper Annotations
- **Gripper Mode**: Open/close state annotations for gripper control
- **Gripper Activity**: Activity state classifications (active/inactive)


### Additional Features
- **End-Effector Simulation Pose**: 6D pose information for end-effectors in simulation space
  - Available for both state and action
- **Gripper Opening Scale**: Continuous gripper opening measurements
  - Available for both state and action


## 📂 Data Splits

The dataset is organized into the following splits:

- **Training**: Episodes 0:37


## 📁 Dataset Structure

This dataset follows the LeRobot format and contains the following components:

### Data Files
- **Videos**: Compressed video files containing RGB camera observations
- **State Data**: Robot joint positions, velocities, and other state information
- **Action Data**: Robot action commands and trajectories
- **Metadata**: Episode metadata, timestamps, and annotations

### File Organization
- **Data Path Pattern**: `data/chunk-{episode_chunk:03d}/episode_{episode_index:06d}.parquet`
- **Video Path Pattern**: `videos/chunk-{episode_chunk:03d}/{video_key}/episode_{episode_index:06d}.mp4`
- **Chunking**: Data is organized into 1 chunk(s)
of size 39


### Features Schema

The dataset includes the following features:

#### Visual Observations
- **observation.images.ego_view**: video
  - FPS: 30
  - Codec: h264

#### State and Action- **observation.state**: float32- **action**: float32

#### Temporal Information
- **timestamp**: float64
- **frame_index**: int64
- **episode_index**: int64
- **index**: int64
- **task_index**: int64


#### Annotations
- **subtask_annotation**: int32
- **scene_annotation**: int32


#### Motion Features
- **eef_sim_pose_state**: float32
  - Dimensions: left_eef_pos_x, left_eef_pos_y, left_eef_pos_z, left_eef_ori_x, left_eef_ori_y, left_eef_ori_z, right_eef_pos_x, right_eef_pos_y, right_eef_pos_z, right_eef_ori_x, right_eef_ori_y, right_eef_ori_z
- **eef_sim_pose_action**: float32
  - Dimensions: left_eef_pos_x, left_eef_pos_y, left_eef_pos_z, left_eef_ori_x, left_eef_ori_y, left_eef_ori_z, right_eef_pos_x, right_eef_pos_y, right_eef_pos_z, right_eef_ori_x, right_eef_ori_y, right_eef_ori_z
- **eef_direction_state**: int32
  - Dimensions: left_eef_direction, right_eef_direction
- **eef_direction_action**: int32
  - Dimensions: left_eef_direction, right_eef_direction
- **eef_velocity_state**: int32
  - Dimensions: left_eef_velocity, right_eef_velocity
- **eef_velocity_action**: int32
  - Dimensions: left_eef_velocity, right_eef_velocity
- **eef_acc_mag_state**: int32
  - Dimensions: left_eef_acc_mag, right_eef_acc_mag
- **eef_acc_mag_action**: int32
  - Dimensions: left_eef_acc_mag, right_eef_acc_mag


#### Gripper Features


### Meta Information

The complete dataset metadata is available in [meta/info.json](meta/info.json):

```json
{"codebase_version": "v2.1", "robot_type": null, "total_episodes": 38, "total_frames": 7219, "total_tasks": 1, "total_videos": 38, "total_chunks": 1, "chunks_size": 39, "fps": 30, "splits": {"train": "0:37"}, "data_path": "data/chunk-{episode_chunk:03d}/episode_{episode_index:06d}.parquet", "video_path": "videos/chunk-{episode_chunk:03d}/{video_key}/episode_{episode_index:06d}.mp4", "features": {"observation.images.ego_view": {"dtype": "video", "shape": [480, 640, 3], "names": ["height", "width", "channel"], "info": {"video.height": 480, "video.width": 640, "video.codec": "h264", "video.pix_fmt": "yuv420p", "video.is_depth_map": false, "video.fps": 30, "video.channels": 3, "has_audio": false}}, "observation.state": {"dtype": "float32", "shape": [30], "names": ["left_arm_joint_1_rad", "left_arm_joint_2_rad", "left_arm_joint_3_rad", "left_arm_joint_4_rad", "left_arm_joint_5_rad", "left_arm_joint_6_rad", "left_arm_joint_7_rad", "right_arm_joint_1_rad", "right_arm_joint_2_rad", "right_arm_joint_3_rad", "right_arm_joint_4_rad", "right_arm_joint_5_rad", "right_arm_joint_6_rad", "right_arm_joint_7_rad", "left_hand_joint_1_rad", "left_hand_joint_2_rad", "left_hand_joint_3_rad", "left_hand_joint_4_rad", "left_hand_joint_5_rad", "left_hand_joint_6_rad", "left_hand_joint_7_rad", "right_hand_joint_1_rad", "right_hand_joint_2_rad", "right_hand_joint_3_rad", "right_hand_joint_4_rad", "right_hand_joint_5_rad", "right_hand_joint_6_rad", "right_hand_joint_7_rad"]}, "action": {"dtype": "float32", "shape": [30], "names": ["left_arm_joint_1_rad", "left_arm_joint_2_rad", "left_arm_joint_3_rad", "left_arm_joint_4_rad", "left_arm_joint_5_rad", "left_arm_joint_6_rad", "left_arm_joint_7_rad", "right_arm_joint_1_rad", "right_arm_joint_2_rad", "right_arm_joint_3_rad", "right_arm_joint_4_rad", "right_arm_joint_5_rad", "right_arm_joint_6_rad", "right_arm_joint_7_rad", "left_hand_joint_1_rad", "left_hand_joint_2_rad", "left_hand_joint_3_rad", "left_hand_joint_4_rad", "left_hand_joint_5_rad", "left_hand_joint_6_rad", "left_hand_joint_7_rad", "right_hand_joint_1_rad", "right_hand_joint_2_rad", "right_hand_joint_3_rad", "right_hand_joint_4_rad", "right_hand_joint_5_rad", "right_hand_joint_6_rad", "right_hand_joint_7_rad"]}, "timestamp": {"dtype": "float64", "shape": [1], "names": null}, "frame_index": {"dtype": "int64", "shape": [1], "names": null}, "episode_index": {"dtype": "int64", "shape": [1], "names": null}, "index": {"dtype": "int64", "shape": [1], "names": null}, "task_index": {"dtype": "int64", "shape": [1], "names": null}, "subtask_annotation": {"names": null, "dtype": "int32", "shape": [5]}, "scene_annotation": {"names": null, "dtype": "int32", "shape": [1]}, "eef_sim_pose_state": {"names": ["left_eef_pos_x", "left_eef_pos_y", "left_eef_pos_z", "left_eef_ori_x", "left_eef_ori_y", "left_eef_ori_z", "right_eef_pos_x", "right_eef_pos_y", "right_eef_pos_z", "right_eef_ori_x", "right_eef_ori_y", "right_eef_ori_z"], "dtype": "float32", "shape": [12]}, "eef_sim_pose_action": {"names": ["left_eef_pos_x", "left_eef_pos_y", "left_eef_pos_z", "left_eef_ori_x", "left_eef_ori_y", "left_eef_ori_z", "right_eef_pos_x", "right_eef_pos_y", "right_eef_pos_z", "right_eef_ori_x", "right_eef_ori_y", "right_eef_ori_z"], "dtype": "float32", "shape": [12]}, "eef_direction_state": {"names": ["left_eef_direction", "right_eef_direction"], "dtype": "int32", "shape": [2]}, "eef_direction_action": {"names": ["left_eef_direction", "right_eef_direction"], "dtype": "int32", "shape": [2]}, "eef_velocity_state": {"names": ["left_eef_velocity", "right_eef_velocity"], "dtype": "int32", "shape": [2]}, "eef_velocity_action": {"names": ["left_eef_velocity", "right_eef_velocity"], "dtype": "int32", "shape": [2]}, "eef_acc_mag_state": {"names": ["left_eef_acc_mag", "right_eef_acc_mag"], "dtype": "int32", "shape": [2]}, "eef_acc_mag_action": {"names": ["left_eef_acc_mag", "right_eef_acc_mag"], "dtype": "int32", "shape": [2]}}, "discarded_episode_indices": []}
```

### Directory Structure

The dataset is organized as follows (showing leaf directories with first 5 files only):

```
G1edu-u3_place_plastic_bowl_ag_qced_hardlink/
├── annotations/
│   ├── eef_acc_mag_annotation.jsonl
│   ├── eef_direction_annotation.jsonl
│   ├── eef_velocity_annotation.jsonl
│   ├── gripper_activity_annotation.jsonl
│   ├── gripper_mode_annotation.jsonl
│   └── (...)
├── data/
│   └── chunk-000/
│       ├── episode_000000.parquet
│       ├── episode_000001.parquet
│       ├── episode_000002.parquet
│       ├── episode_000003.parquet
│       ├── episode_000004.parquet
│       └── (...)
├── meta/
│   ├── episodes.jsonl
│   ├── episodes_stats.jsonl
│   ├── info.json
│   └── tasks.jsonl
└── videos/
    └── chunk-000/
        └── observation.images.ego_view/
            ├── episode_000000.mp4
            ├── episode_000001.mp4
            ├── episode_000002.mp4
            ├── episode_000003.mp4
            ├── episode_000004.mp4
            └── (...)
```


## 📞 Contact and Support

For questions, issues, or feedback regarding this dataset, please contact:
- **Email:** None
For questions, issues, or feedback regarding this dataset, please contact us.
### Support
For technical support, please open an issue on our GitHub repository.

## 📄 License

This dataset is released under the **apache-2.0** license.

Please refer to the LICENSE file for full license terms and conditions.


## 📚 Citation

If you use this dataset in your research, please cite:

```bibtex
@article{robocoin,
    title={RoboCOIN: An Open-Sourced Bimanual Robotic Data Collection for Integrated Manipulation},
    author={Shihan Wu, Xuecheng Liu, Shaoxuan Xie, Pengwei Wang, Xinghang Li, Bowen Yang, Zhe Li, Kai Zhu, Hongyu Wu, Yiheng Liu, Zhaoye Long, Yue Wang, Chong Liu, Dihan Wang, Ziqiang Ni, Xiang Yang, You Liu, Ruoxuan Feng, Runtian Xu, Lei Zhang, Denghang Huang, Chenghao Jin, Anlan Yin, Xinlong Wang, Zhenguo Sun, Junkai Zhao, Mengfei Du, Mingyu Cao, Xiansheng Chen, Hongyang Cheng, Xiaojie Zhang, Yankai Fu, Ning Chen, Cheng Chi, Sixiang Chen, Huaihai Lyu, Xiaoshuai Hao, Yequan Wang, Bo Lei, Dong Liu, Xi Yang, Yance Jiao, Tengfei Pan, Yunyan Zhang, Songjing Wang, Ziqian Zhang, Xu Liu, Ji Zhang, Caowei Meng, Zhizheng Zhang, Jiyang Gao, Song Wang, Xiaokun Leng, Zhiqiang Xie, Zhenzhen Zhou, Peng Huang, Wu Yang, Yandong Guo, Yichao Zhu, Suibing Zheng, Hao Cheng, Xinmin Ding, Yang Yue, Huanqian Wang, Chi Chen, Jingrui Pang, YuXi Qian, Haoran Geng, Lianli Gao, Haiyuan Li, Bin Fang, Gao Huang, Yaodong Yang, Hao Dong, He Wang, Hang Zhao, Yadong Mu, Di Hu, Hao Zhao, Tiejun Huang, Shanghang Zhang, Yonghua Lin, Zhongyuan Wang and Guocai Yao},
    journal={arXiv preprint arXiv:2511.17441},
    url = {https://arxiv.org/abs/2511.17441},
    year={2025}
    }
```

### Additional References

If you use this dataset, please also consider citing:
- LeRobot Framework: https://github.com/huggingface/lerobot

## 📌 Version Information

## Version History
- v1.0.0 (2025-11): Initial release