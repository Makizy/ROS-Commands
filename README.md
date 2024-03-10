# ROS-Commands

## How to source ROS
- Run the cmd in termianl:  <br>
> in this way you have to source every time. It is usefull when you are using ROS1 and ROS2 at the same time.
```
source /opt/ros/noetic/setup.bash
```
or 
- Run the cmd in termianl:
  
```
 gedit ~/.bashrc
```
  then paste the source code `source /opt/ros/noetic/setup.bash` in the last line of the text file that has opened.

## Roscore and a few essential commands

- run the cmd in termianl:  <br>
> This cmd will open ROS. Master is now activated

```
roscore
```
now open another window in terminal 

> shortcut = ctrl + shift + t <br>
> Toggle between windows = alt + number window

### Topics

> we are writing a variable in a topic in ros without node
> 
Run:

```
rostopic list
```

- Publishing a topic
> std_msgs = Standard Messages

```
rostopic pub /my_topic std_msgs/String " Hello World"
```

Open another window and run `rostopic list`, `/my_topic` should be added.

- With `echo` cmd we will see Hello world being published.
  Run in a new terminal:

```
rostopic echo /my_topic
```




- `r10` rate 10 Hz will be published

```
rostopic pub -r10 /my_topic std_msgs/String " Hello World"
```

Run `rostopic echo /my_topic` in a new terminal to see the results


- Diffrent types of `std_msgs`:

    - paste the cmd in a new terminal and tab a few times to see the types of `std_msgs` that can be used:

```
rostopic pub /mytopic std_msgs/
```

- run in the terminal to publish 2 with `Float32`

```
rostopic pub -r10 /my_topic std_msgs/Float32 2.0
```
Run `rostopic echo /my_topic` in a new terminal to see the results

- `rostopic info` information about the node and publisher and subscriber will be printed.

```
rostopic info /rosout
```

## Python Tutorials

Run some simple tasks with python packages on ros

> [!IMPORTANT]
> `rosrun` is for activating a node and `roslaunch` is for activating a package


> [!NOTE]
> `rosrun <package> <node>`
> 
```
rosrun turtlesim trutlesim_node
```
It should open like this: <br>
![image](https://github.com/Makizy/ROS-Commands/assets/53753128/2f2b67e3-6b28-413c-b22e-c03d990d293e)


- open another window in terminal and run:

```
rosrun turtlesim turtle_teleop_key
```

  Now use the arrow keys in keybord to move the turtle.
  > [!CAUTION]
  > Be sure that you are using the arrow keys on the terminal and not TurtleSim

![image](https://github.com/Makizy/ROS-Commands/assets/53753128/8349055b-02cb-4a39-88aa-ecb387aa7a66)


## Rviz

- Run in terminal after running `roscore` in another tap:

```
rviz rviz
```

![image](https://github.com/Makizy/ROS-Commands/assets/53753128/828269cf-2db2-4567-9413-de119c2825c8)


## `rqt_graph`

Sometimes we have too many topics and nodes with `rqt_graph` we can visualize what is happening.

```
rqt_graph
```

![image](https://github.com/Makizy/ROS-Commands/assets/53753128/d0a06628-97b3-48d2-86c9-f7ef10c87bf4)


