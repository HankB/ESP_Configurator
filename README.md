# ESP_Configurator

Provide *nix server and ESP client to support configuration of an ESP or similar device.

## 2025-03-19 Status

* Still in the planning stage. Need to do some additional work with the existing projects before turning attention to this, so "later ..."

## 2025-03-19 Motivation

I have projects that, for example, use an ESP32 to read and publish temperature from a DS18B20 temperature sensor. It's just awkward to have to recompile it for each sensor that I want to deploy. FDurther, I intend to deploy the sensors in multiple locations, each with their own configuration requirements such as WiFi creds(*) and MQTT broker.

(*) The initial version will not include WiFi creds, these will be hard coded.

## 2025-03-19 Plans

* Use UDP broadcast to request configuration, including the MAC address of the ESP client.
* Use UDP point to point to send information (or broadcast if point to point is inconvenient.)
* ESP will be coded in C++ using Arduino/ESP APIs. Perhaps a branch will be provided that uses the ESP-IDF library. At present it is intended that the ESP code be merged in to another existing project.
* Server code can be written in any convenient language.
* Configuration will be stored in an Sqlite database (and some convenieht tool will be suggested for maintaining the database.) Fields in the database will be `MAC address`, `key`, `value`.
* When the server receives a "configure me" request, it will reply with a series of messages, each of which will include `key:value` pairs for all related entries in the database. The `key:value` pairs will be application specific and provided here as test data.

## Errata

* 2025-03-19 This seems like a good project to manage using git subprojects - one for the server and another for the client.
