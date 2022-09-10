---
title: Home Assistant integration
permalink: /docs/Home-assistant-integration/
---

## Preparing Home Assistant

1.  Install the Mosquitto MQTT broker add-on <https://github.com/home-assistant/addons/blob/master/mosquitto/DOCS.md>

2.  Create login details for the gateway in the configuration tab of the Mosquitto broker addon (you could also create a Home Assistant user instead, as these will be also considered as MQTT broker users)

3.  Add your new MQTT details to the IOWAY gateway configuration page. If Home Assistant is available on your local network, you can use the mDNS address "homeassistant" and the gateway will autodiscover the ip-address.

4.  New Push7 devices will automatically show up in the MQTT integration page ![]({{ site.baseurl }}/assets/img/paste-BAF845AF.png)

