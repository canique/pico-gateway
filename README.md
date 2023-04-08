# pico-gateway

[Canique Pico Gateway](http://www.canique.com/pico-gateway) translates wirelessly transmitted messages from Canique sensors into MQTT packets to an MQTT server.

![Canique Pico Gateway](https://www.canique.com/img/1080px/pico-gateway-top.jpg)


## Security

Your Pico Gateway establishes a TLSv1.2 secured connection if you specify the host of your MQTT server as domain name. If you specify it as an IP address though (e.g. in internal networks), then a plain TCP connection is established without TLS. Thus TLS is turned off in MQTT connections if an IP address is specified.   
Please note, that as of now (2023-04), only SSL certificates signed by Let's Encrypt are supported. If you need support for different certificate authorities, please contact Canique Support.


## Locking your Pico Gateway out of the network

If you happen to enter wrong network information (IP, Subnet, Gateway, DNS) into the network settings form, the result can be that your Pico Gateway cannot connect to the network anymore. In such a case you need to open the case of the Pico Gateway (unscrewing the 4 screws on its bottom side). Once the enclosure is open, you'll see a big button labeled RST (either black or red) near a 5 pin connector. While the Pico Gateway is connected to a network cable/to a router and supplied with power, press the RST button and keep it pressed for at least 3 seconds. After 3 seconds the Pico Gateway will change its network settings to DHCP again and then reboot.   
If you keep the RST button pressed for less than 3 seconds, then the Pico Gateway will only reboot without changing the network settings.


## Maximizing wireless range

By default the Pico Gateway's receiver threshold is set to -98 dBm. Pico Gateway (HW rev 0.8.2) is capable of lower thresholds (=longer range), though.   
You can change the threshold in the "Radio Settings" tab to -105 dBm e.g. - you can even go down to -109 (dBm)   
A yellow RX LED inside the Pico Gateway will show how much noise is being received. The LED shines through the case. The goal is to keep the LED off as much as possible. If it is blinking frequently or seems to be on all the time, you will suffer from message loss.   

The reasons for a frequently blinking LED can be:   
- bad quality power supply (with high ripple voltage)
- a device within a radius of approximately 2 meters that is emitting electromagnetic interference (TV, loudspeakers, PC, etc...)
- an antenna that is inadequate (please use the supplied one)

In an experiment where the Pico Gateway was within 2 meters of a personal computer, a threshold setting of less than -104 dBm resulted in a lot of noise being received (RX LED blinking multiple times per second). As soon as the PC was shut down or in standby mode, the RX LED stopped blinking. (In an ideal environment it should only blink when receiving a message from a sensor.)
In a case like this you can either keep the RSSI threshold high or you can move the Pico Gateway away from noise sources and reduce its RSSI threshold down to -109 dBm.

The maximum range achieved with a Pico Gateway (RSSI threshold set to -109 dBm) and a Canique Sensor (with internal wire antenna) was 650 meters without obstacles.
