# The information repository of "Learning ROS Robot Programming with Raspberry Pi"

* For people who are lazy of installing the OS image: https://b.ueda.tech/?post=20180617_raspi_ubuntu
* For people who would like to use Raspberry Pi 3 B+: https://b.ueda.tech/?post=20180827_raspimouse

## Important Information 

### 2018/11/20

There is one unconfirmed supplement about the test. It is usually fine but unless you immediately execute `f. flush()` when writting a word into the dummy device with the test code, there will be delays in file inputs, which leads to the tests being mocky.

### 2018/6/15

By following the procedures listed here https://wiki.ubuntu.com/ARM/RaspberryPi#Wifi we have confirmed that one can install a firmware where the WiFi is enabled. -> [wifiproblem.md](https://github.com/ryuichiueda/raspimouse_book_info/blob/master/trouble_reports/wifiproblem.md)


### 2018/6/11

When installing the newest ROS and executing `catkin_create_pkg`, the format of `package.xml` is generated as version 2. Since in this version `run_depend` is replaced by `exec_depend`, you will need to replace the `run_depend` to `exec_depend` written in the text. If you would like to use the old version, delete the line `format="2"` written in the top of the XML. Although, it will be better to learn the new version. 


### 2018/5/26

We have just noticed this but the WiFi does not work with the method shown in 2017/05/06. It is under investigation and in the mean time please do as follows.

* If you have already installed it and the WiFi works, do NOT `apt upgrade`.
* If you are about to install, use the image [here](https://b.ueda.tech/?post=20171223_raspi_ubuntu_image).

### 2018/4/22

There wasn't a log of the simulator (Chapter E) at the time of writing, so we have made a branch of it.

* Simulator: https://github.com/rt-net/raspimouse_sim/tree/rpim_book_version
* Installer: https://github.com/ryuichiueda/raspimouse_sim_installer/tree/rpim_book_version

### 2017/12/18

In chapter 10, because there was no xml file in the specified path, an error will occur in OpenCV.

* How to handle

Execute the following commands.
```
$ sudo apt install opencv-data
```

### 2017/12/8

The link is broken for the JavaScript codes used in chapter 12.

* Details: https://github.com/ryuichiueda/raspimouse_book_info/issues/11

We modified the bug in the device driver. (2017/07/07)

* [The newest branch](https://github.com/rt-net/RaspberryPiMouse)

### 2017/5/6

We have confirmed a defect where you can't use the WiFi after updating the kernel.

* [Troubleshooting](./trouble_reports/wifiproblem.md)
* [Issue](https://github.com/ryuichiueda/raspimouse_book_info/issues/1)

## Other information

* A collection of shell scripts for setting the system: [ryuichiueda/raspimouse_book_ubuntu_init](https://github.com/ryuichiueda/raspimouse_book_ubuntu_init)
* Information about the OS image used in the text: [os_images.md](./os_images.md)
* A list of errata: [errata.md](./errata.md)
* FAQ: [faq.md](./faq.md)
* Facebook Group: https://www.facebook.com/RaspberryPiMouse

## Repository of each chapters
* Ch. 2: Script for setting up ROS
    * https://github.com/ryuichiueda/ros_setup_scripts_Ubuntu16.04_server
* Ch. 3: Device Driver
    * https://github.com/rt-net/RaspberryPiMouse
* Ch. 4:
    * [Using cron](https://github.com/ryuichiueda/pimouse_setup/tree/cad60aa542ac45c4e685dc81804a9f2aa90b897d)
    * [Using make](https://github.com/ryuichiueda/pimouse_setup)

* Ch. 5: Basic control package for Raspberry Pi Mouse (Commercial item)
    * https://github.com/ryuichiueda/raspimouse_ros/
* Ch. 6 to 8: The basic control package for Raspberry Pi Mouse used in the text.
    * https://github.com/ryuichiueda/pimouse_ros/
    
* Ch. 9: The code for running the Raspberry Pi Mouse in the hallway.
   * https://github.com/ryuichiueda/pimouse_run_corridor

* Ch. 10: Recognizing the face via camera and following it.
    * https://github.com/ryuichiueda/pimouse_vision_control
* Ch. 11: Controlling the robot by voice.
    * https://github.com/ryuichiueda/pimouse_voice_control
* Ch. 12: Controlling the robot through a web browser.
    * https://github.com/ryuichiueda/pimouse_monitor
* Ch. 13: SLAM
    * https://github.com/ryuichiueda/pimouse_slam
    
    
## Convenient Tools

* A package for controlling the robot with a game controller.
    * https://github.com/zaki0929/raspimouse_game_controller
