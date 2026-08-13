# rosbag-convertion


ros1 rosbag to ros2 bag mcap format


    python3 -m rosbags.convert \ --src ~/Downloads/2026-07-20-13-57-07.bag \ --dst ~/Downloads/my_mcap_bag \ --dst-storage mcap


ros1 rosbag to ros2 bag db3 format

    python3 -m rosbags.convert \ --src ~/Downloads/2026-07-20-13-57-07.bag \ --dst ~/Downloads/converted_bag \ --src-typestore ros1_noetic \ --dst-typestore ros2_humble
