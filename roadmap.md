[<< Back to index](/)

## Experimental and upcomming features

So far there is very limited support for other api-functions except what is listed above. However there are some experimentation going on with future functionalities of the platform and this code. Nothing that is decided or ready, but the features may be used as-is for now to experiment and see what can be done. Also, if you extend the code please submit a PR so it can be furthered.

If you have any suggestions do not forget to add them to the issue tracker to be included in HASL 3.0, please use the enhancement label to add your request. [Go do it now!](https://github.com/DSorlov/hasl-platform/issues/new).

To use this stuff you should know your way around advanced customization of your Home Assistant enviroment, but for now three parts exists:

### GUI-Based configuration
Looking into making the configuration GUI-Based instead of using a lot of strange files and stuff. Making it simpler for basic users in other words. We have not started any work on this yet but just to let you know we are thinking of it.. =)

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
