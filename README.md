# sensor.waternsw

## Home Assistant sensor for WaterNSW Real Time Data

This component will set up a sensor platform to retrieve data from WaterNSW's Real Time Data platform

## Installation

1. Using the tool of choice open the directory (folder) for your HA configuration (where you find `configuration.yaml`).
2. If you do not have a `custom_components` directory (folder) there, you need to create it.
3. In the `custom_components` directory (folder) create a new folder called `waternsw`.
4. Download _all_ the files from the `custom_components/waternsw/` directory (folder) in this repository.
5. Place the files you downloaded in the new directory (folder) you created.
6. Create Configuration (see below)
7. Restart Home Assistant

## Getting Configuration from Real Time Data Platform

WaterNSW's Real Time Data Platform can be a little bit tricky to use:

1. Open https://realtimedata.waternsw.com.au/
2. From the menu on the left hand side, select the Dam of interest
3. Select the details Tab and note down the following for the Datasource "PROV"
   1. Site Number (Site ID below)
   2. The Variables (2nd & 3rd columns fo table, used for From and To Variables below)
   3. The Unit of measurement is usually in the description (3rd column)

## Configuration Options

| Key               | Type     | Required | Description                                        |
| ----------------- | -------- | -------- | -------------------------------------------------- |
| `name`            | `string` | `True`   | Name of Sensor                                     |
| `site_id`         | `string` | `True`   | Site Number (from Real Time Data platform)         |
| `from_variable`   | `string` | `True`   | From Variable (from Real Time Data platform)       |
| `to_variable`     | `string` | `True`   | To Variable (from Real Time Data platform)         |
| `unit_of_measure` | `string` | `True`   | Unit of Measurement (from Real Time Data platform) |

## Example Configuration

```yaml
sensor:
  - platform: waternsw
    name: Chaffey Dam Volume
    site_id: 419069
    from_variable: 130.00
    to_variable: 136.00
    unit_of_measure: ML
```

## Contributions

Please feel free to contribute, be it with Issues or Pull Requests!