# Unitree R1-D Description

Wheeled R1-D: differential drive, casters, 2-stage lift, waist yaw, dual 7-DoF arms, head pitch/yaw.

End effectors reuse `unitree_g1_description` hand macros (`type:=none` by default; `dex3` / `rubber_hand` / `revo2` available).

## Build

```bash
colcon build --packages-up-to unitree_r1d_description --symlink-install
```

## Visualize

```bash
ros2 launch robot_common_launch manipulator.launch.py robot:=unitree_r1d
ros2 launch robot_common_launch manipulator.launch.py robot:=unitree_r1d type:=dex3
```
