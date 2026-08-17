# rosbag-convertion


ros1 rosbag to ros2 bag mcap format


    python3 -m rosbags.convert \ --src ~/Downloads/2026-07-20-13-57-07.bag \ --dst ~/Downloads/my_mcap_bag \ --dst-storage mcap


ros1 rosbag to ros2 bag db3 format

    python3 -m rosbags.convert \ --src ~/Downloads/2026-07-20-13-57-07.bag \ --dst ~/Downloads/converted_bag \ --src-typestore ros1_noetic \ --dst-typestore ros2_humble




 
  # 2. Save with default path (will save to funny_lidar_slam/data/map.pcd)
 after running funny_lidar_slam and mapping, we can save map in pcd format

 unitree@lb22:~$ 
 
     ros2 service call /save_map funny_lidar_slam/srv/SaveMap "{map_path: '', split_map: false}"



# 3. Visualize the Map in RViz 

Option A:  Publish the map as a ROS topic


 unitree@lb22:~$ 

    ros2 run pcl_ros pcd_to_pointcloud   --ros-args -p file_name:=/home/unitree/funny_lidar_slam_ws/src/funny_lidar_slam/data/map.pcd   -r /cloud_pcd:=/saved_map



Option B: With static transform (if frame mismatch)

# Terminal 1: Publish the map
    ros2 run pcl_ros pcd_to_pointcloud \
      --ros-args -p file_name:=~/funny_lidar_slam_ws/src/funny_lidar_slam/data/map.pcd \
      -r /cloud_pcd:=/saved_map

# Terminal 2: Publish static transform
    ros2 run tf2_ros static_transform_publisher 0 0 0 0 0 0 map base_link
