---
layout: default
title: Home
nav_order: 1
---
# OpenFLAME
{: .no_toc }

*OpenFLAME* is a global-scale federated and widely-distributed mapping and localization service. FLAME stands for Federated Localization and Mapping Engine. Here, we provide the documentation and links to some tools built for *OpenFLAME*.

1. TOC
{:toc}

## Repositories

All the repositories related to OpenFLAME is in the [openflam Github organization](https://github.com/openflam). Some important repositories are:

- [dns-spatial-discovery](https://github.com/openflam/dns-spatial-discovery): The npm and Python library implementing the main OpenFLAME architecture. It includes DNS-based discovery of map servers, device localization with the map servers, and tracking localization confidence scores against local device sensors (VIO).
  
- [spatial-server](https://github.com/openflam/spatial-server): A reference implementation of the map server that works with OpenFLAME. The map server implements a visual positioning system (VPS) using 2-D images. We use neural-network based feature extractor and matcher. See [documentation]({% link pages/tools/map-server.md %}) on how to use the map server.
  
- [geo-domain-explorer](https://github.com/openflam/geo-domain-explorer): Code for the [geo-domain-explorer tool](https://openflam.github.io/geo-domain-explorer/). See [documentation]({% link pages/tools/geodomain-explorer.md %}) for how to use the tool.
  
- [waypoint-tagger](https://github.com/openflam/waypoint-tagger): Code for the [waypoint-tagger tool](https://openflam.github.io/waypoint-tagger/). See [documentation]({% link pages/tools/waypoint-tagger.md %}) for how to use the tool.

## Design

![Architecture](/assets/images/architecture.png){: width="500" }

The above figure shows the architecture of OpenFLAME and the steps involved in an OpenFLAME query. OpenFLAME is implemented as an [open source npm package](https://github.com/orgs/openflam/packages/npm/package/dnsspatialdiscovery). The package code is [available on Github](https://github.com/openflam/dns-spatial-discovery/tree/master/js). 

See the paper for full details on OpenFLAME, its architecture, use cases and philosophy.

## Tools

### VPS Map server

[VPS map server]({% link pages/tools/map-server.md %}) is a reference implementation that provides the Visual Positioning Service (VPS) using neural-network based feature extractor and matcher. The server provide both map creation and localization endpoints. We also provide an augmented reality application that displays the tagged waypoints against the real-world using the VPS. See [Map Server]({% link pages/tools/map-server.md %}) section for documentation on how to create and localize against maps.

<video src="/assets/videos/spatial_server.mp4" autoplay loop muted width="500"></video>

### Geo-domain Explorer

<a href="https://openflam.github.io/geo-domain-explorer/" target="_blank">Geo-domain Explorer tool</a> visualizes the geo-domains that are queried by a OpenFLAME device for a given location and confidence radius. It also automates the creation of DNS records needed to register a map server to make it discoverable by OpenFLAME. See [Geo-domain explorer]({% link pages/tools/geodomain-explorer.md %}) section for documentation.

![Geo Domain Creator Tool Demo](/assets/gifs/geo-domain-explorer/query.gif){: width="500" }

### Waypoint Tagger 

<a href="https://openflam.github.io/waypoint-tagger/" target="_blank">Waypoint Tagger tool</a> helps map creators visualize their 3D map and tag waypoints on it. The creators can also export their waypoints to be used with the map server. See [Waypoint Tagger]({% link pages/tools/waypoint-tagger.md %}) section for documentation.

![Second Tool Configure Demo](/assets/gifs/waypoint-tagger/load-map.gif){: width="500" }
