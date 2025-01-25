+++
title = "Supported Device Types"
chapter = false
weight = 10
+++

In order to be certified a Matter device must conform to one of the approved device types.

As of Matter 1.4 the following types are certifiable.

- [Utility Device Types](#utility-device-types)
  - [Root Node](#root-node)
  - [Power Source](#power-source)
  - [OTA Requestor](#ota-requestor)
  - [OTA Provider](#ota-provider)
  - [Bridged Node](#bridged-node)
  - [Electrical Sensor](#electrical-sensor)
  - [Device Energy Management](#device-energy-management)
- [Application Device Types](#application-device-types)
  - [Lighting](#lighting)
    - [On/Off Light](#onoff-light)
    - [Dimmable Light](#dimmable-light)
    - [Color Temperature Light](#color-temperature-light)
    - [Extended Color Light](#extended-color-light)
  - [Smart Plugs/Outlets and Other Actuators](#smart-plugsoutlets-and-other-actuators)
    - [On/Off Plug in Unit](#onoff-plug-in-unit)
    - [Dimmable Plug in Unit](#dimmable-plug-in-unit)
    - [Pump](#pump)
    - [Water Valve](#water-valve)
  - [Switches and Controls](#switches-and-controls)
    - [On/Off Light Switch](#onoff-light-switch)
    - [Dimmer Switch](#dimmer-switch)
    - [Color Dimmer Switch](#color-dimmer-switch)
    - [Control Bridge](#control-bridge)
    - [Pump Controller](#pump-controller)
    - [Generic Switch](#generic-switch)
  - [Sensors](#sensors)
    - [Contact Sensor](#contact-sensor)
    - [Light Sensor](#light-sensor)
    - [Occupancy Sensor](#occupancy-sensor)
    - [Temperature Sensor](#temperature-sensor)
    - [Pressure Sensor](#pressure-sensor)
    - [Flow Sensor](#flow-sensor)
    - [Humidity Sensor](#humidity-sensor)
    - [On/Off Sensor](#onoff-sensor)
    - [Smoke CO Alarm](#smoke-co-alarm)
    - [Water Freeze Detector](#water-freeze-detector)
    - [Water Leak Detector](#water-leak-detector)
    - [Rain Sensor](#rain-sensor)
  - [Closures](#closures)
    - [Door Lock](#door-lock)
    - [Door Lock Controller](#door-lock-controller)
    - [Window Covering](#window-covering)
    - [Window Covering Controller](#window-covering-controller)
  - [HVAC](#hvac)
    - [Heating/Cooling Unit](#heatingcooling-unit)
    - [Heat Pump](#heat-pump)
    - [Thermostat](#thermostat)
    - [Water Heater](#water-heater)
    - [Fan](#fan)
    - [Air Purifier](#air-purifier)
    - [Air Quality Sensor](#air-quality-sensor)
  - [Media](#media)
    - [Basic Video Player](#basic-video-player)
    - [Casting Video Player](#casting-video-player)
    - [Speaker](#speaker)
    - [Content App](#content-app)
    - [Casting Video Client](#casting-video-client)
    - [Video Remote Control](#video-remote-control)
  - [Robotic Devices](#robotic-devices)
    - [Robotic Vacuum Cleaner](#robotic-vacuum-cleaner)
  - [Appliances](#appliances)
    - [Refrigerator](#refrigerator)
    - [Temperature Controlled Cabinet](#temperature-controlled-cabinet)
    - [Room Air Conditioner](#room-air-conditioner)
    - [Laundry Washer](#laundry-washer)
    - [Dishwasher](#dishwasher)
    - [Laundry Dryer](#laundry-dryer)
    - [Cook Surface](#cook-surface)
    - [Cooktop](#cooktop)
    - [Oven](#oven)
    - [Extractor Hood](#extractor-hood)
    - [Microwave Oven](#microwave-oven)
  - [Energy Devices](#energy-devices)
    - [Battery Storage](#battery-storage)
    - [EVSE](#evse)
    - [Solar Power](#solar-power)

## Utility Device Types

Utility device types may be include in any device.

### Root Node

All devices must include a Root Node on Endpoint 0. This endpoint is akin to a "read me first" endpoint that describes itself and the other endpoints that make up the node.

### Power Source

This utility device type can be used on one or more endpoints to describe the configuration and capabilities of a physical power source that provides power to one or more endpoints on a node.

### OTA Requestor

An OTA Requestor is a device that is capable of receiving an OTA software update.

### OTA Provider

An OTA Provider is a node that is capable of providing an OTA software update to other nodes on the same fabric.

### Bridged Node

A Bridged Node root endpoint is akin to a "read me first" endpoint that describes itself and any other endpoints that make up the Bridged Node. A Bridged Node endpoint represents a device on a foreign network, but is not the root endpoint of the bridge itself.

### Electrical Sensor

An Electrical Sensor device measures the electrical power and/or energy passing through it. This device type can be added to any matter device so that its electrical power and energy consumption or production can be reported.

### Device Energy Management

A Device Energy Management device provides reporting and optionally adjustment of the electrical power planned on being consumed or produced by the device. 

This allows it to be used to help energy management systems to optimize the energy use across multiple devices in the home (e.g. to match the local solar power being generated, or to provide assistance to the grid). 


## Application Device Types

### Lighting

#### On/Off Light

The On/Off Light is a lighting device that is capable of being switched on or off by means of a bound controller device such as an On/Off Light Switch or a Dimmer Switch. In addition, an on/off light is also capable of being switched by means of a bound occupancy sensor.

#### Dimmable Light

A Dimmable Light is a lighting device that is capable of being switched on or off and the intensity of its light adjusted by means of a bound controller device such as a Dimmer Switch or a Color Dimmer Switch. In addition, a Dimmable Light device is also capable of being switched by means of a bound occupancy sensor or other device(s).

#### Color Temperature Light

A Color Temperature Light is a lighting device that is capable of being switched on or off, the intensity of its light adjusted, and its color temperature adjusted by means of a bound controller device such as a Color Dimmer Switch.

#### Extended Color Light

An Extended Color Light is a lighting device that is capable of being switched on or off, the intensity of its light adjusted, and its color adjusted by means of a bound controller device such as a Color Dimmer Switch or Control Bridge. The device supports adjustment of color by means of hue/saturation, enhanced hue, color looping, XY coordinates, and color temperature. In addition, the extended color light is also capable of being switched by means of a bound occupancy sensor.

### Smart Plugs/Outlets and Other Actuators

#### On/Off Plug in Unit

An On/Off Plug-in Unit is a device that is capable of being switched on or off by means of a bound controller device such as an On/Off Light Switch or a Dimmer Switch. The On/Off Plug-in Unit is typically used to control a conventional non-communicating light by switching its mains connection. Other appliances can be controlled this way as well.

#### Dimmable Plug in Unit

A Dimmable Plug-In Unit is a device that is capable of being switched on or off and have its level adjusted by means of a bound controller device such as a Dimmer Switch or a Color Dimmer Switch. The Dimmable Plug-in Unit is typically used to control a conventional non-communicating light through its mains connection using phase cutting.

#### Pump

A Pump device is a pump that may have variable speed. It may have optional built-in sensors and a regulation mechanism. It is typically used for pumping fluids like water.

#### Water Valve

A Water Valve can be used to control the flow of water, including automatic closing after a specified duration, with optional features to support opening levels. It may optionally include flow measurement sensors.

### Switches and Controls

#### On/Off Light Switch

An On/Off Light Switch is a controller device that, when bound to a lighting device such as an On/Off Light, is capable of being used to switch the device on or off.

#### Dimmer Switch

A Dimmer Switch is a controller device that, when bound to a lighting device such as a Dimmable Light, is capable of being used to switch the device on or off and adjust the intensity of the light being emitted.

#### Color Dimmer Switch

A Color Dimmer Switch is a controller device that, when bound to a lighting device such as an Extended Color Light, is capable of being used to adjust the color of the light being emitted.

#### Control Bridge

A Control Bridge is a controller device that, when bound to a lighting device such as an Extended Color Light, is capable of being used to switch the device on or off, adjust the intensity of the light being emitted and adjust the color of the light being emitted. In addition, a Control Bridge device is capable of being used for setting scenes.

#### Pump Controller

A Pump Controller device is capable of configuring and controlling a Pump device.

#### Generic Switch

A generic switch can be either momentary or latching in state, with multiple positions.

The Generic Switch device type and the On/Off Light Switch device type both convey information about interactions with a switch to another device.

- The On/Off Light Switch will send On/Off/Toggle commands from its On/Off (client) cluster to a device implementing the On/Off (server) cluster to control the on/off functionality of that device. An On/Off Light Switch device can also implement Groups and Scenes clusters and thus send group and scene commands. Basically, it is targeted at directly sending control commands to other devices. The binding table is used to tell the device where to send the commands.
- The Generic Switch device type will send updates of attributes (for Latching Switch only) and events to subscribed parties which implement the Switch client cluster, as indications of inter­ action with the switch - leaving the interpretation (e.g. which device should be actuated because of the interaction) to the subscribed party. So it can be compared to a sensor-type device.

This allows a more comprehensive controller to combine the information from the switch with other inputs or information sources (e.g. time of day, user presence) to determine which control commands (e.g. on/off, scene recall, attribute change) are sent to other devices in the network.

### Sensors

#### Contact Sensor

The Contact Sensor is a device that reports a boolean state, typically open/closed.

#### Light Sensor

A Light Sensor device is a measurement and sensing device that is capable of measuring and reporting the intensity of light (illuminance) to which the sensor is being subjected.

#### Occupancy Sensor

An Occupancy Sensor is a measurement and sensing device that is capable of measuring and reporting the occupancy state in a designated area.

#### Temperature Sensor

A Temperature Sensor device reports measurements of temperature.

#### Pressure Sensor

A Pressure Sensor device measures and reports the pressure of a fluid.

#### Flow Sensor

A Flow Sensor device measures and reports the flow rate of a fluid.

#### Humidity Sensor

A humidity sensor (in most cases a Relative humidity sensor) reports humidity measurements.

#### On/Off Sensor

An On/Off Sensor is a measurement and sensing device that, when bound to a lighting device such as a Dimmable Light, is capable of being used to switch the device on or off.

#### Smoke CO Alarm

A Smoke CO Alarm device is capable of sensing smoke, carbon monoxide or both. It is capable of issuing a visual and audible alert to indicate elevated concentration of smoke or carbon monoxide.
Smoke CO Alarms are capable of monitoring themselves and issuing visual and audible alerts for hardware faults, critical low battery conditions, and end of service. Optionally, some of the audible alerts can be temporarily silenced. Smoke CO Alarms are capable of performing a self-test which performs a diagnostic of the primary sensor and issuing a cycle of the audible and visual life safety alarm indications.
Some smoke alarms MAY be capable of adjusting sensitivity. Smoke CO Alarm MAY have the ability to detect and report humidity levels, temperature levels, and contamination levels.

#### Water Freeze Detector

A Water Freeze Detector device is able to indicate the likelihood that water could potentially freeze in the current ambient conditions.

#### Water Leak Detector

A Water Leak Detector device is able to indicate if a water leak is detected.

#### Rain Sensor

A Rain Sensor device is able to indicate if rain is detected.

### Closures

#### Door Lock

A Door Lock is a device used to secure a door. It is possible to actuate a door lock either by means of a manual or a remote method.

#### Door Lock Controller

A Door Lock Controller is a device capable of controlling a door lock.

#### Window Covering

A window covering is a device that actuates a cover for a window, typically a blind. The covering can be vertical or horizontal and optionally the tilt of the sections in the covering can be changed.

#### Window Covering Controller

A Window Covering Controller is a device that controls a window covering device.

### HVAC

#### Heating/Cooling Unit

A Heating/Cooling Unit is a device capable of heating or cooling a space in a house. It is not mandatory to provide both functionalities (for example, the device may just heat but not cool). It may be an indoor air handler.

#### Heat Pump

A Heat Pump device is a device that uses electrical energy to heat either spaces
or water tanks using ground, water or air as the heat source. These typically
can heat the air or can pump water via central heating radiators or underfloor
heating systems. It is typical to also heat hot water and store the heat in a
hot water tank.

Note that the Water Heater device type can also be heated by a heat pump and has
similar requirements, but that device cannot be used for heating of spaces.

#### Thermostat

A Thermostat device is capable of having either built-in or separate sensors for temperature, humidity or occupancy. It allows the desired temperature to be set either remotely or locally. The thermostat is capable of sending heating and/or cooling requirement notifications to a heating/cool­ ing unit (for example, an indoor air handler) or is capable of including a mechanism to control a heating or cooling unit directly.

#### Water Heater

A water heater is a device that is generally installed in properties to heat
water for showers, baths etc.

#### Fan

#### Air Purifier

An Air Purifier is a standalone device that is designed to clean the air in a room.
It is a device that has a fan to control the air speed while it is operating. Optionally, it can report on the condition of its filters.

#### Air Quality Sensor

This defines conformance for the Air Quality Sensor device type.
An air quality sensor is a device designed to monitor and measure various parameters related to the quality of ambient air in indoor or outdoor environments.

### Media

#### Basic Video Player

A Basic Video Player  represents a device that is able to play media to a physical output or to a display screen which is part of the device.
A Basic Video Player has playback controls (play, pause, etc.) and keypad remote controls (up, down, number input), but is not able to launch content and is not a content app platform.
For example, a Basic Video Player can be a traditional TV device a physical media playback device such as a DVD Player, or a device that provides input to another device like a TV or computer monitor.

#### Casting Video Player

A Casting Video Player  represents a device that is able to play media to a physical  output or to a display screen which is part of the device.
A Casting Video Player has basic controls for playback (play, pause, etc.) and keypad input (up, down, number input), and is able to launch content.
For example, a Casting Video Player can be a smart TV device, a TV Set Top Box, or a content streaming device that provides input to another device like a TV or computer monitor.

#### Speaker

This feature controls the speaker volume of the device.
To control unmute/mute, the On/Off cluster SHALL be used. A value of TRUE for the OnOff attribute SHALL represent the volume on (not muted) state, while a value of FALSE SHALL represent the vol­ume off (muted) state. For volume level control, the Level cluster SHALL be used.
A dedicated endpoint is needed because the On/Off cluster can also be used for other purposes, such as for power control.

#### Content App

A Content App is usually an application built by a Content Provider. A Casting Video Player with a Content App Platform is able to launch Content Apps and represent these apps as separate end­ points.

#### Casting Video Client

A Casting Video Client is a client that can launch content on a Casting Video Player, for example, a Smart Speaker or a Content Provider phone app.

#### Video Remote Control

A Video Remote Control is a client that can control a Video Player, for example, a traditional universal remote control.

### Robotic Devices

#### Robotic Vacuum Cleaner

A robotic vacuum cleaner is a device capable of autonomous cleaning, the cleaning mode may be selected from a number of predefined options and the device should report back any error states.

### Appliances

#### Refrigerator

A refrigerator represents a device that contains one or more cabinets that are capable of chilling or freezing food. Examples of consumer products that MAY make use of this device type include refrigerators, freezers, and wine coolers.

#### Temperature Controlled Cabinet

A Temperature Controlled Cabinet only exists composed as part of another device type. It represents a single cabinet chilling or freezing food in a refrigerator, freezer, wine chiller or other similar device.

#### Room Air Conditioner

A Room Air Conditioner is a device with the primary function of controlling the air temperature in a single room.

#### Laundry Washer

A Laundry Washer represents a device that is capable of laundering consumer items. Any laundry washer product may utilize this device type.

#### Dishwasher

A dishwasher is a device that is generally installed in residential homes and is capable of washing dishes, cutlery, and other items associate with food preparation and consumption. The device can be permanently installed or portable and can have variety of filling and draining methods.

#### Laundry Dryer

A Laundry Dryer represents a device that is capable of drying laundry items.

#### Cook Surface

A Cook Surface device type represents a heating object on a cooktop or other similar device. It SHALL only be used when composed as part of another device type.

#### Cooktop

A cooktop is a cooking surface that heats food either by transferring currents from an electromagnetic field located below the glass surface directly to the magnetic induction cookware placed above or through traditional gas or electric burners.

#### Oven

An oven represents a device that contains one or more cabinets, and optionally a single cooktop, that are all capable of heating food. Examples of consumer products implementing this device type include ovens, wall ovens, convection ovens, etc.

#### Extractor Hood

An Extractor Hood is a device that is generally installed above a cooking surface in residential kitchens. An Extractor Hood’s primary purpose is to reduce odors that arise during the cooking process by either extracting the air above the cooking surface or by recirculating and filtering it. It may also contain a light for illuminating the cooking surface.

#### Microwave Oven

 A Microwave Oven is a device with the primary function of heating foods and beverages using a magnetron. A Microwave Oven is a device which at a minimum is capable of being started and stopped and of setting a power level.

### Energy Devices

#### Battery Storage

A Battery Storage device is a device that allows a DC battery, which can
optionally be comprised of a set parallel strings of battery packs and
associated controller, and an AC inverter, to be monitored and controlled by an
Energy Management System in order to manage the peaks and troughs of supply and
demand, and/or to optimize cost of the energy consumed in premises. It is not
intended to be used for a UPS directly supplying a set of appliances, nor for
portable battery storage devices.

#### EVSE

An EVSE (Electric Vehicle Supply Equipment) is a device that allows an EV
(Electric Vehicle) to be connected to the mains electricity supply to allow it
to be charged (or discharged in case of Vehicle to Grid / Vehicle to Home
applications).

#### Solar Power

A Solar Power device is a device that allows a solar panel array, which can
optionally be comprised of a set parallel strings of solar panels, and its
associated controller and, if appropriate, inverter, to be monitored and
controlled by an Energy Management System.


