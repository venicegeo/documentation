## 07 December 2018

* A custom importer has been written to ingest the Geographic Names Database, the formal gazetteer maintained by NGA.  This is on top of the other gazetteers included in Pelias (Who’s on First, Geonames.org, OpenStreetMap, and Open Addresses).  
* Added `/convert` endpoint that integrates NGA’s Geotrans library for MGRS to decimal degrees and decimal degrees to MGRS conversions. Pelias will now automatically recognize MGRS coordinates (of varying precision) and return point coordinates.  Additionally, Pelias will also return results from other gazetteers that are in proximity to that point, essentially helping to translate between MGRS and real-world entities.  The `/convert` endpoint is extensible, so other coordinate systems could be added.  
* Added administrative boundary search. The Who’s on First gazetteer, which was built by Mapzen to be the foundation dataset in Pelias, excels at defining polygon boundaries for features like neighborhoods, which typically do not have a defined boundary. 
* Added Swagger docs.
