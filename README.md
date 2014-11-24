knx2mqtt
========

Overview
--------

knx2mqtt is a gateway between a KNX bus interface and MQTT. It receives group telegrams and publishes them as MQTT topics, and similarily subscribes to MQTT topics and converts them into KNX group writes.

It's intended as a building block in heterogenous smart home environments where an MQTT message broker is used as the centralized message bus.

If you don't understand any of the above, knx2mqtt is most likely not useful to you.


Prerequisites
-------------

* Java 1.7 SE Runtime Environment: https://www.java.com/
* Calimero 2.2.0 or newer: https://github.com/calimero-project/calimero / https://www.auto.tuwien.ac.at/a-lab/calimero.html
* Eclipse Paho: https://www.eclipse.org/paho/clients/java/
* Minimal-JSON: https://github.com/ralfstx/minimal-json / 


EIBD
----

The Calimero library is able to directly talk to EIBnet/IP gateways or routers. However, knx2mqtt can be used in conjunction with 
eibd if eibd is run as an EIBnet/IP server with option "-S". Note that this is not the same as eibd's proprietary TCP protocol
which by default uses TCP port 6720.


Usage
-----

Configuration options can either be specified on the command line, or as system properties with the prefix "knx2mqtt".
Examples:

    java -jar knx2mqtt.jar knx.ip=127.0.0.1
    
    java -Dknxmqtt.knx.ip=127.0.0.1 -jar knx2mqtt.jar
    
### Available options:    

- knx.type

  Connection type. Can be either TUNNELING or ROUTING. Defaults to TUNNELING.

- knx.ip
  
  IP address of the EIBnet/IP server/gateway (no default)
  
- knx.port

  Port of the EIBnet/IP server/gateway. Defaults to 3671.

- knx.localip
  
  IP address (interface) to use for originating EIBnet/IP messages. No default, mainly useful
  in ROUTING mode to specify the multicast interface.
  
- knx.groupaddresstable

  A ETS4 group address export file in XML format. No default. If specified, received group addresses
  are translated to their assigned names before they are published.

- mqtt.broker

  ServerURI of the MQTT broker to connect to. Defaults to "tcp://localhost:1883".
  
- mqtt.clientid

  ClientID to use in the MQTT connection. Defaults to "knx2mqtt".
  
- mqtt.topic

  The topic prefix used for publishing and subscribing. Defaults to "knx/".

  
  
Changelog
---------
(work in progress)
 