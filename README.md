[![hacs_badge](https://img.shields.io/badge/hacs-default-orange.svg)](https://github.com/custom-components/hacs)
[![ha_version](https://img.shields.io/badge/home%20assistant-2021.12%2B-green.svg)](https://www.home-assistant.io)
![stability-stable](https://img.shields.io/badge/stability-stable-green.svg)
![version](https://img.shields.io/badge/version-3.0.1-green.svg)
![maintained](https://img.shields.io/maintenance/yes/2022.svg)
[![maintainer](https://img.shields.io/badge/maintainer-dsorlov-blue.svg)](https://github.com/DSorlov)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

Home Assistant SL Sensor (HASL)
===============================

This is a platform for Home Assistant that can be used to create "Departure board" or "Traffic Situation" sensors for buses and trains in Stockholm, Sweden. You have to install it as a custom component and you need to get your own API keys from SL / Trafiklab. Originally started with [fredrikbaberg SL sensor](https://github.com/fredrikbaberg/ha-sensor-sl) that was forked into [Home Assistant SL Sensor by DSorlov](https://github.com/DSorlov/hasl-platform) and now moved to its own organisation and life as [Home Assistant SL Sensor Integration](https://github.com/hasl-platform/integration).

![card](https://user-images.githubusercontent.com/8133650/56198334-0a150f00-603b-11e9-9e93-92be212d7f7b.PNG)

This is a custom component so not installed by default in your Home Assistant install. However it can be easily installed and updated using [HACS](https://custom-components.github.io/hacs/) where this integration is included by default under the integration headline.
By using HACS you will also make sure that any new versions are installed by default and as simple as the install itself. We will not be adding ourselfs to the official repo for now due to the work that it takes to manage the administration, perhaps a task you are up for?

## Getting started with HASL
1. [Getting API keys from Trafiklab](trafiklab)
2. Install via [HACS](hacs_install) (recomended) or [manual](manual_install) (not recomended)
3. Configure using GUI, to find Location IDs via [SL Platsuppslag](https://developer.trafiklab.se/api/sl-platsuppslag/konsol)
4. Install [lovelace cards](lovelace_cards) to display in frontend
5. Enjoy!

## Documentation and resources
* [Full documentation](https://github.com/hasl-sensor/integration/blob/master/README.md)
* [Changelog and updates](https://github.com/hasl-sensor/integration/blob/master/CHANGELOG.md)
* [Issues, upcomming features and wishlists](https://github.com/hasl-sensor/integration/issues).
