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



  
