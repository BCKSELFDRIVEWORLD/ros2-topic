# ros2-topic

   ros2 topic info <topic_name>

    
![cmd_vel_info](https://github.com/BCKSELFDRIVEWORLD/ros2-topic/assets/146545020/d21836eb-b2f5-4ed2-86c7-8475a76b78b4)

Type: Refers to the ROS2 interface associated with the Topic with which you need to work with this Topic.

Publisher count: Refers to the number of active Publishers connected to the Topic.

Subscription count: Refers to the number of active Subscribers connected to the Topic

Look at how you can check the current data for a specific Topic. To do this, run the following command in the same shell:

    ros2 topic echo /cmd_vel

The ros2 topic echo command is used to read (subscribe to) the published Topic
