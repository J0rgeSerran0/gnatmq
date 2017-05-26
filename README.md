### Note: this is a fork from the Paolo Patierno repo that fix some bugs or issues I have experimented using this library in production.

#### Three (3) bugs resolved in this repo:
* MqttClient

Bug resolution:
Is not a good idea throw an exception in the Publish method.
Return 0 should be better instead throw an exception.
As a plus, should be interesting register a log if we want to trace this situation (nos implemented).

* MqttPublisherManager

Bug resolution:
Avoid a strange situation when a subscription client comes to null.
Really, is not a normal situation, but I have noticed that sometimes, a subscription client could be null.
In these cases, an exception is generated in runtime.
Here, I mitigate this behaviour avoiding an exception.
As a plus, should be interesting register a log if we want to trace this situation (nos implemented).

* MqttSubscriberManager

Bug resolution:
"The collection has been modified while accessing it"
The Get methods have not the lock action.
A concurrent action could generate an exception in runtime.
This code, resolves this bug.


# GnatMQ

![](images/gnat.jpg)

GnatMQ - MQTT Broker for .NET and WinRT

*Project Description*

Project to develop a broker (server) for the MQTT protocol, an M2M Internet-of-Things communication protocol based on .Net Framework. It works on WinRT platforms too (Windows 8.1, Windows Phone 8.1 and Windows 10) and .Net Compact Framework 3.9 (Windows Embedded Compact).

MQTT, short for Message Queue Telemetry Transport, is a light weight messaging protocol that enables embedded devices with limited resources to perform asynchronous communication on a constrained network.

Developed by IBM and Eurotech, the MQTT protocol is released as an open standard and being standardized by OASIS (Organization for the Advancement of Structured Information Standard), a non-profit consortium that drives the development, convergence and adoption of open standards for the global information society.

In general, the MQTT environment consists of multiple clients and a server, called broker.

This project is created to develop an MQTT broker.  While there are other MQTT broker project, this project is created to provide additional resources to learn and engage in developing useful resources for the MQTT protocol, in conjunction with the M2Mqtt project, a .NET client library for MQTT that supports .NET Framework, .NET Compact Framework and .NET Micro Framework.

The project has an official website here :  http://www.m2mqtt.net

For more information about MQTT, visit: http://www.mqtt.org

For more information about OASIS, visit: https://www.oasis-open.org

There is an MQTT client, M2Mqtt released as community resource on this GitHub repo : https://github.com/ppatierno/m2mqtt

*Main features included in the current release :*

* All three Quality of Service (QoS) Levels (at most once, at least once, exactly once);
* Clean session;
* Retained messages;
* Will message (QoS, topic and message);
* Username/Password via a User Access Control;
* Subscription to topics with wildcards;
* Publish and subscribe handle using inflight queue;
* Security connection with SSL/TLS;

Features not included in the current release :

* Broker configuration using a simple config file;
* Bridge configuration (broker to broker);
* Sessions, retained and will messages persisted at broker shutdown (ex. database); 
