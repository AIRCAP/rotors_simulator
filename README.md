How to start a simulation environment in Gazebo 8.0 for the MAVOCAP/AirCap Project

Step 1. Make sure you followed the instructions to compile all the packages in the MAVOCAP repository on gitlab. If not, get it from here: https://gitlab.tuebingen.mpg.de/aahmad/MAVOCAP . You will have to replace 'aamir' by your username. For that you need an account on mpi gitlab (It is automatically there if you are an internal employee) and then you need to request Aamir Ahmad to make you a member of this gitlab project.

Step 2. Clone the following in your catkin workspace (check whether it is already installed from main ros repository and pay attention to the forks):

1. https://github.com/ethz-asl/mav_comm.git
2. https://github.com/aamirahmad/rotors_simulator.git
3. cd rotors_simulator (check why this is necessary but seems like it is important to clone the next repos inside)
4. https://github.com/catkin/catkin_simple.git
5. https://github.com/ethz-asl/yaml_cpp_catkin.git
Step 3. Make sure you have Gazebo 8 installed. 

Step 4. export GAZEBO_PLUGIN_PATH=${GAZEBO_PLUGIN_PATH}: <Path to MAVOCAP repository>/Gazebo_Plugins

Step 5. export GAZEBO_MODEL_PATH=${GAZEBO_MODEL_PATH}: <Path to MAVOCAP repository>/Gazebo_Models

Step 6. cd <Path to MAVOCAP repository>/Gazebo_Plugins
	mkdir build
	cmake ..
	make

Step 4. Open file <Path to MAVOCAP repository>/Packages/simulation/perception_formation/scripts/experiment_mavocap_gazebo.sh

sTEP 5. Add desired path for storing the rosbag log files in the line "LOGPATH="

STEP 6. In a terminal :  chmod +x <Path to MAVOCAP repository>/Packages/simulation/perception_formation/scripts/experiment_mavocap_gazebo.sh

Step 7. Open two terminals

Step 8. Run a roscore in one terminal.

Step 9. Execute the following command in the second terminal:

     cd <Path to MAVOCAP repository>/Packages/simulation/perception_formation/scripts
     ./setup_mavocap_gazebo.sh <number_of_robots> <communication_success_rate_in_%> <experiment_name> 

*** In gazebo we observe that the visualization in Gazebo is fast for 1 to 8 robots (<number_of_robots>). Above 8 robots the real time factor is generally near 0.1. The parameter defaults to 2 robots if not provided***
*** (Optional) <communication_success_rate_in_%> defaults to 100 if not provided***
*** (Optional) <experiment_name> defaults to  "gazebo_flight_$( date + '%s' )"***

***(Optional) In a third terminal ***
 Step 10. Use rqt_image_view to see the neural network detector outputs.
 Step 11. run rviz for upto 8 UAVs  rosrun rviz rviz -d <Path to MAVOCAP repository>/rviz_config/CNN_DQMPC_8UAVS.rviz
