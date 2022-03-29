[<<Back to index](/)

## Sensors

One objective during development have been to not touch the existing sensors so much to make sure it is compatible as far as possible with the older versions. This table also contains differances between v2.x (Legacy) and current release.

| HASL | HASLv3 | Sensor Name | Description | Notes |
| -- | -- | -- | -- | -- |
| :heavy_check_mark: | :heavy_check_mark: | Departures | Departure information for a given SL Hållplats | Same between both versions. In v3 Deviation Sensor is used for deviation information. |
| :x: | :heavy_check_mark: | Deviations | Is there any changes in traffic?  | This was available in v2 as a integrated data in Departures, now supports both locations and lines to be able to build panels etc. |
| :x: | :heavy_check_mark: | Route | Current best route between A and B | Looks up a current route between point A and B. Takes current traffic and deviations into account. |
| :heavy_check_mark: | :heavy_check_mark: | Traffic Status | High level status for different traffic types | In v2 one combined sensor is created for all traffic types while in v3 a binary_sensor is created for each selected type. |
| :heavy_check_mark:* | :heavy_check_mark: | Vehicle Locations | How many vehicles and their locations | Was experimental in v2 and data is cleaned up in v3. A separate sensor is created for each type of traffic |
| :x: | :heavy_check_mark: | RR Departures | Departure information for a given Hållplats | Lookup departures using ResRobot API instead of SL.
| :x: | :heavy_check_mark: | RR Arrivals | Arrivals information for a given Hållplats | Lookup arrivals using ResRobot API.
| :x: | :heavy_check_mark: | RR Route | Current best route between A and B | Looks up a current route between point A and B using ResRobot API.