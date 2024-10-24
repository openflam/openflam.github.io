---
layout: default
parent: Tools
title: Map Server
nav_order: 1
---

# Map server

The [map server](https://github.com/openvps/spatial-server) or the spatial server is a reference implementation for a map server that works within the OpenVPS framework. We use [hloc](https://github.com/cvg/Hierarchical-Localization) (which in turn uses [SuperPoint](https://arxiv.org/abs/1712.07629) and [SuperGlue](https://arxiv.org/abs/1911.11763)) for map creation and localization. The map server provides the following functionalites:

- Map creation and storage along with tools required to transform maps.
- Localization against stored maps.
- Tagging maps with *waypoints*.



## Setting up the map server

Follow instructions on the [Github repository](https://github.com/openvps/spatial-server) to set up the map server. Once the map server is set up, the landing page at <https://localhost:8001/> (replace `localhost` with your IP address if you have set it up on a remote server) should look like this:

![Map server landing page](/assets/images/map-server/landing-page.png){: width="500" }

## Map creation

[TBD]

