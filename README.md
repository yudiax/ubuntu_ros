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

roslaunch urdf02_gazebo demo03_env.launch gezol
roslaunch urdf02_gazebo demo04_sensor.launch rviz

sudo apt-get 安装 ros-noetic-rviz

sudo apt-get 删除 ros-neotic-* sudo apt-get 删除 python-rosdep python-rosinstall python-rosinstall-plugins ros-noetic-ros* sudo apt-get autoremove

rostopic pub -r 10 /cmd_vel geometry_msgs/Twist "linear:,
angle  z改0.5

