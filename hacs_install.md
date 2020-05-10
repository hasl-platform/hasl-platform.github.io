## Automatic installation using HACS

First, visit [https://www.trafiklab.se/api](https://www.trafiklab.se/api) and create a free account. They provide multiple APIs, the ones you want is ["SL Trafikinformation 4"](https://www.trafiklab.se/api/sl-realtidsinformation-4) and ["SL Störningsinformation 2"](https://www.trafiklab.se/api/sl-storningsinformation-2), optionally you can also register for ["SL Trafikläget 2"](https://www.trafiklab.se/api/sl-trafiklaget-2) to get status sensors. When you have your API keys, you're ready to add the component to your Home Assistant.

This is a custom component so not installed by default in your Home Assistant install. However it can be easily installed and updated using [HACS](https://custom-components.github.io/hacs/) where this integration is included by default under the integration headline.
By using HACS you will also make sure that any new versions are installed by default and as simple as the install itself.

After you added the integration then add the desired configuration in config. Here is an example of a typical configuration:

```yaml
sensor:
- platform: hasl
  ri4key: YOUR-RI4-KEY-HERE
  si2key: YOUR-SI2-KEY-HERE
  tl2key: YOUR-OPTIONAL-TI2-KEY-HERE
  sensors:
   - friendly_name: Mölnvik
     sensor_type: departures
     siteid: 4244
     lines: ['474', '480C']
     direction: 1
   - friendly_name: Trafikstatus
     sensor_type: status
```

Restart Home Assistant to make sure it loads and calls the integration!
