Hex Robotics Mechahand Model
============================

MuJoCo model for Hex Robotics mechahand v13: https://www.youtube.com/shorts/kJ4OLfqDy5U

![Screenshot of robot hand model in MuJoCo.](/assets/hexrobotics_mujoco_screenshot.png)

The MJCF `hex_hand_right.xml` describes the mechanics of the (right handed) robot hand in Meter Killogram Second (MKS) units.

The scene file `hex_scene_right.xml` sets up the robot hand to fidget with an orange egg thing.

This dextrous robot hand attempts to mimic a human hand in movement degrees of freedom and 
integrated sensors. The total set of inputs and outputs for the robot hand is:
* 25 degrees of freedom (DOF) with position sensors on each joint.
    - 4 DOF per finger x 5 fingers.
    - 2 DOF extra to enable opposable thumb and pinkie.
    - 3 DOF for the wrist.
* 20 driven joints with torque sensors on the motors.
* 5 passive joints linked by a spring mechanism providing torque sensing for the fingertips.
* 24 force sensors on the fingertips and palm (4 around the each fingertip and 4 in the palm).
* 1 accelerometer in the forearm.

In the physical hand the 20 motor channels can be commanded by either position seeking with 
configurable PID parameters. The custom motor driver implements current feedback and can finely 
control the motor current/torque with an on-board current PID loop, which also has configurable
parameters. The motor commands can also be linearly combined to obtain position seeking with
a torque offset to enable holding, or position seeking with a torque limit for delicate handling.

In the simulated hand the joints are simplified and driven directly via the position actuator. The
simplified model does not (yet) accurately model the tendon flexion and spring extension mechanism
nor the slight change in tendon lengths as the wrist rotates. In the MJCF model the joint torque 
values are accurate for the flexion movement but the finger extension is much weaker on the real robot.
