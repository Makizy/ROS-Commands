##

### make launch file 

- create a new folder in the test_sub_pub

- after opening the empty launch file, click right to choose open in terminal.

```
gedit nodes.launch

```

> `.launch` is the format

> we can make it in vscode too like anyother file.

- xml is a file format.

- we open a tag like `<launch>` which is the parent and we put come child in it like '<node>'

  > `<launch>` is the start. `</launch>` is the finish tag.

- `name`   :where we have used initial node `rospy.init_node('publisher_node')` here `publisher_node` is the name of the node.

- `pkg`    :is the name of the package we are running in our case it is `test_sub_pub`
  
- `type`   :is the python file which our node wants to run.
 
- `output` :is where we define if we want to see the node or we want it hidden. for showing it we use `screen`

> [!CAUTION]
> the name of the node should be in the same type you are adressing otherwise there will be an error.

- now the .launch file should look like this:

```
<launch>

	<!-- launch launch node 1 -->
	<node name="publisher_node" pkg="test_sub_pub" type="publisher_test" output="screen" />

	<!-- launch launch node 2 -->

	<node name="subscriber" pkg="test_sub_pub" type="subscriber_test" output="screen" />

</launch>
```

- publisher node code:

```
#!/usr/bin/env python3.8

import rospy
from std_msgs.msg import String


test_pub = rospy.Publisher("/data",String, queue_size = 10)

if __name__ == '__main__':
    rospy.init_node('publisher_node')
    rospy.loginfo('Hello from publisher')

    #rospy.sleep(1.0)
    rate = rospy.Rate(1) # 1 Hz

    while not rospy.is_shutdown():
        #rospy.loginfo('In the loop')
        test_pub.publish("dataaaaaaa")
        rate.sleep()

```

- subscriber node code :

```
#!/usr/bin/env python3.8

import rospy
from std_msgs.msg import String #import String from std_msgs.msg library


def handle(data):
    print( "test            ", data)

if __name__ == '__main__':
    
    #creating a node with its name
    rospy.init_node('subscriber') 

    #define a rate with rospy (10Hz) 
    #rate = rospy.Rate(10)
    
    #subscribe to a topic /data here and then do the function 'handle' that was defined
    rospy.Subscriber("/data", String, handle)
    
    while not rospy.is_shutdown():
        pass

    else:
        
        rospy.loginfo("Node shutdown")
        
    
    rospy.spin()
```

- the format which we will run the cmd in `/catkin_ws` is `roslaunch <pkg_name> <launch_file_name>`

```
roslaunch test_sub_pub nodes.launch
```

this is how the `rqt_graph` will look like :

![image](https://github.com/Makizy/ROS-Commands/assets/53753128/c7470e38-a05d-40ec-8166-713adde845c3)


## Gazebo simulation and ROS cheat sheet

The cheat sheet is available [here](https://github.com/nooshin-kohli/simulation)

## URDF

urdf is used in many simulations and its not only limited to ROS. a simple urdf contains come box,...).If we want to visualize it urdf yse meches and mesh formats can be ftl,object,dae,....

> `xacro` is the same as `urdf`. in `xacro` for example it help you calculate repeated parameters. like inertia.
> in otherwords `xacro` is usded to simplify `urdf`

### suggestion for the first projects

- arm        : ur5 or ur10
- navigation : turtlebot3 - turtlebot
- control    : 4 wheeled robot 

> install a plugin for solidwork or blender.
> it is not recommended to get urdf staight from soldwork or blender becouse it has too many errors. Its better to get the mesh from there and use it in te urdf.

- in the test_sub_pub create a new folder named `urdf`.

- create new file `gedit arm.urdf`

- parent <robot name=2link_robot>

- child ` material`

```
<material name=black>
  <color rgba="0 0 0 0.7"/>
</material>
```
> `rgba` : red green blue transparency. it can be find with a simple search.

- we now want to only show in rviz becouse only visual matters

```
	<link name="arm1">
		<visual>
			<geometry>
				<box size="1 .05 .05"/>
			</geometry>
			<origin rpy="0 0 0" xyz="0.5 0 0"/>
			<material name="black"/>
		</visual>
	</link>

```
- `<box size` is in SI and meter.
- `origin` how much distance from `rpy` = roll pitch yaw, or from `xyz`.
- 
