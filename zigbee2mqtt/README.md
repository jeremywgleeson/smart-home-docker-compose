Zigbee2mqtt was added because it has better support for my cat feeder. You can also use ZHA add-on to home assistant and pass the usb device through to the container.

The following is a base config, you may need to modify the usb device/network key.

```yaml
permit_join: true  # Allow new devices to join automatically 
homeassistant: true
mqtt:
  base_topic: zigbee2mqtt
  server: mqtt://mosquitto
serial:
  port: /dev/ttyUSB0
frontend:
  port: 80
advanced:
  network_key: GENERATE
  homeassistant_legacy_entity_attributes: false
  legacy_api: false
  legacy_availability_payload: false
device_options:
  legacy: false
```
