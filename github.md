# geojson test
https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-diagrams#creating-geojson-and-topojson-maps

The example `geojson` snippet in the official docs not works well.

````
```geojson
{
  "type": "Polygon",
  "coordinates": [
      [
          [-90,30],
          [-90,35],
          [-90,35],
          [-85,35],
          [-85,30]
      ]
  ]
}
```
````

```geojson
{
  "type": "Polygon",
  "coordinates": [
      [
          [-90,30],
          [-90,35],
          [-90,35],
          [-85,35],
          [-85,30]
      ]
  ]
}
```

Instead of this, the following snippet works.

````
```geojson
{
    "type": "FeatureCollection",
    "features": [
        {
            "type": "Feature",
            "properties": {},
            "geometry": {
                "type": "Polygon",
                "coordinates": [
                    [
                        [-90, 30],
                        [-90, 35],
                        [-90, 35],
                        [-85, 35],
                        [-85, 30]
                    ]
                ]
            }
        }
    ]
}
```
````

```geojson
{
    "type": "FeatureCollection",
    "features": [
        {
            "type": "Feature",
            "properties": {},
            "geometry": {
                "type": "Polygon",
                "coordinates": [
                    [
                        [-90, 30],
                        [-90, 35],
                        [-90, 35],
                        [-85, 35],
                        [-85, 30]
                    ]
                ]
            }
        }
    ]
}

```

By setting `"properties"`, the properties of each feature will be displayed on mouse click.

````
```geojson
{"type": "FeatureCollection",
 "features": [
     {"type": "Feature",
      "properties": {"field_id": 1001, "productivity": "good"},
      "geometry": {"type": "Polygon",
                   "coordinates": [[[12.16927, 44.75398],
                                    [12.17158, 44.75012],
                                    [12.16866, 44.74924],
                                    [12.16635, 44.75311],
                                    [12.16927, 44.75398]]]}},
     {"type": "Feature",
      "properties": {"field_id": 1002, "productivity": "fair"},
      "geometry": {"type": "Polygon",
                   "coordinates": [[[12.16326, 44.752143],
                                    [12.16626, 44.753050],
                                    [12.16851, 44.749185],
                                    [12.16548, 44.748270],
                                    [12.16326, 44.752143]]]}},
     {"type": "Feature",
      "properties": {"field_id": 1007, "productivity": "good"},
      "geometry": {"type": "Polygon",
                   "coordinates": [[[12.13494, 44.743663],
                                    [12.13687, 44.743576],
                                    [12.13773, 44.743874],
                                    [12.13966, 44.740659],
                                    [12.13328, 44.738795],
                                    [12.13418, 44.741576],
                                    [12.13494, 44.743663]],
                                   [[12.13621, 44.742436],
                                    [12.13599, 44.742454],
                                    [12.13577, 44.741671],
                                    [12.13583, 44.741364],
                                    [12.13592, 44.741244],
                                    [12.13665, 44.741224],
                                    [12.13671, 44.741607],
                                    [12.13621, 44.742436]]]}}]}
```
````

```geojson
{"type": "FeatureCollection",
 "features": [
     {"type": "Feature",
      "properties": {"field_id": 1001, "productivity": "good"},
      "geometry": {"type": "Polygon",
                   "coordinates": [[[12.16927, 44.75398],
                                    [12.17158, 44.75012],
                                    [12.16866, 44.74924],
                                    [12.16635, 44.75311],
                                    [12.16927, 44.75398]]]}},
     {"type": "Feature",
      "properties": {"field_id": 1002, "productivity": "fair"},
      "geometry": {"type": "Polygon",
                   "coordinates": [[[12.16326, 44.752143],
                                    [12.16626, 44.753050],
                                    [12.16851, 44.749185],
                                    [12.16548, 44.748270],
                                    [12.16326, 44.752143]]]}},
     {"type": "Feature",
      "properties": {"field_id": 1007, "productivity": "good"},
      "geometry": {"type": "Polygon",
                   "coordinates": [[[12.13494, 44.743663],
                                    [12.13687, 44.743576],
                                    [12.13773, 44.743874],
                                    [12.13966, 44.740659],
                                    [12.13328, 44.738795],
                                    [12.13418, 44.741576],
                                    [12.13494, 44.743663]],
                                   [[12.13621, 44.742436],
                                    [12.13599, 44.742454],
                                    [12.13577, 44.741671],
                                    [12.13583, 44.741364],
                                    [12.13592, 44.741244],
                                    [12.13665, 44.741224],
                                    [12.13671, 44.741607],
                                    [12.13621, 44.742436]]]}}]}
```
`geojson` string is easy to generate from a shapefile with `geopandas`.

```python
import geopandas as gpd

geojson_str = gpd.GeoDataFrame.from_file('data/fields.shp').to_crs('epsg:4326').to_json()
```
