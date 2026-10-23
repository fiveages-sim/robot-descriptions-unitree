# Unitree Dex Description

Shared Unitree end effectors. Robots mount them through `UnitreeG1Eefs`.

| Macro | What it is |
|-------|------------|
| `UnitreeDex1` | Parallel gripper. `name` is `left` or `right`. Finger joints are independent prismatic joints. |
| `UnitreeDex3` | One-sided Dex3 hand. `name` + `direction` (`1` left, `-1` right). One mesh set; right places each mesh with a π roll about X. Palm mount stays on the robot. |

Meshes live in `meshes/dex1` and `meshes/dex3`.

ros2_control interfaces live next to the kinematic macros, the same way Revo2 and XHand do:

| Macro | Joints |
|-------|--------|
| `UnitreeDex1Interfaces` | `name` + `_gripper_joint` (command). `*_gripper_joint1` stays a URDF mimic; Gazebo adds a state-only interface. |
| `UnitreeDex3Interfaces` | `name` + `_hand_thumb/middle/index_*_joint` |

`eef_fixed:=true` emits nothing, matching the planning URDF. Host robots include `xacro/ros2_control/dex1.xacro` and `dex3.xacro` and call the macro for the active `type`.

## Visualize

```bash
ros2 launch robot_common_launch manipulator.launch.py robot:=unitree_dex
ros2 launch robot_common_launch manipulator.launch.py robot:=unitree_dex type:=dex3
```
