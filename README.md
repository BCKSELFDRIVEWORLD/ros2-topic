# ros2-topic

   ros2 topic info <topic_name>

    
![cmd_vel_info](https://github.com/BCKSELFDRIVEWORLD/ros2-topic/assets/146545020/d21836eb-b2f5-4ed2-86c7-8475a76b78b4)

Type: Refers to the ROS2 interface associated with the Topic with which you need to work with this Topic.

Publisher count: Refers to the number of active Publishers connected to the Topic.

Subscription count: Refers to the number of active Subscribers connected to the Topic

Look at how you can check the current data for a specific Topic. To do this, run the following command in the same shell:

      ros2 topic echo <topic_name>
      
The ros2 topic echo command is used to read (subscribe to) the published Topic

Check what type of interface the Topic uses. Then, try a new command named interface. As you did before, start by listing the available interfaces

      ros2 interface list

The ros2 interface list command prints a list of all the available interfaces.


Messages: Can be found as .msg files. They are simple text files that describe the fields of a ROS message. You can use them to generate source code for messages.

Services: Can be found as .srv files. They are composed of two parts: a request and a response. Both are message declarations.

Actions: Can be found as .action files. They are composed of three parts: a goal, a result, and feedback. Each part contains a message declaration.

The .msg files are composed of two parts: fields and constants.

      ros2 topic pub <topic_name> <interface_name> <message>
      ros2 topic pub --once /cmd_vel geometry_msgs/msg/Twist "{linear: {x: 0.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 0.0}}"
# Topic Publisher

Initiate a node named simple_publisher:

      super().__init__('simple_publisher')
Create a Publisher for the /cmd_vel Topic that uses Twist messages:

      self.publisher_ = self.create_publisher(Twist, 'cmd_vel', 10)
Create a timer object that will trigger the timer_callback method each 0.5 (timer_period) seconds:

      self.timer = self.create_timer(timer_period, self.timer_callback)
Publish the contents of msg into the /cmd_vel Topic.

        self.publisher_.publish(msg)

# Topic Subscriber

Create a Subscriber for the /scan topic that uses LaserScan messages:


         self.subscriber= self.create_subscription(
                     LaserScan,
                     '/scan',
                     self.listener_callback,
                     QoSProfile(depth=10, reliability=ReliabilityPolicy.RELIABLE))
Notice that you are doing two interesting things here:

First, you define a callback method named listener_callback for the subscriber. This means that every time a message is published to the /scan topic, this method will be triggered.
Second, you define a QoSProfile. This refers to the Quality of Service of the topic.

# TASK

Write a Publisher and Subscriber node:

Create a new package and call it exercise31_pkg with rclpy, std_msgs, sensor_msgs, and geometry_msgs as dependencies.

Use the previous publisher code as a template to create a new program that makes the robot turn left using Twist messages.

Get information from the laser and use the LaserScan messages to decide how to move.

Turn left until you get a value lower than 5m (from the laser direction in front of the robot). Then, move straight.

If the distance received is greater than 50cm, move in a straight line towards the wall (do not go too fast!).

If the distance received is less than 50cm, the robot stops.

The resulting motion should be something similar to this:

   
