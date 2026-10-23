# Unitree G1-D Description

Wheeled G1-D: AGV chassis, 3-stage lift, pitch/yaw mount, dual 7-DoF arms, Dex3 hands (default).

Reuses from `unitree_g1_description`:

- `UnitreeG1Torso` (torso mesh, logo, torso IMU / D435 / Mid360)
- `UnitreeG1Arm`, `UnitreeG1Head`, `UnitreeG1Eefs` (`eefs.xacro`)

`torso_yaw_joint` (Yaw_Link → torso_link) keeps the official G1-D yaw limits, with
origin z reduced by 9.8 mm so the G1 torso frame sits on the lift stack.

## Control

- Split: `ocs2_arm_controller` (dual arms, `config/ocs2/task.info`) + `body_joint_controller`
- Full body: `ocs2_wbc_controller` (`config/ocs2/fixed_base_tcp.info`) — lift×2 + pitch + torso yaw + arms×14
- EE: `type:=dex3` → `left/right_hand_controller`; `type:=dex1` → `adaptive_gripper` on `*_gripper_joint`
- Wheels fixed by default; `chassis_joints_movable:=true` enables `diff_drive_controller`
- RViz: `config/rviz/fullbody.rviz` (Fixed Frame `world`) / `splitbody.rviz` (`base_footprint`)

## Build

```bash
colcon build --packages-up-to unitree_g1d_description --symlink-install
```

## Visualize

```bash
ros2 launch robot_common_launch manipulator.launch.py robot:=unitree_g1d
ros2 launch robot_common_launch manipulator.launch.py robot:=unitree_g1d type:=dex1
ros2 launch robot_common_launch manipulator.launch.py robot:=unitree_g1d type:=none
```

## Full-body / split control

```bash
ros2 launch ocs2_arm_controller full_body.launch.py robot:=unitree_g1d
ros2 launch ocs2_arm_controller full_body.launch.py robot:=unitree_g1d type:=dex1
ros2 launch ocs2_arm_controller full_body.launch.py robot:=unitree_g1d hardware:=isaac
ros2 launch ocs2_arm_controller split_body.launch.py robot:=unitree_g1d
```
