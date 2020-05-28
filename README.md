# Robotics-Software-Engineering-Nanodegree_GoChaseIt

# Goal
In this project, you should create two ROS packages inside the catkin_ws/src file: the drive_bot and the ball_chaser. The goal is to use the two ROS packages along with the robot and world created in BuildMyWorld to make the robot move towards a white ball when the ball is in view. 

# Summary of Tasks
Create drive_bot:  
1. Create a my_robot ROS package to hold your robot, the white ball, and the world.  

2. Design a differential drive robot with the Unified Robot Description Format. Add two sensors to your robot: a lidar and a camera. Add Gazebo plugins for your robot’s differential drive, lidar, and camera. The robot you design should be significantly different from the one presented in the project lesson. Implement significant changes such as adjusting the color, wheel radius, and chassis dimensions.  

3. House your robot inside the world you built in the Build My World project.  

4. Add a white-colored ball to your Gazebo world and save a new copy of this world.  

5. The world.launch file should launch your world with the white-colored ball and your robot.  

Create ball_chaser:  

6. Create a ball_chaser ROS package to hold your C++ nodes.  

7. Write a drive_botC++ node that will provide a ball_chaser/command_robot service to drive the robot by controlling its linear x and angular z velocities. The service should publish to the wheel joints and return back the requested velocities.  

8. Write a process_image C++ node that reads your robot’s camera image, analyzes it to determine the presence and position of a white ball. If a white ball exists in the image, your node should request a service via a client to drive the robot towards it.  

9. The ball_chaser.launch should run both the drive_bot and the process_image nodes.  

10. The robot you design in this project will be used as a base model for all your upcoming projects in this Robotics Software Engineer Nanodegree Program.  

# Project Requirements
Gazebo >= 7.0  

# Project Setup
Run Update On Linux Command Line:   
```bash
$ sudo apt-get update && sudo apt-get upgrade -y
```  


# Project Directory
 ```bash
.Project2                          # Go Chase It Project
    ├── my_robot                       # my_robot package                   
    │   ├── launch                     # launch folder for robot and world launch files   
    │   │   ├── robot_description.launch
    │   │   ├── world.launch
    │   ├── meshes                     # meshes folder for robot's sensors
    │   │   ├── hokuyo.dae
    │   ├── urdf                       # urdf folder for robot's xarco files
    │   │   ├── my_robot.gazebo
    │   │   ├── my_robot.xacro
    │   ├── world                      # world folder for world files
    │   │   ├── myworld.world
    │   ├── CMakeLists.txt             # compiler instructions
    │   ├── package.xml                # package info
    ├── ball_chaser                    # ball_chaser package                   
    │   ├── launch                     # launch folder for launch files   
    │   │   ├── ball_chaser.launch
    │   ├── src                        # source folder for C++ scripts
    │   │   ├── drive_bot.cpp          # C++ script that moves the robot
    │   │   ├── process_images.cpp     # C++ script that detects if a white ball is in sight
    │   ├── srv                        # service folder for ROS services
    │   │   ├── DriveToTarget.srv
    │   ├── CMakeLists.txt             # compiler instructions
    │   ├── package.xml                # package info                  
    └──                                  
```

# Run Instructions
Create a workspace:    
```bash
$ mkdir -p /home/workspace/catkin_ws/src
$ cd /home/workspace/catkin_ws/src
```   

Clone this git repository in src:    
```bash
git clone https://github.com/dereklau33/Robotics-Software-Engineering-Nanodegree_GoChaseIt.git
```  

Build package:  
```bash
$ cd /home/workspace/catkin_ws
source devel/setup.bash
catkin_make
```

Launch Simulation of the Robot in Gazebo:
```bash
$ roslaunch my_robot world.launch
```

Run Drive Bot and Process Image Packages:   
```bash
$ roslaunch ball_chaser ball_chaser.launch
```

Visualize Robot Camera Images  
```bash
$ rosrun rqt_image_view rqt_image_view
```

Place the White Ball in Front of the Robot by Clicking and Dragging so the Robot Will Chase After the Ball
