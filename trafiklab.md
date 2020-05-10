[<<Back to index](/)

## Apply for free API keys

This project is dependent on a number of APIs to aquire information. The APIs are mostly free but somewhat limited. Read more about that below.

First, visit [https://www.trafiklab.se/api](https://www.trafiklab.se/api) and create a free account.

They provide multiple APIs, the ones you want is
1. ["SL Trafikinformation 4"](https://www.trafiklab.se/api/sl-realtidsinformation-4)
2. ["SL Störningsinformation 2"](https://www.trafiklab.se/api/sl-storningsinformation-2)

Optionally you can also register for
1. ["SL Trafikläget 2"](https://www.trafiklab.se/api/sl-trafiklaget-2) to get status sensors.

When you have your API keys, you're ready to add the component to your Home Assistant either via [HACS](hacs_install) or [manual](manual_install).

## API-call restrictions and optimizations

The `Bronze` level API is limited to 30 API calls per minute, 10.000 per month. With 10.000 calls per month, that allows for less than one call every 4 minute but if you are using multiple sensors this is split between them and each config sensor section can contain a separate pair of api-keys.

The calls have been optimized and are beeing locally cached for the specified freshness, if multiple sensors are using the same siteid there will still only be one call. Caching is done in a file (haslcache.json) that will be automatically created in the configuration directory.

You can also specify a binary_sensor that perhaps is turned of when no-one is at home or similar to reduce the number of calls. Optimizations can be turned of if needed in very specific situation or if you have a high level API-key.
