[<<Back to index](/)

## Automatic installation using HACS

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
