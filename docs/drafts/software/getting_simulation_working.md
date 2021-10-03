# Getting the simulation working

If you're here you're trying to get simulation working on the UAV machine. 

## What you will need
(https://github.com/PX4/PX4-Autopilot)[PX4 Gazebo] or (https://github.com/khancyr/ardupilot_gazebo)[Ardupilot Gazebo]

## First time set
1. Build PX4 or Ardupilot gazebo plugins

## Running simulation
1. run `roscore`
2. Run gazebo plugin
   * PX4: `roslaunch px4 mavros_posix_sitl.launch`
   * Ardupilot:
     * Terminal 1: `gazebo --verbose ardupilot_gazebo/worlds/iris_arducopter_runway.world`
     * Terminal 2: `cd ardupilot/ArduCopter && ./../Tools/autotest/sim_vehicle.py -f gazebo-iris --console --map`
3. Run Application
