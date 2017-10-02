# INSPIRE ready Geoserver
INSPIRE ready geoserver (using app-schema from British Geological Survey)

## Background 

Example of INSPIRE and app-schema out of the box compose. The docker compose will build the structure referenced in the following report [INSPIRE WFS cookbook](https://data.gov.uk/sites/default/files/library/INSPIREWFSCookbook_v1.0.pdf): 

The docker compose uses 2 slightly modified images obtained in these repositories:

* [postgis](https://github.com/kartoza/docker-postgis)
* [geoserver](https://github.com/kartoza/docker-geoserver)

## Run build local 

To run it is is best first to build the images:
```
docker-compose build --no-cache
```

And then to run it
```
docker-compose up
```

It is also possible to pull already build images (faster to start)
```
docker-compose -f docker-compose-production.yml up
```

### Testing

Geoserver runs on port 8080 and has the default geoserver login (admin:geoserver). PLEASE DONT USE THIS IN PRODCUTION

Geoserver:
```
http://localhost:8080/geoserver
http://localhost:8080/geoserver/ows?service=wfs&version=2.0.0&request=GetCapabilities
http://localhost:8080/geoserver/wfs?request=GetFeature&service=wfs&version=2.0.0&typeName=gsmlgu:GeologicUnit&outputFormat=gml32&count=2
```

The last should produce a valid XML with information about a Geological Unit


### Issues

PostGIS takes sometime to ingest the data, please run a iotop command on host to see the status

## Versions

* OS Debian Jesse
* Geoserver 2.11.2
* Postgresql 9.5
* Postgis 2.2

## Credits for geoserver

* Tim Sutton (tim@kartoza.com)
* Shane St Clair (shane@axiomdatascience.com)
* Alex Leith (alexgleith@gmail.com)

## Credits for postgis

* Tim Sutton (tim@kartoza.com)


