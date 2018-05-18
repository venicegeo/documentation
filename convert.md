# Convert endpoint

The `/convert` endpoint integrates the [Geotrans MGRS Converter](https://github.com/venicegeo/geotrans-mgrs-converter) to convert between Military Grid Reference System (MGRS) coordinates and geocentric coordinates using NGA's Geotrans C++ libraries.

Parameter | Type | Required | Accepted values
--- | --- | --- | ---
`to`| string | yes | mgrs or decdeg
`from` | string | yes | mgrs or decdeg
`datum` | string | yes | https://geocap.atlassian.net/wiki/spaces/ug/pages/7372992/Datums+and+coordinate+systems

## Convert from MGRS coordinates to decimal degrees

To convert MGRS coordinates to decimal degrees, specify the MGRS coordinates using the `q` parameter. For example:

> /v1/convert?from=mgrs&to=decdeg&q=37UDB13187997

Output for the example above looks like:

```
{
    "type": "Feature",
    "geometry": {
        "type": "Point",
        "coordinates": [
            37.616512715282965,
            55.75761701627411
        ]
    },
    "properties": {
        "name": "37UDB13187997",
        "from": "mgrs",
        "to": "decdeg"
    }
}
```

## Convert from decimal degrees to MGRS coordinates

To convert decimal degrees to MGRS coordinates, specify the geocentric coordinates using the `lat` and `lon` parameters. For example:

> /v1/convert?from=decdeg&to=mgrs&lat=37.616512715282965&lon=55.75761701627411

Output for the example above looks like:

```
{
    "type": "Feature",
    "geometry": {
        "type": "Point",
        "coordinates": [
            37.616512715282965,
            55.75761701627411
        ]
    },
    "properties": {
        "name": "37UDB13187997",
        "from": "decdeg",
        "to": "mgrs"
    }
}
```

## Error handling

Geotrans will return errors if parameters are missing or invalid, or if unsupported coordinate types are submitted.

Error code | Definition
--- | ---
422 | https://tools.ietf.org/html/rfc4918#page-78
