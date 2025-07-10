---
layout: default
parent: Tools
title: Waypoint Tagger
nav_order: 3
---

# Waypoint Tagger

<a href="https://openflam.github.io/waypoint-tagger/" target="_blank">Waypoint Tagger tool</a> helps map creators visualize their scan in 3D and tag waypoints. The tool requires no installation and is entirely web-based.

### Load 3D Scan

The tool takes in the 3D scan as a `glb` file. A GLB file can be exported from any 3D scanning application (e.g., [Polycam](https://learn.poly.cam/hc/en-us/articles/29647691255316-How-to-Export-Polycam-Captures)). We provide an example scan that can be visualized. Download <a href="https://figshare.com/s/eeec9fe3877bd35a1b2e" target="_blank">map.glb</a> from figshare (If you are logged in to your figshare account, please log out. Otherwise you might see "Insufficient Permission" error). 

Click on the green "Load GLB" button on the left and select the glb file. The 3D scan of the map shoud load into the tool.

{: .highlight}
Use Left mouse button to rotate. Right mouse button to pan. Scroll to zoom.

![Load_Map Demo](/assets/gifs/waypoint-tagger/load-map.gif){: width="500" }

### Load Waypoints

A _Waypoints Graph_ contains the map data corresponding to the scan. Waypoints Graph is stored as a CSV file. To import an existing waypoints graph click on the green "Load Waypoints" button and choose the CSV file. We provide an example waypoints graph that can be used. Download <a href="https://figshare.com/s/eeec9fe3877bd35a1b2e" target="_blank">waypoints_graph.csv</a> from figshare

![Load_Map Demo](/assets/gifs/waypoint-tagger/load-waypoints.gif){: width="500" }

### Add Waypoint

Click on the red "Add Waypoint" button on the left. In the panel on the right, enter the "ID" of the waypoint (eg. "door5"). Add as many waypoints as necessary. We recommend that waypoints correspond to fixed locations in the real-world such as doors, elevators and stairs.

{: .highlight}
When a waypoint is selected, you can use the axis handles to move it along an axis and the plane handles to move it along a plane. You generally want to move it along the x-z plane.

![Add Waypoint Demo](/assets/gifs/waypoint-tagger/add-waypoint.gif){: width="500" }

### Connect Neighbors

Select a waypoint to update its neighbors. In the "neighbors" field, enter the IDs of the neighboring waypoints, separated by a comma. Two waypoints are neighbors if there is a direct path between them in the real-world without turns and obstacles. A white line should connect the neighbors.

![Connect Neighbors Demo](/assets/gifs/waypoint-tagger/add-neighbors.gif){: width="500" }

### Download Waypoints

Once the waypoints are created and neighbors connected, the resulting graph can be exported as a CSV file. Click on the red "Download Waypoints" button. The exported CSV file can be uploaded to the map server, which will expose it to the OpenFLAME client on query.
