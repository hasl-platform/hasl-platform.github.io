[<<Back to index](/)

## Location IDs

To get data about a specific stop for depatures or other sensors you will need to have a Location ID. Location IDs are NOT interchangeable between SL and ResRobot so depending on your api you will need to lookup locations via api.

## SL API

The IDs you get here is only for use with the SL sensors.

Go to Find Location IDs via [SL Platsuppslag](https://developer.trafiklab.se/api/sl-platsuppslag/konsol)

## Resrobot API 

The IDs you get here is only for use with the Resrobot sensors.

1. Start a browser window and go to the Developer Tools in Home Assistant
2. Navigate to the Events tab
3. Start listeningen to `hasl3` events
4. Start another browser window and go to the Developer Tools in Home Assistant
5. Navigate to the Services tab
6. Select the `rr_find_location` service, enter your [API keys](trafiklab) for ["ResRobot v2.1"](https://www.trafiklab.se/api/trafiklab-apis/resrobot-v21/) and a search string. Click Call Service.
7. Switch to the first browser window and see the response code and get the id for your location. Currently addresses are NOT supported.

## SL API (alternative method)

The IDs you get here is only for use with the SL sensors. This is a bit harder than the first approach but is available to be common with Resrobot.

1. Start a browser window and go to the Developer Tools in Home Assistant
2. Navigate to the Events tab
3. Start listeningen to `hasl3` events
4. Start another browser window and go to the Developer Tools in Home Assistant
5. Navigate to the Services tab
6. Select the `sl_find_location` service, enter your [API keys](trafiklab) for ["SL Platsuppslag"](https://developer.trafiklab.se/api/sl-platsuppslag) and a search string. Click Call Service.
7. Switch to the first browser window and see the response code and get the id for your location.