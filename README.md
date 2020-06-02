# ros-example-kinesisvideo
ROS example for usb-cam and aws-kinesisvideo

# Environment Setting
* Install ROS [http://wiki.ros.org/ROS/Installation](http://wiki.ros.org/ROS/Installation)  

* git clone this repository  
```git clone https://github.com/yesseecity/ros-example-kinesisvideo.git```

* init git submodule and update  
```git submodule init```  
```git submodule update```  

* Install dependency  
```sh 
sudo apt-get update
sudo apt-get install -y ros-$ROS_DISTRO-h264-video-encoder  ros-$ROS_DISTRO-image-view ros-$ROS_DISTRO-kinesis-video-streamer
```

* ROS catkin make
```catkin_make```

* Source setup  
If you used bash.  
```source $(pwd)/devel/setup.bash && echo source $(pwd)/devel/setup.bash > ~/.bashrc```  
If you used zsh.  
```source $(pwd)/devel/setup.zsh && echo source $(pwd)/devel/setup.zsh > ~/.zshrc```


# Config

### Change usb camera path
Show your camera  
```ls /dev/video*```  
![show camera](/images/show_camera.png)  

Change your camera setting in [/src/aws_stream/launch/aws_camera.launch](/src/aws_stream/launch/aws_camera.launch)  
![change camera](/images/change_camera.png)  

### Change AWS region
[/src/aws_stream/launch/kinesisvideo/node_config.yaml](/src/aws_stream/launch/kinesisvideo/node_config.yaml)
![change aws region](/images/change_aws_region.png)

### Add user on AWS IAM 
[https://console.aws.amazon.com/iam/home#/users](https://console.aws.amazon.com/iam/home#/users)  
Add user
![AWS Add user](/images/iam_add_user_1.png)  

### Select policy **AmazonKinesisVideoStreamsFullAccess**
![AWS Add user](/images/iam_add_user_2.png)

### Take down **Access key ID** and **Secret access key**  
![AWS Add user](/images/iam_add_user_3.png)  

### Back user list and click user stream_video_user  
![AWS Add user](/images/iam_add_user_4.png)  

### Take down **User ARN**  
![AWS Add user](/images/iam_add_user_5.png)  

### Add user access info to your ```~/.bashrc``` or ```~/.zshrc```  
![AWS Add user](/images/iam_add_user_6.png)  

### Resource your  ```~/.bashrc``` or ```~/.zshrc```  
```source ~/.bashrc```  
or  
```source ~/.zshrc```  

# Launch
* ROS launch
```roslaunch aws_stream aws_camera.launch```  
