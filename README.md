# HA-Vera-Modes
Integrate Vera House Modes with Home Assistant. This updates when the House Mode is changed in Vera, and also changes the mode on Vera when changed in Home Assistant.

This requires Button Card >= 3.0.0. Available in HACS, or see https://github.com/custom-cards/button-card

Buttons may not work in some browsers/UIs

# Installation
Add or update `sensors.yaml` and `rest.yaml` in your homeassistant configuration directory. Be sure to replace [Vera_IP_address] with the IP Address of your Vera.  
In your `configuration.yaml` file, ensure that these lines are present:
```yaml
sensor: !include sensors.yaml
rest_command: !include rest.yaml
```

You must restart Home Assistant for the previous changes to take effect.

In your Lovelace UI, add a Horizontal Stack Card. The code for the stack card is in `vera-button-card.yaml`

# Usage
The card will display the current Vera House Mode.  
Clicking on a button on the card will change the House Mode in Vera.  
The state of `sensor.vera_house_mode` can be used in integrations.  
To programmatically change the House Mode, call the following service:
```yaml
service: rest_command.hm_command
service_data:
  mode: [1,2,3,4]
```
Mode values:  
1: Home  
2: Away  
3: Night  
4: Vacation
