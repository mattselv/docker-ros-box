# docker-ros-box

Dockerized [ROS](http://www.ros.org/) environment with X11 support based on [ros-lunar-desktop-full](https://hub.docker.com/r/osrf/ros/).

Using this project you will be able to run a complete ROS environment inside a Docker container.

This is very handful for example if your host operating system is *not* debian based.


# Credits

This project is highly inspired by [docker-browser-ros](https://github.com/sameersbn/docker-browser-box) and [this blog post from Fabio Rehm](http://fabiorehm.com/blog/2014/09/11/running-gui-apps-with-docker/) as well as [docker-opengl-mesa](https://github.com/thewtex/docker-opengl-mesa) for the hardware acceleration support.


# Usage

1. Clone the repository:

2. Initialize your ROS box:
```
./docker-ros-box/init-ros-box.sh [ros_distro] [target]
    ros_distro        The ROS distribution to work with (lunar, kinetic, etc.)
    target            The target directory to deploy the basic setup
```
Building the docker container image can take some time depending on your internet connexion. Please be patient.

Once the initialization is done, your dockerized ROS box is ready.

In the `target` directory you will find 4 files:

- `ros_distro`: This file contains the ROS distribution used in your project. Do not touch this file.
- `src`: Put your ROS project sources in this directory. It is automatically mounted in ~/catkin_ws/src inside the ROS box so you can work there from your host system.
- `utils.include.sh`: A shell script to be included by the scripts below.
- `start.sh`: Run this script to start the container and open a shell in it. You cannot run the same container several times.
- `join.sh`: Run this script to open an additional shell in a running ROS box. You can run this script several times to open several shellson the same ROS box.

3. Start you ROS box
```
cd [target]
./start.sh
```

4. Open additional shells to the same ROS box
```
cd [target]
./join.sh
```


# Additional notes

- The scripts assume you run docker as root using `sudo`.


# Contribute

Feel free to use this project and improve it.

If you would like to contribute, clone the repository, commit your modifications and open a PR


# Author

[Pierre Killy](https://www.linkedin.com/in/pierrekilly/)


# License

MIT


