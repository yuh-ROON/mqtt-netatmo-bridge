# mqtt-netatmo-bridge

This is a simple docker container that I use to bridge to/from my MQTT bridge.

I have a collection of bridges, and the general format of these begins with these environment variables:

```yaml
      TOPIC_PREFIX: /your_topic_prefix  (eg: /some_topic_prefix/somthing)
      MQTT_HOST: YOUR_MQTT_URL (eg: mqtt://mqtt.yourdomain.net)
      (OPTIONAL) MQTT_USER: YOUR_MQTT_USERNAME
      (OPTIONAL) MQTT_PASS: YOUR_MQTT_PASSWORD
```

## Documentation
Thanks to @skyynet for some documentation for how to set this up on a Synology NAS (but likely applies to more)!
* English: https://skyynet.de/e-netatmo
* German: https://skyynet.de/netatmo

## Build the image
docker build https://github.com/yuh-ROON/mqtt-netatmo-bridge.git -t mqtt-netatmo-bridge

## Docker Compose
Here's an example docker compose:

```yaml
version: '3.3'
services:
  mqtt-netatmo-bridge:
    image: mqtt-netatmo-bridge:latest
    environment:
      LOGGING_NAME: mqtt-netatmo-bridge
      TZ: YOUR_TIMEZONE (eg: America/Los_Angeles)
      TOPIC_PREFIX: /your_topic_prefix  (eg: /netatmo)
      NETATMO_USER: YOUR_NETATMO_USERNAME,
      NETATMO_PASS: YOUR_NETATMO_PASSWORD,
      NETATMO_CLIENT_ID: YOUR_NETATMO_CLIENT_ID,
      NETATMO_CLIENT_SECRET: YOUR_NETATMO_CLIENT_SECRET,
      MQTT_HOST: YOUR_MQTT_URL (eg: mqtt://mqtt.yourdomain.net)
      (OPTIONAL) MQTT_USER: YOUR_MQTT_USERNAME
      (OPTIONAL) MQTT_PASS: YOUR_MQTT_PASSWORD
      (OPTIONAL) HEALTH_CHECK_PORT: "3001"
      (OPTIONAL) HEALTH_CHECK_TIME: "120"
      (OPTIONAL) HEALTH_CHECK_URL: /healthcheck
```
