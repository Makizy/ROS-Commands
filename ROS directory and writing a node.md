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
> when we want to write a code we go to `src`.

```
cd src
```

It is preferable to use VScode to code.

use `code` cmd to open vscode in terminal:

```
code
```

- we have to define what vesion of python we are using in the begining of the code:

```python
#!/usr/bin/env python3.8
```

>[!NOTE]
> For noetic use puthon 3 and for melodic use python2


