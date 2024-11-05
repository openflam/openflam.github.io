---
layout: default
parent: Tools
title: Map Server
nav_order: 1
---

# Map server
{: .no_toc }

The [map server](https://github.com/openvps/spatial-server) or the spatial server is a reference implementation for a map server that works within the OpenVPS framework. We use [hloc](https://github.com/cvg/Hierarchical-Localization) (which in turn uses [SuperPoint](https://arxiv.org/abs/1712.07629) and [SuperGlue](https://arxiv.org/abs/1911.11763)) for map creation and localization. The map server provides the following functionalites:

- Map creation and storage along with tools required to transform maps.
- Localization against stored maps.
- Tagging maps with *waypoints* and exploring tagged points in augmented reality.

<video src="/assets/videos/spatial_server.mp4" autoplay loop muted width="500"></video>

1. TOC
{:toc}

## Setting up the map server

Follow instructions on the [Github repository](https://github.com/openvps/spatial-server) to set up the map server. Once the map server is set up, the landing page at <https://localhost:8001/> (replace `localhost` with your IP address if you have set it up on a remote server) should look like this:

![Map server landing page](/assets/images/map-server/landing-page.png){: width="500" }

## Map creation

Maps can be created using the Polycam application (on iPhones/iPads with a LiDAR (2020+)), or using a 2-D video on android phones.

{: .hint}
Polycam is the easiest way to create maps on OpenVPS. Creating a map using a video requires an extra step of estimating real-world scale. Map creation using a video may also fail sometimes because of insuficient overlap between video frames.

### Polycam

#### Scanning

1. We use the same workflow for Polyam as is used in [dataset creation in NeRF Studio](https://docs.nerf.studio/quickstart/custom_dataset.html#polycam). Download the application from the [app store](https://apps.apple.com/us/app/polycam-3d-scanner-lidar-360/id1532482376). Go to the settings and enable developer mode. 
   
   ![Polycam Settings](/assets/images/map-server/polycam-settings.png){: width="200"}

2. Capture data in LiDAR or Room mode.
3. Tap Process to process the data in the Polycam app.
4. Navigate to the export app pane.
5. Select raw data to export a .zip file.

#### Create Map

1. Go to the server landing page and select the "Create Map" option.
2. In the "Map data type" dropdown, select "Polycam".
3. Enter any Name of your choice.
4. Upload the zip created by the Polycam application in the previous step.
5. Click on "Submit" button. The map creation process will start in the background.

#### Map creation logs

To check the progress of the map creation process, click on the "View Logs" button in the landing page. Select the map name whose creation process was started in the previous step. The map creation logs are displayed live. At the end of the map creation process, the log "Map creation completed" is printed.

{: .highlight}
Map creation using Polycam generally takes around 2-3 minutes based on the specific GPU used.

### Video

#### Capture the video

Capture a video of the space. Move the camera slowly so that there is sufficient overlap between consecutive video frames. We recommend locking the camera exposure and focus so it is the same across all video frames.

{: .highlight}
We find that a resolution of 1920 X 1080 and a frame rate of 30 FPS is suffucient to get good scans. 

#### Create a map

1. Go to the server landing page and select the "Create Map" option.
2. In the "Map data type" dropdown, select "Video".
3. Enter any Name of your choice.
4. Upload the captured video.
5. Mention the percentage of frames to extract from the video for map creation. The default of 25% works well for most videos.
6. Click on "Submit" button. The map creation process will start in the background.

You can view the live logs of the map creation process by going to the "View Logs" page from the landing page.

#### Scale the map

A map created from a video capture does not have real-world scale. To scale the world to real-world metrics, we provide an AR application to capture images and their corresponding pose. 

{: .important}
Currently, the pose and image collection application only works on Android mobile devices such as phones and tablets with a camera.

1. From the landing page, select the "Save Image Pose" option under "Map Transforms" section. 
2. Select the name of the map that was created in the previous step and click on "Collect Data".
3. Once the a-frame application loads, click on the "AR" option at the bottom right of the screen.
4. Walk to different parts of your space and click on the capture button at the bottom right of the screen. The application sends the AR pose and the captured image to the server. You can see the data collected in the `data/map_data/your_map_name/images_with_pose` directory.
5. Go back to the server landing page and select the "Scale Map" option under "Map Transforms". The server uses the collected images and pose to automatically scale the map.

## Waypoints

### Upload waypoints
Download the map using the "Download Map" button on the landing page. A zip file containing the map point cloud is downloaded. Extract the zip file. Upload the point cloud to the [Waypoint Tagger tool]({% link pages/tools/waypoint-tagger.md %}). This helps you visualize the generated point cloud. Tag waypoints using [instructions from the tool page]({% link pages/tools/waypoint-tagger.md %}). The tagged waypoints can be downloaded as a CSV from the tagger tool. 

{: .highlight}
If the point cloud looks upside down (the ceiling is at the bottom and the floor is at the top), go to the "Rotate Map" option in the landing page to rotate the map by 180 degrees along the X-axis.

Click on the "Upload Waypoints" button on the map server landing page. Select the map name and upload the waypoints CSV file.

### Explore waypoints

We provide an augmented reality application to explore the tagged waypoints graph overlaid against the real-world.

<video src="/assets/videos/explore_waypoints.mp4" autoplay loop muted width="500"></video>

{: .important}
The AR application only works on Android device such as phones and tablets with a camera.

Click on the "Explore Waypoints" button on the server landing page. Once the web application opens, click on he AR button at the bottom right corner of the page. The application should localize against the map created in the previous steps and should show the waypoints overlaid against the real-wold.

