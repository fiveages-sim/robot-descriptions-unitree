# Unitree G1-D Description

Wheeled G1-D: AGV chassis, 3-stage lift, pitch/yaw mount, dual 7-DoF arms, Dex3 hands.

Arms, head, and end effectors are reused from `unitree_g1_description`.

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

Upstream kinematics from Unitree G1-D URDF. Arm visuals use the repainted G1 OBJ meshes.
