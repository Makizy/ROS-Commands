# ROS directory and writing a node

## Make Directory

- make directory

```
makdir catkin_ws
```

to navigate to directory we use `cd` :

```
cd catkin_ws
```

> [!NOTE]
> use `ls` in directory to see the list.

> [!TIP]
> use `win + tab` to switch between terminal windows.

- run in terminal to make directory:
  similar to making in c++, it will make the file and check versions to make it excutable.  

  ```
  catkin_make
  ```
  
  - after making it, use `ls` in terminal. There should be 3 names like the picture bellow.
![image](https://github.com/Makizy/ROS-Commands/assets/53753128/413e2e7b-48d1-4b75-ad09-1a9b4586888a)

go to `src` with cd :
```
cd src
```

- in `src` we want to creat a package so we run in terminal:
> `catkin_creat_pkg <name_of the package> dependencies`<br>
> name_of the package = test_sub_pub<br>
> libreies dependencies = std_msgs, rospy, roscpp

```
catkin_create_pkg test_sub_pub std_msgs rospy roscpp
```

>`package.xml` has information about the creator of package and dependencies and ... <br>

  use `ls` to check.
  
> `CMakeLists.txt` link every libries and make the file excutable and we can make the version of libries campatible if needed.<br>

- now go to `test_sub_pub` with `cd`:

```
cd test_sub_pub
```

> in ` include` headers files are placed .h files which means are where libries located.<br>

> `src` is where source is.

> [!NOTE]
> when we want to write a code in `src`.

use `code src` cmd in terminal to open vscode and also folder src in vscode :

```
code src
```

It is preferable to use VScode to code.

> [!NOTE]
> Install usefull extentions in vscode : Python, CMake, ROS.

- we have to define what vesion of python we are using in the begining of the code:

```python
#!/usr/bin/env python3.8
```

>[!NOTE]
> For noetic use python3 and for melodic use python2

we import the needed libries:

```
import rospy
```

```python

#!/usr/bin/env python3.8

import rospy

if __name__ == '__main__':
    
    #creating a node with its name
    rospy.init_node('publisher_node') 
    
    # equal to print('Hello world)
    rospy.loginfo('Hello from publisher world')

```

- now to make our code excutable run the cmd in src  terminal:

```
chmod +x pub_python.py
```

now to run the code we use `python` cmd:

```
python3.8 pub_python.py 
```

now add warning and error :

```python
#!/usr/bin/env python3.8

import rospy

if __name__ == '__main__':
    
    #creating a node with its name
    rospy.init_node('publisher_node') 
    
    # equal to print('Hello world)
    rospy.loginfo('Hello from publisher world')
    
    #instead of loginfo for warning
    rospy.logwarn('This is a warning!!!')
    
    #instead of loginfo for error
    rospy.logerr('This is an error!!!')
```

and the result is lke this:
![image](https://github.com/Makizy/ROS-Commands/assets/53753128/94139696-0f4d-4792-af87-13a41d020054)

go to `~/catkin_ws$ ` in terminal with cd: 

> use 3 times

```
cd ..
```

use `catkin_make` :

```
catkin_make
```

this shows that our package is maked.
![image](https://github.com/Makizy/ROS-Commands/assets/53753128/f5f07e21-47ef-4940-a857-577745bba09c)

should also sourec this package with either this cmd:

```
source devel/setup.bash
```

or with :

```
gedit ~/.bashrc
```
and then add source `~/catkin_ws/devel/setup.bash` in the last line.

one of the ways we can check it our package has been made correctly.
use `rosrun test` + `tab`  if it completed the name of the package we will know it has been made correctly.

run the node with `rosrun`:

```
rosrun test_sub_pub pub_python.py
```

- add a while loop and rate in the node:

```python
#!/usr/bin/env python3.8

import rospy

if __name__ == '__main__':
    
    #creating a node with its name
    rospy.init_node('publisher_node') 
    
    # equal to print('Hello world)
    rospy.loginfo('Hello from publisher world')
    
    #instead of loginfo for warning
    rospy.logwarn('This is a warning!!!')
    
    #instead of loginfo for error
    rospy.logerr('This is an error!!!')
    
    #sleep for 1 sec
    rospy.sleep(1.0)
    
    #define a rate with rospy (10Hz) 
    rate = rospy.Rate(10)
    
    while not rospy.is_shutdown():
        
        rospy.loginfo("In the loop")
        
        #will use the rate we have defined to sleep
        rate.sleep()
```


> [!CAUTION]
> while working on python, upon saving the code. we can use `rosrun` or `python` to run the code
> but for c++ we have to use `catkin_make` every time.

- making a publisher node
> [!NOTE]
> `queue_size` is the size which store history if it is 10, that means after storing 10 message the 11th will be saved and the first one will be deleted. this determines how much RAM is used.

```python
#!/usr/bin/env python3.8

import rospy
from std_msgs.msg import String #import String from std_msgs.msg library

#create a topic 
test_pub = rospy.Publisher("/data", String, queue_size=10)

if __name__ == '__main__':
    
    #creating a node with its name
    rospy.init_node('publisher_node') 
    
    # equal to print('Hello world)
    rospy.loginfo('Hello from publisher world')
    
    #instead of loginfo for warning
    rospy.logwarn('This is a warning!!!')
    
    #instead of loginfo for error
    rospy.logerr('This is an error!!!')
    
    ##sleep for 1 sec
    #rospy.sleep(1.0)
    
    #define a rate with rospy (10Hz) 
    rate = rospy.Rate(10)
    
    while not rospy.is_shutdown():
        
        
        #rospy.loginfo("In the loop")
        
        test_pub.publish("Hello ROS")
        
        #will use the rate we have defined to sleep
        rate.sleep()
        
    else:
        rospy.loginfo("Node shutdown")
```

run the node again:

```
rosrun test_sub_pub pub_python.py
```

- after running the code open another terminal window and check `rostopic list`
  there should be `/data` topic becouse our node is activated

- run `echo` to publish from the topic:

```
rostopic echo /data
```

> [!CAUTION]
> We can't have two nodes with the same name to run.

> [!NOTE]
> use `rosnode list` to check active nodes.

> [!NOTE]
> use `rosnode info /publisher_node` to check the information of the node.









