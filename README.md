[![hacs_badge](https://img.shields.io/badge/hacs-default-orange.svg)](https://github.com/custom-components/hacs)
[![ha_version](https://img.shields.io/badge/home%20assistant-0.92%2B-yellow.svg)](https://www.home-assistant.io)
[![stability-stable](https://img.shields.io/badge/stability-released-lightgrey.svg)](#)
[![version](https://img.shields.io/badge/version-2.2.2-green.svg)](#)
[![maintained](https://img.shields.io/maintenance/yes/2020.svg)](#)
[![maintainer](https://img.shields.io/badge/maintainer-daniel%20sörlöv-blue.svg)](https://github.com/DSorlov)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

Home Assistant SL Sensor (HASL)
===============================

This is a platform for Home Assistant that can be used to create "Departure board" or "Traffic Situation" sensors for buses and trains in Stockholm, Sweden. You have to install it as a custom component and you need to get your own API keys from SL / Trafiklab. Originally started with [fredrikbaberg SL sensor](https://github.com/fredrikbaberg/ha-sensor-sl) that was forked into [Home Assistant SL Sensor by DSorlov](https://github.com/DSorlov/hasl-platform) and now moved to its own organisation and life.

![card](https://user-images.githubusercontent.com/8133650/56198334-0a150f00-603b-11e9-9e93-92be212d7f7b.PNG)

This is a custom component so not installed by default in your Home Assistant install. However it can be easily installed and updated using [HACS](https://custom-components.github.io/hacs/) where this integration is included by default under the integration headline.
By using HACS you will also make sure that any new versions are installed by default and as simple as the install itself. We will not be adding ourselfs to the official repo for now due to the work that it takes to manage the administration, perhaps a task you are up for?

## Getting started with HASL!
1. [Getting API keys from Trafiklab](trafiklab)
2. Install via [HACS](hacs_install) (recomended) or [manual](manual_install) (not recomended)
3. Customize your install using [configuration](yaml_configuration)
4. Install [lovelace cards](lovelace_cards) to display in frontend
5. Enjoy!

Also you can find some notes on [upcomming, experiments and roadmap here](roadmap).
