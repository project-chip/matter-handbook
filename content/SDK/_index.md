+++
title = "SDK"
chapter = true
weight = 4
pre = "<b>4. </b>"
+++


# The Matter SDK

The Matter Software Development Kit is a collection of tools to facilitate building  Matter devices and control applications.
The SDK comprises of several different components to guide the development process.

### ZAP
The ZAP tool is a GUI tool that is used to generate a .zap file which describes the endpoint composition of your device, and the clusters that are on it along with their attributes, commands, features, etc.
This .zap file is used by the ZAP compiler along with the cluster definitions from the SDK to generate an Ember layer. This happens automatically as part of the build process, and the Ember layer is compiled into the firmware. 

The tool produces .matter files which are a human-readable version of the .zap that can be used for review.

### Ember
The Ember layer is a generated layer that implements the composition of ONE SPECIFIC device. It looks at each message and determines if the device has implemented the selected attribute or command on the cluster on the selected endpoint, and then blocks or routes accordingly, based on the implementation and the access control. Valid requests are forwarded on to the cluster implementations to handle and invalid requests get sent back with an error. Ember layer is the piece that makes your device your device. Most are generated statically using zap.

### Chef 
Chef is a tool to help generate sample device type zap configuration files which can be further customised with the ZAP tool.

### Core
The Core src folder contains the underlying Matter interoperability layers that provide essential functionality. These are used by the build process.

### CHIP Tool
CHIP Tool is our example controller app, used for development and testing of your Matter device.

### GN/Ninja
GN is part of the build system which was originally developed for the Chromium browser project, it is used to configure the build of a Matter device.
Ninja is the component which builds the device image.

### Platform Layer
The platform layer contains device specific delegate implementations for most of the common architectures on which Matter is deployed.

### Abstraction Layers
The SDK contains absctraction layters for Python, Java and Kotlin controllers.


The SDK is publically avalible on [GitHub](https://github.com/project-chip/connectedhomeip)