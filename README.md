How to start a simulation environment in Gazebo 8.0 for the MAVOCAP/AirCap Project

Step 1. Make sure you followed the instructions to compile all the packages in the AirCap repository on gitlab. If not, get it from here: https://github.com/AIRCAP/AIRCAP .

Step 2. Clone the following in your catkin workspace (check whether it is already installed from main ros repository and pay attention to the forks):

	https://github.com/AIRCAP/rotors_simulator.git

Step 3. export GAZEBO_PLUGIN_PATH=${GAZEBO_PLUGIN_PATH}: <Path to rotors_simulator>/Gazebo_Plugins

Step 4. cd <Path to rotors_simulator>/Gazebo_Plugins
	mkdir build
	cmake ..
	make

Step 5. Open file <Path to AIRCAP repository>/scripts/simulation/setup_mavocap_gazebo.sh or 

Step 6. Add desired path for storing the rosbag log files in the line "LOGPATH="

Step 7. In a terminal :  chmod +x <Path to AIRCAP repository>/scripts/simulation/setup_mavocap_gazebo.sh

Step 8. Open two terminals

Step 9. Run a roscore in one terminal.

Step 10. Execute the following command in the second terminal:

     cd <Path to AIRCAP repository>/scripts/simulation;
     ./setup_mavocap_gazebo.sh <number_of_robots> <communication_success_rate_in_%> <experiment_name> 

***In gazebo we observe that the visualization in Gazebo is fast for 1 to 8 robots (<number_of_robots>). Above 8 robots the real time factor is generally near 0.1. The parameter defaults to 2 robots if not provided ***

***(Optional) <communication_success_rate_in_%> defaults to 100 if not provided ***

***(Optional) <experiment_name> defaults to  "gazebo_flight_$( date + '%s' )" ***

***(Optional) In a third terminal ***

Step 11. Use rqt_image_view to see the neural network detector outputs.

Step 12. run rviz for upto 8 UAVs  rosrun rviz rviz
