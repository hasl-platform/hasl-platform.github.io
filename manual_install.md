## Manual installation (not advised)

The integration can be installed manually by copying some files from this repo to your install. Also you will need to create API key and config as outlined in the previous section.
Note that HASL will not automatically update as newer versions are released so you need to keep track of that yourself. We recomend using HACS as outlined above in the previous section.

Please copy files:

[`hasl/__init__.py`](https://github.com/DSorlov/ha-sensor-sl/blob/hasl/custom_components/hasl/__init__.py) to `<config>/custom_components/hasl/__init__.py`
[`hasl/sensor.py`](https://github.com/DSorlov/ha-sensor-sl/blob/hasl/custom_components/hasl/sensor.py) to `<config>/custom_components/hasl/sensor.py`
[`hasl/manifest.json`](https://github.com/DSorlov/ha-sensor-sl/blob/hasl/custom_components/hasl/manifest.json) to `<config>/custom_components/hasl/manifest.json`

where `<config>` is your Home Assistant configuration directory.

