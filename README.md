# homebridge-http-slider
A homebridge plugin to provide a simple slider, that calls specific http-urls
at specific states.

(At the moment) There is no polling or requesting of an actual state from an 
http-server possible!

# Installation
1. Install [Homebridge](https://github.com/nfarina/homebridge)
2. Install this plugin `sudo npm install -g homebridge-http-slider`
3. Add this plugin as accessory to your `config.json` file

## Configuration
Inside the Homebridge `config.json`

Mandatory
```json
...
    "accessories": [
        {
```

Mandatory
```json
            "accessory": "Slider",
            "name": "Slider Name",
            "service": "Lightbulb",
            "request_type": "get",
            "http_states": [
                {"url": "http://127.0.0.1/0", "body": "hi"},
                {"url": "http://127.0.0.1/1", "body": "hi"},
                {"url": "http://127.0.0.1/2", "body": "hi"}
            ],
```
* `name` can be freely chosen
* Supported `service`s are `Lightbulb`, `Fan` and `Thermostat`
* `request_type` can be any request type like "get" or "post". 
* `http_states` http-urls who get called when the slider gets set to a specific
  state. A low index in the array represents a low value/state in the slider.

Optional
```json
            "thermo_range_high": 100,
            "thermo_range_low": 0
```
* Interval of values when using the `Thermostat` service

```json
        },
...
```
