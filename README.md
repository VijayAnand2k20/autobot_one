## AUTOBOT_ONE

Completed a mobile robot from writing the URDF till autonomous navigation

Steps to run:

1. Run `colcon build --symlink-install`

2. Launch the main program by executing: `ros2 launch autobot_one launch_sim.launch.py`

3. Run `ros2 run twist_mux twist_mux --ros-args --params-file ./config/twist_mux.yaml -r cmd_vel_out:=diff_cont/cmd_vel_unstamped` to map the keyboard commands's output topic appropriately

4. Run `ros2 run teleop_twist_keyboard teleop_twist_keyboard --ros-args -r /cmd_vel:=/cmd_vel_joy` to activate keyboard control

5. Open rviz2 by running: `rviz2 -d ./config/main.rviz`

6. Launch the localization_launch file to use the obtained map or run `ros2 launch slam_toolbox online_async_launch.py slam_params_file:=./config/mapper_params_online_async.yaml use_sim_time:=true` and make sure to change the mode to mapping in the mapping params file to map a new world yourself.

7. Run `ros2 launch nav2_bringup navigation_launch.py`

8. After running the localization_launch file, use the 2D Pose Estimate to mark the position of your robot in rviz2

9. Open the nav2 panel in rviz2 and set waypoints to see your robot navigate through the environment.



Thanks to [Articulated Robotics](https://github.com/joshnewans/articubot_one/tree/humble) for providing such an extensive tutorial on building mobile robots with ROS2 and Nav2