[<<Back to index](/)

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
