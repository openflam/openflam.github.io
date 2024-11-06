---
layout: default
parent: Tools
title: Waypoint Tagger
nav_order: 3
---

# Waypoint Tagger

<a href="https://anon-vps.github.io/waypoint-tagger/" target="_blank">Waypoint Tagger tool</a> helps map creators visualize their map in 3D and tag waypoints. The tool requires no installation and is entirely web-based.

### Load map

The tool takes in the map as a `pcd` file. Our implementation of the image-based map server (which will be open-sourced after publication) automatically generates the pcd file from 3D scans. For now, we provide an example map that can be visualized. Download <a href="https://figshare.com/s/d8ac40e112587e2ea957" target="_blank">points.pcd</a> from figshare (If you are logged in to your figshare account, please log out. Otherwise you might see "Insufficient Permission" error). 

Click on the green "Load Map" button on the left and select the pcd file. The point cloud of the map shoud load into the tool.

{: .highlight}
Use Left mouse button to rotate. Right mouse button to pan. Scroll to zoom.

![Load_Map Demo](/assets/gifs/waypoint-tagger/load-map.gif){: width="500" }

### Add Waypoint

Click on the red "Add Waypoint" button on the left. In the panel on the right, enter the "ID" of the waypoint (eg. "door5"). Add as many waypoints as necessary. We recommend that waypoints correspond to fixed locations in the real-world such as doors, elevators and stairs.

{: .highlight}
When a waypoint is selected, you can use the axis handles to move it along an axis and the plane handles to move it along a plane. You generally want to move it along the x-z plane.

![Second Tool Configure Demo](/assets/gifs/waypoint-tagger/add-waypoint.gif){: width="500" }

### Connect neighbors

Select a waypoint to update its neighbors. In the "neighbors" field, enter the IDs of the neighboring waypoints, separated by a comma. Two waypoints are neighbors if there is a direct path between them in the real-world without turns and obstacles. A white line should connect the neighbors.

![Second Tool Configure Demo](/assets/gifs/waypoint-tagger/add-waypoint-neighbors.gif){: width="500" }

### Download waypoints

Once the waypoints are created and neighbors connected, the resulting graph can be exported as a CSV file. Click on the red "Download Waypoints" button. The exported CSV file can be uploaded to the map server, which will expose it to the OpenFLAME client on query.

The green "Load Waypoints" button can be used to import a waypoints CSV.

![Second Tool Configure Demo](/assets/gifs/waypoint-tagger/under-over.gif){: width="500" }
