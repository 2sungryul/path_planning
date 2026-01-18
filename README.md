# path_planning

# how to run map server

$ ros2 run nav2_map_server map_server --ros-args -p yaml_filename:=map.yaml

$ ros2 lifecycle set /map_server configure
$ ros2 lifecycle set /map_server activate

or 

$ ros2 run nav2_lifecycle_manager lifecycle_manager --ros-args -p node_names:=['map_server'] -p autostart:=true

# how to run planner server

> $ ros2 run tf2_ros static_transform_publisher 0 0 0 0 0 0 map base_link
> $ ros2 run nav2_planner planner_server --ros-args --params-file myplanner.yaml
> $ ros2 lifecycle set /planner_server configure
> $ ros2 lifecycle set /planner_server activate
> or
> $ ros2 run nav2_lifecycle_manager lifecycle_manager --ros-args -p node_names:=['planner_server'] -p autostart:=true

# how to run action client

$ ros2 action send_goal /compute_path_to_pose nav2_msgs/action/ComputePathToPose "{
  use_start: true,
  start: {header: {frame_id: 'map'}, pose: {position: {x: 0.0, y: 0.0, z: 0.0}}},
  goal: {header: {frame_id: 'map'}, pose: {position: {x: 4.0, y: 1.0, z: 0.0}}},
  planner_id: 'GridBased'
}"











