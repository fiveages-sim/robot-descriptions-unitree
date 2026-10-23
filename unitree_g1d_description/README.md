# Unitree G1-D Description

Wheeled G1-D: AGV chassis, 3-stage lift, pitch/yaw mount, dual 7-DoF arms, Dex3 hands.

Reuses from `unitree_g1_description`:

- `UnitreeG1Torso` (torso mesh, logo, torso IMU / D435 / Mid360)
- `UnitreeG1Arm`, `UnitreeG1Head`, `hand.xacro`

`torso_yaw_joint` (Yaw_Link → torso_link) keeps the official G1-D yaw limits, with
origin z reduced by 9.8 mm so the G1 torso frame sits on the lift stack.

## Build

```bash
colcon build --packages-up-to unitree_g1d_description --symlink-install
```

## Visualize

```bash
ros2 launch robot_common_launch manipulator.launch.py robot:=unitree_g1d
ros2 launch robot_common_launch manipulator.launch.py robot:=unitree_g1d type:=rubber_hand
ros2 launch robot_common_launch manipulator.launch.py robot:=unitree_g1d type:=none
```
