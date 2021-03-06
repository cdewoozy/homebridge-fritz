# homebridge-fritz
[![NPM Version](https://img.shields.io/npm/v/homebridge-fritz.svg)](https://www.npmjs.com/package/homebridge-fritz)
[![Build status](https://travis-ci.org/andig/homebridge-fritz.svg?branch=master)](https://travis-ci.org/andig/homebridge-fritz)
[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=HGD5E9L28HQHC)


Homebridge platform plugin for FRITZ!Box.

This plugin exposes:

  - Wlan guest access switch
  - Fritz!DECT outlets (100, 200, 210)
  - Fritz!Powerline outlets (510, 540)
  - Comet!DECT thermostats


## Installation

Follow the homebridge installation instructions at [homebridge](https://www.npmjs.com/package/homebridge).

Install this plugin globally:

```
npm install -g homebridge-fritz
```

Add platform to `config.json`, for configuration see below.


## Configuration

```
{
  "platforms": [
    {
      "platform": "Fritz!Box",
      "name": "My FritzBox",
      "username": "<username>",
      "password": "<password>",
      "url": "http://fritz.box",
      "interval": 60,
      "debug": false
    }
  ]
}

```

The `url`, `interval` and `debug` settings are optional:

  - `url`: Fritz!Box address
  - `interval`: polling interval for updating accessories if state was changed outside homebringe
  - `debug`: if true the smartfritz API calls are logged


## Common Issues / Frequently Asked Questions

  1. homebridge-fritz can't login to the FritzBox
  
    Some users have reported that logging into the FritzBox internally via `https` fails. This seems to be caused by the FritzApp *occupying* the same port.
    In this case you can connect internally via `http` or use the external IP.
  
  2. homebridge-fritz is not able to update my thermostat
  
    Current FritzBox firmwares seem to ignore API updates when the thermostat has been key-locked. 
    No workaround available- please contact AVM to change this behaviour or don't use the locking mechanism.

## Acknowledgements

  - Original non-working fritz accessory https://github.com/tommasomarchionni/homebridge-FRITZBox
  - Platform implementation inspired by https://github.com/rudders/homebridge-platform-wemo.
