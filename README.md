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

This is a custom component so not installed by default in your Home Assistant install. However it can be easily installed and updated using [HACS](https://custom-components.github.io/hacs/) where this integration is included by default under the integration headline.
By using HACS you will also make sure that any new versions are installed by default and as simple as the install itself. We will not be adding ourselfs to the official repo for now due to the work that it takes to manage the administration, perhaps a task you are up for?

## Getting started with HASL!
1. [Getting API keys from Trafiklab](trafiklab)
2. Install via [HACS](hacs_install) (recomended) or [manual](manual_install) (not recomended)
3. Customize your install using [configuration](yaml-configuration)
4. Install visual elements to your frontend


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
