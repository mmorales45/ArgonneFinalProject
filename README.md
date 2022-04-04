# Argonne Dual Arm mobile base
By Marco Morales

<!-- ![Robot_first](pictures/ArgonnePic1.png)

![Robot_second](pictures/ArgonnePic2.png) -->



Instructions for the Mobile Base to Move

1. Turn on the robot and ensure the knob position is set to Automatic, manual should be used for pushing the robot to a desired position.

2. Connect to the MiR website.
    - For Marco, the username is `Marco` and the password is `test`.
    - If you plan on being a long term user, create a new user account through an existing account.

3. The following substeps are useful for preventing errors and headaches down the road.
    - Ensure the robot's time and the computers times are in sync. This can be done by going into System > Settings > Data & Time and then clicking on laod from device followed by `Save Changes`. Wait for the system to sync up. 

4. On you computer, load the following launchfile.
    ```
    roslaunch mir_driver mir.launch
    ``` 
    - This will establish a connect between the MiR's and your computer. This may take a few seconds so please be patient. 

5. Now run the hector mapping launchfile to map the area around the robot.
    ```
    roslaunch mir_navigation hector_mapping.launch
    ```

6. Now run the move_base launchfile which will enable the mobile base to be controlled thourgh move base goals.
    ```
    roslaunch mir_navigation move_base.xml with_virtual_walls:=false
    ```
7. Finally, run the RVIZ file to see visual representaion of the operations.
    ```
    rviz -d $(rospack find mir_navigation)/rviz/navigation.rviz
    ```
8. Now the map should be visible to you, if not try zooming out to see if the robot and map were offset and then move the camera to that position. 
    - You can set waypoints/goals by clicking on `Set 2D nav goal` and then clicking on a location and the  releasing at the disired orientation. 

Accessing cameras of MiR base

1. export ROS_MASTER_URI=http://192.168.12.20:11311

2. rqt_image_view