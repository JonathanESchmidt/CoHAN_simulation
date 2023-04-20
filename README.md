
# CoHAN Navigation

This package provides the configuration files and examples for the [CoHAN Planner](https://github.com/sphanit/CoHAN_Planner).

It uses slightly modified versions of [stage_ros](https://github.com/ros-simulation/stage_ros) simulator for simulating the robot and the humans. The modified version of ```stage_ros``` is already included.

# Installation
1. Download and build the package
	```
	cd cohan_ws/src
	git clone https://github.com/JonathanESchmidt/CoHAN_simulation -b master
	cd ..
	rosdep install --from-paths src --ignore-src --rosdistro=melodic -y
	catkin build
	```
	(install any other depencies if needed)
	
2. Install MORSE seperately before running its examples.
# Running the examples (Stage)
1. PR2 with two humans and stage GUI
	```
	roslaunch cohan_navigation stage_pr2_full.launch gui:=true map_name:=laas_adream localize:=amcl
	```
2. Running stage in fast mode
	```
	roslaunch cohan_navigation stage_pr2_full.launch fast_mode:=true map_name:=laas_adream localize:=fake
	```

# Possible Error
```
error: terminate called after throwing an instance of 'std::runtime_error'
  what():  Time is out of dual 32-bit range
```
This occurs if the simulator is not launched properly before the navigation due to some delayed communications. One solution is to launch the simulator separately and wait until it is completely launched before launching navigation. You can also control this delay using ```node_start_delay ``` argument of launch files.
