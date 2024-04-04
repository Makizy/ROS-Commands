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
-  
