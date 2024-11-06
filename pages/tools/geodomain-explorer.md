---
layout: default
parent: Tools
title: Geo-domain Explorer
nav_order: 2
---

# Geo-domain Explorer

<a href="https://anon-vps.github.io/geo-domain-explorer/" target="_blank">Geo-domain Explorer tool</a> helps visualize geo-domains queried by the OpenFLAME client at a given location. It also automates the creation of DNS records that are needed to register map servers and make them discoverable by OpenFLAME.

## Visualize geo-domains queried

To show geo-domains that are queried by a client at a location, select the "**Draw Marker**" option on the left (the button that looks like a black balloon with a white circle). Once selected, click anywhere on the map. The purple squares show the geo-domains (or the corresponding S2 cells) that are queried. Use the "Geolocation Error" slider to change the confidence radius and notice how the geo-domains queried change.

![Geo Domain Creator Tool Demo](/assets/gifs/geo-domain-explorer/query.gif){: width="500" }

{: .highlight}
Click on the red "Clear marker" button to clear the marker and the S2 cells.

## Generate DNS zonefiles

Follow the steps below to generate DNS zonefiles for a map server.

### Draw a boundary around the region covered by the map

Select the "**Draw Polygon**" tool on the left. Draw a polygon that covers the region where the map server provides localization service. A reasonable guess for the boundary is acceptable; it does not have to be exact. 

{: .important}
The points in the polygon always have to be selected in the **clockwise** order. 

![Geo Domain Creator Tool Demo](/assets/gifs/geo-domain-explorer/create-box.gif){: width="500" }


### Generate Cells

Use the "Maximum number of cells" slider to upper bound the number of cells generated. Higher the number of cells, better is the region-covering approximation. However, this also leads to an equally large number of DNS records in the generated zone file.

Click on the red "Generate Cells" button to generate cells.

![Geo Domain Creator Tool Demo](/assets/gifs/geo-domain-explorer/gen-cells.gif){: width="500" }

### Generate Zone File

Fill in the form with information about the DNS zone. 

{: .highlight}
Scroll in the right pane to see the full form.

The first section is on `SOA` (Start of Authority) record. Description of the fields in `SOA RDATA` borrowed from [RFC 1035](https://datatracker.ietf.org/doc/html/rfc1035#autoid-31):

```
MNAME           The <domain-name> of the name server that was the
                original or primary source of data for this zone.
RNAME           A <domain-name> which specifies the mailbox of the
                person responsible for this zone.
REFRESH         A 32 bit time interval before the zone should be
                refreshed.
RETRY           A 32 bit time interval that should elapse before a
                failed refresh should be retried.
EXPIRE          A 32 bit time value that specifies the upper limit on
                the time interval that can elapse before the zone is no
                longer authoritative.
MINIMUM         The unsigned 32 bit minimum TTL field that should be
                exported with any RR from this zone.
```

The "RR Records" section is specific to OpenFLAME records. 

***Suffix***: The suffix to be added to geo-domains. We believe this should be a TLD of its own. But for now, this can be any domain that the OpenFLAME client is configured to disocver.

***RR type***: Choose from the list. MCNAME and MNS are described in the paper (Section 4.2).

***RR data***: The address of the map server.

***TTL***: Time to Live for caching.

After filling the form, click on "Generate Zone File" button to generate the zone file. Note that the `MCNAME` and `MNS` records are wrapped in `TXT` so the zone file can work with any existing DNS server.

![Geo Domain Creator Tool Demo](/assets/gifs/geo-domain-explorer/gen-zonefile.gif){: width="500" }
