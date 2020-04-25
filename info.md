# sensor.waternsw

Home Assistant sensor for WaterNSW Real Time Data

This component will set up a sensor platform to retrieve data from WaterNSW's Real Time Data platform

[![maintained](https://img.shields.io/maintenance/yes/2020.svg)](#)
[![HitCount](http://hits.dwyl.io/bacco007/sensorwaternsw.svg)](http://hits.dwyl.io/bacco007/sensorwaternsw)
![LastCommit](https://img.shields.io/github/last-commit/bacco007/sensor.waternsw)
![Licence](https://img.shields.io/github/license/bacco007/sensor.waternsw)
![Downloads](https://img.shields.io/github/downloads/bacco007/sensor.waternsw/total)
[![hacs_badge](https://img.shields.io/badge/HACS-Custom-orange.svg)](https://github.com/custom-components/hacs)
![Validate with hassfest](https://github.com/bacco007/sensor.waternsw/workflows/Validate%20with%20hassfest/badge.svg)

[![Buy me a coffee][buymeacoffee-shield]][buymeacoffee]

---

## Table of Contents

- [sensor.waternsw](#sensorwaternsw)
  - [Table of Contents](#table-of-contents)
  - [Installation](#installation)
    - [Manual Installation](#manual-installation)
    - [Installation via Home Assistant Community Store (HACS)](#installation-via-home-assistant-community-store-hacs)
  - [Getting Configuration from Real Time Data Platform](#getting-configuration-from-real-time-data-platform)
  - [Configuration Options](#configuration-options)
    - [Dams - Variables](#dams---variables)
  - [Example Configuration](#example-configuration)
  - [Contributions](#contributions)

---

## Installation

### Manual Installation

1. Using the tool of choice open the directory (folder) for your HA configuration (where you find `configuration.yaml`).
2. If you do not have a `custom_components` directory (folder) there, you need to create it.
3. In the `custom_components` directory (folder) create a new folder called `waternsw`.
4. Download _all_ the files from the `custom_components/waternsw/` directory (folder) in this repository.
5. Place the files you downloaded in the new directory (folder) you created.
6. Create Configuration (see below)
7. Restart Home Assistant

### Installation via Home Assistant Community Store (HACS)

1. Ensure [HACS](http://hacs.xyz/) is installed.
2. Search for and install the "Water NSW" integration
3. Configure the sensor
4. Restart Home Assistant

---

## Getting Configuration from Real Time Data Platform

WaterNSW's Real Time Data Platform can be a little bit tricky to use:

1. Open [https://realtimedata.waternsw.com.au/](https://realtimedata.waternsw.com.au/)
2. From the menu on the left hand side, select the Dam of interest
3. Select the details Tab and note down the following for the Datasource "PROV"
   1. Site Number (Site ID below)
   2. The Variables (2nd & 3rd columns fo table, used for From and To Variables below)
   3. The Unit of measurement is usually in the description (3rd column)

---

## Configuration Options

| Key               | Type     | Required | Description                                            |
| ----------------- | -------- | -------- | ------------------------------------------------------ |
| `name`            | `string` | `True`   | Name of Sensor                                         |
| `icon`            | `string` | `False`  | MDI Icon to be used (default: `mdi:water`)             |
| `scan_interval`   | `number` | `False`  | Number of Seconds between updates (default 10 minutes) |
| `site_id`         | `string` | `True`   | Site Number (from Real Time Data platform)             |
| `from_variable`   | `string` | `True`   | From Variable (from Real Time Data platform)           |
| `to_variable`     | `string` | `True`   | To Variable (from Real Time Data platform)             |
| `unit_of_measure` | `string` | `True`   | Unit of Measurement (from Real Time Data platform)     |

### Dams - Variables

Most Dams on the platform use the same variables - reproduced below, however in some cases the variables may be slightly different due to changes at the dam (eg: capacity changes)

| Data                  | UoM         | From Variable | To Variable | Notes                           |
| --------------------- | ----------- | ------------- | ----------- | ------------------------------- |
| Rainfall              | Millimetres | 10.00         | 10.00       |
| Water Level           | Metres      | 130.00        | 130.00      |
| Water Volume          | Megalitres  | 130.00        | 136.00      |
| Water Volume          | Percentage  | 130.00        | 448.00      |
| Inflow (24hr Total)   | Megalitres  | 422.00        | 422.00      |
| Releases (24hr Total) | Megalitres  | 459.00        | 459.00      |
| Evaporation           | Millimetres | 700.00        | 700.00      | Not all Dams record evaporation |

---

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

---

## Contributions

Please feel free to contribute, be it with Issues or Pull Requests!

[buymeacoffee-shield]: https://www.buymeacoffee.com/assets/img/guidelines/download-assets-sm-2.svg
[buymeacoffee]: https://www.buymeacoffee.com/bacco007
