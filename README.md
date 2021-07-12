This package logs the poses of antennas fitted to a robot as the robot moves in space through time. This calculation assumes that the pose of the robot and the relative placement of the antennas relative to the robot's `base_footprint` are known. The pose of the robot is provided by a pose-tracking algorithm to a topic (e.g. `amcl` to `/amcl_pose`). The pose of the robot may be provided by an additional source, such as by the output of an algorithm that improves the output pose of `amcl`. The configuration of relative placements of antennas resides in `.yaml` files in directory `config`.

Input params:
- `robot_type`: `rb1` or `turtlebot`
- `config_file`: the `.yaml` file where the placements of antennas is stored
- `pose_robot_filename`: the absolute path of the directory under which the robot's poses are to be logged
- `pose_pipeline_robot_filename`: the absolute path of the directory under which the "improved" robot's poses are to be logged
- `pose_filename`: the absolute path of the directory under which the antennas' poses are to be logged + "/" + a prefix
- `pose_pipeline_filename`: the absolute path of the directory under which the "improved" antennas' poses are to be logged + "/" + a prefix
- `velocity_filename`: the absolute path of the file in which the velocity of the robot is to be logged into
- `antennas_polarities_filaname`: the absolute path of the file in which the polarities of the antennas are written. The polarity of an antenna expresses its heading with respect to the robot's frame of reference (positive for antennas having the same direction as the y-axis)
- under directory `config`:
  - `reader_X`: where X > 0 and incremental
  - `sn`: The reader's MAC address in condensed form (without colons)
  - `active`: Whether the poses of the antennas connected to this reader are
  to be logged
  - `antenna_Y`: where Y > 0 and incremental is the configuration per antenna;
  - `active`: if the pose of antenna Y is to be logged
  - `x`, `y`, `z`: the pose of antenna Y with respect to the robot's `base_footprint`


Subscribed topics:
- `pose_topic` the robot's pose (AMCL in particular)
- `pose_pipeline_topic` the robot's pose that has been improved via matching the robot's range scan to the virtual scan which is computed via ray-casting the map from the robot's pose estimate (i.e. AMCL's pose estimate)
- `velocity_topic` the robot's velocity

Published topics: none
