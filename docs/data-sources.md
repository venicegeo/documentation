# Data sources with supported importers

Pelias is built with a mostly data-agnostic architecture: any datasource that can be converted into the Elasticsearch document format used by Pelias can be imported and geocoded against. Pelias currently has support for five importers, and can be customized to include additional importers.

Attribution is required for many of data providers. Some license information is listed here, but you are responsible for researching each project to follow their license terms.

## NGA Geographic Names Database

`sources=geographicnames` | `sources=gndb`

Layers:

- `venue`
- `country`
- `macroregion`
- `region`
- `county`
- `localadmin`
- `locality`
- `neighbourhood`
- `coarse` (alias for simultaneously using all the above)

[NGA's Geographic Names Database](http://geonames.nga.mil/gns/html/index.html) is the National Geospatial-Intelligence Agency's official repository of foreign place-name decisions approved by the U.S. Board on Geographic Names (BGN). The geographic area of coverage is worldwide, excluding the United States and Antarctica. The data served are in a geographic coordinate system based on the WGS84 datum and ellipsoid. Geographic coordinates are approximate and are intended for finding purposes. The data are served by the GEOnet Names Server (GNS); the database is updated weekly.

There are no licensing requirements or restrictions in place for the use of the GNS data. However, the following citation is recommended to identify the GNS as a source:

Toponymic information is based on the Geographic Names Data Base, containing official standard names approved by the United States Board on Geographic Names and maintained by the National Geospatial-Intelligence Agency. The National Geospatial-Intelligence Agency name, initials, and seal are protected by 10 United States Code Section 425.

## OpenAddresses

`sources=openaddresses` | `sources=oa`

Layers:

- `address`

OpenAddresses is a collection of over 300 million addresses around the world. Data in OpenAddresses only comes from national, state, and local governments, so this data is highly authoritative. Because it consists of entirely bulk imports, OpenAddresses is a large, global, and rapidly growing dataset. Many countries, particularly in Europe, now have every address represented in OpenAddresses.

OpenAddresses is by far the largest dataset by number of records used by Pelias. Even though it only contains address data (as in no building names or other metadata), it's a great resource for global geocoding.

The license for each individual source within OpenAddresses differs. Many of the sources require attribution, and many others have a share-alike clause.
*Note:* Pelias does _not_ currently return license information directly, but the license and attribution requirements for each source within OpenAddresses can be determined from the machine-readable `state.txt` file published on the OpenAddresses website.

## Who's on First

`sources=whosonfirst` | `sources=wof`

Layers:

- `country`
- `macroregion`
- `region`
- `macrocounty`
- `county`
- `localadmin`
- `locality`
- `borough`
- `neighbourhood`
- `coarse` (alias for simultaneously using all the above)

[Who's on First](https://www.whosonfirst.org/) is an open-data directory of worldwide administrative places. Originally started at Mapzen, it is the primary provider of:

- Countries
- Macroregions (for example, England is a Macroregion within the United Kingdom)
- Regions (for example, states, provinces)
- Macro-counties (for example, [Departments of France](https://en.wikipedia.org/wiki/Departments_of_France))
- Counties
- Localities (cities, towns, hamlets)
- Neighbourhoods

Additionally, for addresses, venues, and points of interest coming from OpenStreetMap, Geonames, and OpenAddresses, Pelias uses Who's on First to provide standardized fields for the country, region, locality, and neighbourhood.

[License](https://github.com/whosonfirst/whosonfirst-data/blob/master/LICENSE.md)

## OpenStreetMap

`sources=openstreetmap` | `sources=osm`

Layers:

- `address`
- `venue`
- `street`

OpenStreetMap is a community-driven, editable map of the world. It prioritizes local knowledge and individual contributions over bulk imports, which often means it has excellent coverage even in remote areas where no large-scale mapping efforts have been attempted. OpenStreetMap contains information on landmarks, buildings, roads, and natural features.

With its coverage of roads as well as rich metadata, OpenStreetMap is arguably the most valuable dataset used by Pelias for general usage.

All OpenStreetMap data is licensed under the ODbL, a [share-alike](https://en.wikipedia.org/wiki/Share-alike) license which also requires attribution.

**Note:** There are _two_ importers for OSM data. The main importer, [pelias/openstreetmap](https://github.com/pelias/openstreetmap/), handles venues and addresses. The [pelias/polylines](https://github.com/pelias/polylines) importer handles streets, since dealing with line geometry is a special challenge.

## Geonames

`sources=geonames` | `sources=gn`

Layers:

- `venue`
- `country`
- `macroregion`
- `region`
- `county`
- `localadmin`
- `locality`
- `neighbourhood`
- `coarse` (alias for simultaneously using all the above)

[Geonames](http://www.geonames.org/) is an aggregation of many authoritative and non-authoritative datasets. It contains information on everything from country borders to airport names to geographical features. While Geonames does not contain any shape data (such as country borders), it does have a powerful and well defined hierarchy to describe the relationships between different records. This custom hierarchy makes it harder to use in combination with data from other sources, but the  [Who's On First](https://www.whosonfirst.org) project will help by providing concordance between Geonames and other datasets.

In the meantime, Geonames still provides a wide variety of useful data that helps augment the other datasets used by Pelias.

Geonames data is licensed [CC-BY-3.0](http://creativecommons.org/licenses/by/3.0/).
