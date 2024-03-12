# ROS Commands Summary

This repository contains two markdown files outlining essential commands and tutorials for working with ROS (Robot Operating System). Below is a summary of each file:

## 1 - ROS [source + topics]

This file provides instructions on sourcing ROS, essential ROS commands, working with topics, Python tutorials, using RViz, and visualizing the ROS graph with `rqt_graph`.

### How to source ROS
- Instructions on how to source ROS environment variables, either by running a command in the terminal or by editing the `.bashrc` file.

### Roscore and Essential Commands
- Command to start `roscore` and manage multiple terminal windows efficiently.
- Commands for listing topics, publishing topics, subscribing to topics, and checking topic information.
- Tutorial on exploring different message types using `rostopic`.

### Python Tutorials
- Instructions on running basic tasks with Python packages in ROS.
- Explanation of the difference between `rosrun` and `roslaunch`.
- Tutorial on controlling a turtle in the TurtleSim environment using Python.

### RViz
- Command to launch RViz for visualization purposes in ROS.

### `rqt_graph`
- Command to visualize the ROS computation graph using `rqt_graph`.

## 2 - ROS [catkin_make nodes]

This file focuses on using `catkin_make` to build ROS packages, creating packages, writing publisher and subscriber nodes, and running them.

### Make Directory and Create a Package
- Instructions on creating a workspace directory and creating a new ROS package using `catkin_create_pkg`.

### Write Publisher and Subscriber Nodes with VSCode
- Instructions on writing simple Python nodes for publishing and subscribing to topics using rospy.
- Explanation of adding ROS logging levels (info, warning, error) and managing node execution with `rospy.spin()`.

### Publisher Node
- Code and instructions for creating a publisher node that publishes messages to a specified topic.

### Subscriber Node
- Code and instructions for creating a subscriber node that listens to messages from a specified topic.

### Additional Notes
- Tips on using VSCode for ROS development and managing Python environment versions.
- Tips on managing ROS nodes and topics effectively.

These files serve as comprehensive guides for beginners to get started with ROS development and familiarize themselves with essential commands and concepts.
