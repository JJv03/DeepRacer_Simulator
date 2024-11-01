# deepRacer_simulator

## About the project

An open source library based on Gazebo and Ros to simulate DeepRacer. It has been developed on a Ubuntu 20.04 with Ros Noetic and Gazebo 11.11.0. 

## How to install

Clone the repository and execute the setup_deepracer.sh (do not use sudo, some commands may fail):

    git clone https://github.com/JJv03/deepRacer_simulator
    cd deepRacer_simulator
    chmod +x setup_deepracer.sh
    ./setup_deepracer.sh

Copy the deepracer_simulation files inside the ~/robot_ws/src/deepracer_simulation directory

## How to run

Use the following commands:

    cd ~/robot_ws
    source ~/robot_ws/devel/setup.bash
    catkin_make
    cd src/deepracer_simulation/launch
    roslaunch deepracer_simulation racetrack_with_racecar.launch world_name:=hard_track

[In case you have any errors](#possible-errors)
    
You can select between these three worlds: {easy_track | medium_track | hard_track}

## Useful commands:

Change speed:

    rostopic pub /<car_name>/<car_part>_wheel_velocity_controller/command std_msgs/Float64 "data: <value>" -r 10

Example use:

    rostopic pub /racecar/left_front_wheel_velocity_controller/command std_msgs/Float64 "data: 1.0" -r 10

Change wheel angle:

    rostopic pub /<car_name>/<car_side>_steering_hinge_position_controller/command std_msgs/Float64 "data: <value>" -r 10

Example use:

    rostopic pub /racecar/left_steering_hinge_position_controller/command std_msgs/Float64 "data: 0.0" -r 10

Use the camera:

    rqt_image_view

## Possible errors

In case you have this error:

    ERROR: cannot launch node of type [deepracer_simulation/servo_commands.py]: Cannot locate node of type [servo_commands.py] in package [deepracer_simulation]. Make sure file exists in package path and permission is set to executable (chmod +x)

Try to give execute rights to the file scripts/servo_commands.py (you can run this line from the launch directory to avoid changing directory, just for convenience):

    chmod +x ../scripts/servo_commands.py
