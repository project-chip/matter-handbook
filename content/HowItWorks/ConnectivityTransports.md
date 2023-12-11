+++
title = "Connectivity Transports"
chapter = false
weight = 30
+++

In principle, any IPv6-bearing network is suitable for Matter deployment, subject to supporting a few core IPv6 standards. In the current version of the specification, we focus on three link layer technologies: Ethernet, Wi-Fi and Thread. We restrict the specification to the above so that the specification can suitably cover provisioning of these link layers, and so that the amount of testing in certifica­tion is suitably bounded.

Matter treats networks as shared resources: it makes no stipulation of exclusive network owner­ship or access. As a result, it is possible to overlay multiple Matter networks over the same set of constituent IP networks.
This protocol may operate in the absence of globally routable IPv6 infrastructure. This requirement enables operation in a network disconnected or firewalled from the global Internet. It also enables deployment in situations where the Internet Service Provider either does not support IPv6 on con­sumer premises or where the support proves otherwise limiting, for example, if the delegated pre­fix cannot accommodate all the networks and devices on premises.
This protocol supports local communications spanning one or more IPv6 subnets. Canonical net­works supporting a fabric may include a Wi-Fi/Ethernet subnet, or one or more low power and lossy networks (LLN) subnets. In this version of the specification, Thread is the supported LLN standard.
Matter uses IPv6 for its operational communications, and leverages both IPv6 Unicast and Multicast addressing for accessing its Nodes and Groups, respectively.


## Ethernet

This is the simplest transport for Matter, as there is no need to communicated any network credential to the device it is simply connected to the Ethernet network.
Commissioning of devices should use the on-network bitmask in the Discovery Capabilities of the Onboarding Payload and the device will be discovered via DNS-SD.

## Wi-Fi

Matter devices may use the 802.11 (Wi-Fi) standard for connectivity, any of the approved versions of ths spec are compatible with Matter and all the approved frequency bands may be used (subject to local regulatory limits).
In order for a Matter device that uses Wi-Fi to be certified the manufacturer must first obtain Wi-Fi certification for the device from the [WiFi Alliance](https://www.wi-fi.org/certification).
This can often be obtained via the Wi-Fi chipset vendors existing certification.
For commissioning Wi-Fi devices may use the BLE method of discovery and conveying of network credentials or the device may already be connected to the IP network via an existing proprietary method.
The use of Soft-AP mode for Wi-Fi commissioning mode while part of the specification is not yet deployed by any vendor.

## Thread

Thread is a low power 802.15.4 mesh based radio protocol designed for IP transport. There are a number of additional considerations when using Thread for a Matter which are explained on the dedicated Thread page of this site.
In order for a Matter device that uses Thread to be certified the manufacturer must first obtain Thrad certification for the device from the [Thread Group](https://www.threadgroup.org/What-is-Thread/Certification)
Where a device used Thread it must also use BLE for Discovery and Commissioning in order to provision the Thread network credentials to the device.

## Bluetooth

Bluetooth Low Energy (BLE) Is used in Matter as part of the discovery and commissioning stage as a method for passing the credentials of the WiFi or Thread network that the device will use for operational communication. BLE is Required where a device uses Thread and optional for WiFi.
BLE Cannot be used as the sole transport technology for a Matter Device.
