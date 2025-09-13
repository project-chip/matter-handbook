---
label: What is Matter
order: 200
---
Matter has the goal of being an interoperable standard that fosters technology adoption and innovation, gradually replacing proprietary protocols for smart home ecosystems.

Matter is implemented by an open source SDK that contains not only the implementation of the specification but also a rich set of examples and interoperable code. The core Matter protocol fits on the top three layers in the context of OSI, meaning it can run over any type of IPv6 transport and network. While control and other operational communication are performed over IPv6, Bluetooth Low Energy (BLE) may be employed to commission new devices.

![The Matter Network Stack](/static/primer-matter-architecture.png)

Matter is flexible and interoperable. It builds upon years of challenges and successes of low power 802.15.4 networks as well as Wi-Fi smart home devices. Like Thread, Matter builds atop IPv6. It includes strong cryptography, a well-defined modeling of Device Types and their data, and the support for multiple ecosystem administrators.

Matter also supports bridging of other Smart Home technologies such as Zigbee, Bluetooth Mesh and Z-Wave. This means that devices based on these protocols may be operated as if they were Matter devices through a Bridge, which is a member device of both a Matter network and the other, bridged, IoT technologies.

There is a dual advantage to Bridges. The devices that use other protocols gain access to technologies and ecosystems that target native Matter devices. Meanwhile Matter will leverage mature technologies with large installed user bases to create a true web of connected things.

_This content was originally published on the [Google Developer Site](https://developers.home.google.com/matter/primer)_
