#A Simulator Of diff_wheels_robot And Vehicle Navigation

These ROS packages are used to simulate the environment of 3D navigation

---

## dependences

1. Based on indigo of Ubuntu 14.04
2. gazebo and gazebo_ros (I used gazebo7)
3. PCL(needed if you want use multiwire laser, it is required in package **block_laser**)

---

## introduce

There are five packages .

1. **block_laser** Multiwire laser plugin.You can change the paraments to simulate velodyne laser or other laser . The data is published in format of sensor_msgs::PointCloud2.
2. **diff_robot** Models of diff_wheels_robot.You can add block laser, hokuyo laser or kinect.(multiple_robot is testing)
3. **control_msgs** Messages of controlling the four_wheeled_car.
4. **control_plugin** A gazebo plugin of controlling the four_wheeled_car.You can control the car by joystick.
5. **vehicle_sim** Models of four_wheeled_car.Come form [car_demo](https://github.com/osrf/car_demo).(two_wheeled_bike is testing)
 
---

## usage

1. Just build the packages as common ROS packages.
2. `roslaunch diff_robot nav_sim.launch` to launch the robot simulation.
3. `roslaunch vehicle_sim vehicle_sim.launch` to launch the vehicle simulation.

## others

1. There may be some problems in building **block_laser**. I used `gazebo7`, `ignition-msgs0`and`ignition-transport3`.If the differences of version make the errors in building, you can `1.change the version` or `2.edit the file block_laser_16.cpp to adapte the API`.Good luck. 