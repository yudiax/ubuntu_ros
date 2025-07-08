# ubuntu_ros
安装virtualbox为7.1.10，及其拓展包，并在阿里云安装ubuntu20.04.6，但命名错误为22

显示22.04.5可以更新，但我自己忽略该版本

键盘无法输入，无法安装增强功能，没有反应 终端打不开， 教程 https://blog.csdn.net/muxuen/article/details/145412992?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522089fb6b92b8ffe2e4fc92c62cbdebc52%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=089fb6b92b8ffe 2e4fc92c62cbdebc52&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-145412992-null-null.142^v102^pc_search_result_base6&utm_term=virtualbox%E5%AE%89%E8%A3%85ubuntu22.04&spm=1018.2226.3001.4187 然后同意锁指针，就可以看见添加成功

后来，发现不能粘贴，利用 https://blog.csdn.net/subtitle_/article/details/132032433?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522f1490e8c8 4ef977c8d18006f1c3d42a8%2522%252C%2522scm%2522%253A%25222014071 3.130102334..%2522%257D&request_id=f1490e8c84ef977c8d18006f1c3d 42a8&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-132032433-null-null.142^v102^pc_search_result_base6&utm_term=%E6%97%A0%E6%B3%95%E5%AE%89%E8%A3%85%E5%A2%9E%E5%BC%BA%E5%8A%9F%E8%83%BD&spm=1018.2226.3001.4187 后来发现不是 ctrl 加 v，要右键

增强包直接运行，它会自动添加。

usb添加设备后，锁指针不能动一点，就不添加了

打开虚拟机的设置，在存储勾选控制器:STATA->使用主机输入输出(I/O)缓存和***.(虚拟机的名字)vdl->固态驱动器；在常规选择共享粘贴板和拖放双向。参考virtualBox 设置增强功能粘贴和拖放

安装 ros https://blog.csdn.net/qq_44339029/article/details/120579608?ops_request_misc=%257B%2522request%255Fid%2522%253A%252216f3eb58f78d331a0f201ea93e27e2ac%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=16f3eb58f 78d331a0f201ea93e27e2ac&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-120579608-null-null.142^v102^pc_search_result_base6&utm_term=ubuntu20.04%E5%AE%89%E8%A3%85ros&spm=1018.2226.3001.4187

但是没有执行初始化rosdp

安装 English https://blog.csdn.net/Misakaya/article/details/146299957?ops_request_misc=%257B%2522request%255Fid%2522%253A%25228aba3ee03470fa31556cbf895f599e85%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=8aba3ee03470fa31556cbf895f599e85&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-146299957-null-null.142^v102^pc_search_result_base6&utm_term=ubuntu%E8%99%9A%E6%8B%9F%E6%9C%BA%E4%B8%AD%E6%96%87%E8%BE%93%E5%85%A5%E6%B3%95&spm=1018.2226.3001.4187

切换到 terminator exec x-terminal-emulator exec-arg -e

roslaunch urdf_tutorial display.launch 模型:=mybot1.urdf

sudo apt-get 安装 ros-noetic-arbotix

先启动 roscore,然后运行 rosrun

先进入工作区间 source ./devel/setup.bash

我在gezebo上导入，发先不显示，重新添加了质量就显示

分割线————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————
大概说一下怎么使用这些代码吧，
1.先安装虚拟机ubuntu系统20.04，并配置ros-noetic-full-desk，和vscode
2.下载完代码后，先终端运行   roscore
3.进入工作空间vscode终端运行source ./devel/setup.bash
4.然后运行launch文件就行，所有代码都可以运行

5.分为 urdf01_rviz 和 urdf02_gazebo 两个功能包,

urdf01_rviz
是6.3.4 urdf练习的四轮小车，运行指令roslaunch urdf01_rviz demo05_test.launch用urdf写的小车

6.4.4 用xacro写的四轮带摄像头和传感器的小车，car.launch，运行roslaunch urdf01_rviz car.launch

6.5.1让小车动起来并显示运动轨迹，
先运行control.launch，再在rviz显示odometry，topic改为odom，改fixed frame从base_footprint为odom，再开一个终端rostopic list,检查有没有cmd_vel
在终端发布消息rostopic pub -r 10 /cmd_vel geometry_msgs/Twist '{linear: {x: 0.2, y: 0, z: 0}, angular: {x: 0, y: 0, z: 0.5}}'
就可以动起来了并生成红色圈

6.6.3 URDF集成Gazebo实操————将之前的机器人模型(xacro版)显示在 gazebo 中
后面集成gezebo,launch urdf02_gazebo 功能包来运行就行
运行roslaunch urdf02_gazebo demo02_car.launch显示模型

6.6.4世界文件，后缀是world的那个

6.7.1
运行roslaunch urdf02_gazebo demo03_env.launch显示世界上的模型，再运行roslaunch urdf02_gazebo demo04_sensor.launch并显示运动轨迹
rostopic pub -r 10 /cmd_vel geometry_msgs/Twist '{linear: {x: 0.2, y: 0, z: 0}, angular: {x: 0, y: 0, z: 0.5}}'

6.7.2运行 demo04_sensor.launch

6.7.3运行  demo03_env.launch
然后终端运行rostopic pub -r 10 /cmd_vel geometry_msgs/Twist "linear:
设置angular中的z为0.5后回车执行，发现小车实时转动的的视角图片展现了出来：

6.7.4依旧运行  demo03_env.launch，按他说的配置，然后转动视角同上


