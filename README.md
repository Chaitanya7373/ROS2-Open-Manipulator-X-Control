# ROS2-Open-Manipulator-X-Control
The repository includes four implementations:

## Forward Kinematics, Inverse Kinematics, and Pick and Place

- **Forward Kinematics Subscriber Node**: Calculates the end effector pose.
- **Inverse Kinematics Subscriber Node**: Includes a service client that receives the desired end effector pose from the user and returns the corresponding joint positions.
- **Pick and Place Node**: Executes a sequence where the robot moves to the calculated position, picks up the object, and places it. It incorporates an intermediate gripper position above the object for effective picking and lifting maneuvers.

## Looped Joint Position Update and Cartesian Control

- **JK Subscriber Node**: Offers two services—one that converts joint velocities to end effector velocities, and another that converts end effector velocities to joint velocities.
- **Incremental Node**: Supplies incremental position references to robot joints (`q_ref = q_ref_old + delta_q * sampling_time`), acting as a velocity controller for joint position goals.
- **Incremental Node for Cartesian Space**: Provides a constant positive velocity reference in a specified Cartesian direction, converts it to joint space velocities using the Jacobian, and feeds it as a reference to the incremental position node, enabling linear movement in the specified direction.

## PD Controller for End Effector

- **PD Controller**: Implements a PD controller to regulate the end effector position.
  - The controller reads the current joint position, receives position references, and publishes control efforts.

## MoveIt Configuration of Open Manipulator Arm

- **MoveIt Configuration**: Configuration setup for MoveIt with the open manipulator arm.
