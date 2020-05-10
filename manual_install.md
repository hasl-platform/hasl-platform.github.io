[<<Back to index](/)

## Manual installation (not advised)

The integration can be installed manually by copying some files from this repo to your install. Note that HASL will not automatically update as newer versions are released so you need to keep track of that yourself. We recomend using [HACS](hacs) for install and keeping up to date.

Please copy files:

[`hasl/__init__.py`](https://github.com/hasl-platform/hasl-sensor/blob/master/custom_components/hasl/__init__.py) to `<config>/custom_components/hasl/__init__.py`
[`hasl/sensor.py`](https://github.com/hasl-platform/hasl-sensor/blob/master/custom_components/hasl/sensor.py) to `<config>/custom_components/hasl/sensor.py`
[`hasl/manifest.json`](https://github.com/hasl-platform/hasl-sensor/blob/master/custom_components/hasl/manifest.json) to `<config>/custom_components/hasl/manifest.json`

where `<config>` is your Home Assistant configuration directory.

