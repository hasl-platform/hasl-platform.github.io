[![hacs_badge](https://img.shields.io/badge/hacs-default-orange.svg)](https://github.com/custom-components/hacs)
[![ha_version](https://img.shields.io/badge/home%20assistant-0.92%2B-yellow.svg)](https://www.home-assistant.io)
[![stability-stable](https://img.shields.io/badge/stability-released-lightgrey.svg)](#)
[![version](https://img.shields.io/badge/version-2.2.2-green.svg)](#)
[![maintained](https://img.shields.io/maintenance/yes/2020.svg)](#)
[![maintainer](https://img.shields.io/badge/maintainer-daniel%20sörlöv-blue.svg)](https://github.com/DSorlov)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

Home Assistant SL Sensor (HASL)
===============================

This is a platform for Home Assistant that can be used to create "Departure board" or "Traffic Situation" sensors for buses and trains in Stockholm, Sweden. You have to install it as a custom component and you need to get your own API keys from SL / Trafiklab. Originally started with [fredrikbaberg SL sensor](https://github.com/fredrikbaberg/ha-sensor-sl) that was forked into [Home Assistant SL Sensor by DSorlov](https://github.com/DSorlov/hasl-platform) and now moved to its own organisation and life.

## Getting started!
1. [Install via HACS](hacs_install) (recomended) or [Manual install](manual_install)

## Configuration variables
| Name | Required? | Description | Default |
|------|-----------|-------------|---------|
|**ri4key**| optional | Your API key from Trafiklab for the Realtidsinformation 4 API (required for departures sensors) ||
|**si2key**| optional | Your API key from Trafiklab for the Störningsinformation 2 API ||
|**tl2key**| optional | Your API key from Trafiklab for the Trafikläget 2 API (required for status sensors) ||
|**version_sensor**| optional| Add a sensor showing component versions | `false` |
|**api_minimization**| optional | Use the api-call-minimization-strategy| `true` |
|**sensors**| | A list of all the sensors to be created. Theese can be of sensor_type `departures`, `status` or `trainlocation`||


## Configuration variables for departure sensors
This sensor type creates a departuresined departure sensor for a specific stop. You can find the ID with some help from another API , ["SL Platsuppslag](https://www.trafiklab.se/api/sl-platsuppslag/konsol)).  In the example above, site 4244 is Mölnvik. This sensor can be used with hasl-cards ([departure-card](https://github.com/hasl-platform/lovelace-hasl-departure-card), [traffic-status-card](https://github.com/hasl-platform/lovelace-hasl-traffic-status-card)) and outputs data as described in the [sensor description](DEPARTURES_OBJECT.md).

| Name | Required? | Description | Default |
|------|-----------|-------------|---------|
|**sensor_type**| yes |  Mandatory configuration for departures sensor (must be set to `departures`) ||
|**friendly_name**| optional | Used as display name ||
|**siteid**| yes | The ID of the bus stop or station you want to monitor.||
|**scan_interval**| optional | Timespan between updates. You can specify `00:01:00` or `60` for update every minute. ||
|**sensor**| optional | Specify the name of a binary_sensor to determine if this sensor should be updated. If sensor is ON, or if this option is not set, update will be done. ||
|**property**| optional | Which property to report as sensor state. Can be one of: `min` minutes to departure (default), `time` next departure time, `deviations` number of active deviations, `refresh` if sensor is refreshing or not, `updated` when sensor data was last updated. ||
|**lines**| optional | An array list of line numbers that you are interested in. Most likely, you only want info on the bus that you usually ride.  If omitted, all lines at the specified site id will be included.  In the example above, lines 474 and 480C will be included. ||
|**direction**| optional | Unless your site id happens to be the end of the line, buses and trains goes in both directions. You can enter **1** or **2** (**0** represents both directions). | 0 |
|**timewindow**| optional | The number of minutes to look ahead when requesting the departure board from the api. Minimum is 5 and maximum is 60. | 60 |

## Configuration variables for status sensors
This sensor type creates a Traffic Situation sensor and shows the all-up trafic situation in the public transportation system. This sensor can be used with hasl-cards ([departure-card](https://github.com/hasl-platform/lovelace-hasl-departure-card), [traffic-status-card](https://github.com/hasl-platform/lovelace-hasl-traffic-status-card)) . and outputs data as described in the [sensor description](STATUS_OBJECT.md)

| Name | Required? | Description |
|------|-----------|-------------|
|**sensor_type**| yes | mandatory configuration for status sensor and must be set to `status` |
|**friendly_name**| optional | Used as display name |
|**scan_interval**| optional| Timespan between updates. You can specify `00:01:00` or `60` for update every minute. |
|**sensor**| optional | Specify the name of a binary_sensor to determine if this sensor should be updated. If sensor is 'on', or if this option is not set, update will be done. |
|**traffic_class**| optional | A comma separated list of the types to present in the sensor if not all (`metro`,`train`,`local`,`tram`,`bus`,`fer`) |

## Display of sensor data
The sensors can be used with multiple cards in hasl-cards ([departure-card](https://github.com/hasl-platform/lovelace-hasl-departure-card), [traffic-status-card](https://github.com/hasl-platform/lovelace-hasl-traffic-status-card)) . There are several cards for different sensors and presentation options for each sensor type.

![card](https://user-images.githubusercontent.com/8133650/56198334-0a150f00-603b-11e9-9e93-92be212d7f7b.PNG)

## API-call restrictions and optimizations

The `Bronze` level API is limited to 30 API calls per minute, 10.000 per month. With 10.000 calls per month, that allows for less than one call every 4 minute but if you are using multiple sensors this is split between them and each config sensor section can contain a separate pair of api-keys.
The calls have been optimized and are beeing locally cached for the specified freshness, if multiple sensors are using the same siteid there will still only be one call. Caching is done in a file (haslcache.json) that will be automatically created in the configuration directory.
You can also specify a binary_sensor that perhaps is turned of when no-one is at home or similar to reduce the number of calls. Optimizations can be turned of if needed in very specific situation or if you have a high level API-key.

## Experimental and upcomming features

So far there is very limited support for other api-functions except what is listed above. However there are some experimentation going on with future functionalities of the platform and this code. Nothing that is decided or ready, but the features may be used as-is for now to experiment and see what can be done. Also, if you extend the code please submit a PR so it can be furthered.

If you have any suggestions do not forget to add them to the issue tracker to be included in HASL 3.0, please use the enhancement label to add your request. [Go do it now!](https://github.com/DSorlov/hasl-platform/issues/new).

To use this stuff you should know your way around advanced customization of your Home Assistant enviroment, but for now three parts exists:

### Train location sensor
This sensor type creates a train location sensor and shows the train locations for subway, and surface trains. This sensor is EXPERIMENTAL and NOT SUPPORTED yet. Outputs json object to be parsed by frontend, but no specific card exists yet. Subject to change.

| Name | Required? | Description |
|------|-----------|-------------|
|**sensor_type** | yes | mandatory configuration for train location sensor and must be set to `trainlocation` |
|**friendly_name**| optional | Used as display name|
|**train_type**| yes | Which train type should this sensor monitor. Choose one of `PT` (pendeltåg),`RB` (roslagsbanan),`TVB` (tvärbanan),`SB` (saltsjöbanan),`LB` (lidingöbanan),`SpvC` (spårväg city),`TB1` (gröna linjen),`TB2` (röda linjen),`TB3` (blåa linjen) |
|**scan_interval**| optional | Timespan between updates. You can specify `00:01:00` or `60` for update every minute.|
|**sensor** | optional | Specify the name of a binary_sensor to determine if this sensor should be updated. If sensor is 'on', or if this option is not set, update will be done.


### Platsuppslag
(Requires PU1-API-Key) The PU1 or [Platsuppslag](https://www.trafiklab.se/api/sl-platsuppslag) API can be used to get the codes for stops needed for configuration as described above. It may also be used to do advanced typeahead searches. There is no GUI provided but there is a services exposed under services: `hasl.find_location`. It requires one argument as a string `search_string` that contains the place to be looked up. Returns the raw api response for now.

Configuration.yaml
```yaml
hasl:
  pu1key: YOUR-PU1-KEY-HERE
```
### Reseplaneraren 3.1
(Requires TP3-API-Key) The TP3 or [Reseplaneraren3.1](https://www.trafiklab.se/api/sl-reseplanerare-31) lets you search for routes, prices and current times in the real-time and planned schedule for the stockholm traffic. This could be used to have a dashboard for the current route to work or something similar. There is no GUI provided but there is two services exposed under services: `hasl.find_trip_id` which accepts a stop id from SL as integers `orig` and `dest` and then returns the raw api response. The second service `hasl.find_trip_loc` instead accepts a logitude and latitude in `orig_lat`, `orig_lon`, `dest_lat` and `dest_lon` and also returns raw response.

Configuration.yaml
```yaml
hasl:
  tp3key: YOUR-TP3-KEY-HERE
```
