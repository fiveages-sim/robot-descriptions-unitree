# Unitree H2D Description

Wheeled H2D: base, waist heave and pitch, dual 7-DoF arms, head, and the Dex1 gripper.

The gripper is `UnitreeDex1` in `unitree_dex_description`, mounted by
`UnitreeG1Eefs` with `type:=dex1`. `h2d.urdf` is the original CAD export.

## Control

- Split: `ocs2_arm_controller` (dual arms, `config/ocs2/task.info`) + `body_joint_controller` + `head_joint_controller` + `left/right_gripper_controller`
- Full body: `ocs2_wbc_controller` (`config/ocs2/fixed_base_tcp.info`) — waist×2 + head×2 + arms×14
- Grippers: `adaptive_gripper_controller` on `left/right_gripper_joint` (`*_gripper_joint1` mimics)

## Build

```bash
colcon build --packages-up-to h2d_description --symlink-install
```

## Visualize

```bash
ros2 launch robot_common_launch manipulator.launch.py robot:=h2d
ros2 launch robot_common_launch manipulator.launch.py robot:=h2d type:=none
```
