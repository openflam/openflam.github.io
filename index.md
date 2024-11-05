---
layout: default
title: Home
nav_order: 1
---
# Mercator

*Mercator* is a global-scale federated and widely-distributed mapping and localization service. Here, we provide the documentation and links to some tools built for *Mercator*.

## VPS Map server

[VPS map server]({% link pages/tools/map-server.md %}) is a reference implementation that provides the Visual Positioning Service (VPS) using neural-network based feature extractor and matcher. The server provide both map creation and localization endpoints. We also provide an augmented reality application that displays the tagged waypoints against the real-world using the VPS. See [Map Server]({% link pages/tools/map-server.md %}) section for documentation on how to create and localize against maps.

<video src="/assets/videos/spatial_server.mp4" autoplay loop muted width="500"></video>

## Geo-domain Explorer

<a href="https://openvps.github.io/geo-domain-explorer/" target="_blank">Geo-domain Explorer tool</a> visualizes the geo-domains that are queried by a Mercator device for a given location and confidence radius. It also automates the creation of DNS records needed to register a map server to make it discoverable by Mercator. See [Geo-domain explorer]({% link pages/tools/geodomain-explorer.md %}) section for documentation.

![Geo Domain Creator Tool Demo](/assets/gifs/geo-domain-explorer/query.gif){: width="500" }

## Waypoint Tagger 

<a href="https://openvps.github.io/waypoint-tagger/" target="_blank">Waypoint Tagger tool</a> helps map creators visualize their 3D map and tag waypoints on it. The creators can also export their waypoints to be used with the map server. See [Waypoint Tagger]({% link pages/tools/waypoint-tagger.md %}) section for documentation.

![Second Tool Configure Demo](/assets/gifs/waypoint-tagger/load-map.gif){: width="500" }
