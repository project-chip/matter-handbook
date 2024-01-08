+++
title = "Thread"
chapter = false
weight = 60
+++

## Low Power
Some Matter Nodes are wired and have energy budgets that allow them to keep their radios continuously on. Other types of Nodes such as sensors have requirements to run for years on a battery, operating their radios on low-power networks such as Thread. The proxy architecture, along with Thread Sleepy End Devices, allows full-powered Nodes to provide both network-level and application-level functionality that insulates their child Nodes from energy-intensive transactions.

A fundamental aspect of Matter is that it works both on high-throughput network mediums such as Wi-Fi and Ethernet, but also on low-latency, low-bandwidth, such as Thread. If all Multicast packets from Wi-Fi were bridged into Thread, we'd overburden the network, and potentially flood it. Thread's goal is to enable IPv6 in low-power, low-latency mesh networking, not high-bandwidth data transfer. While Thread's ICMPv6 pings in a local network are typically under few tens of milliseconds RTT, its total bandwidth is limited to 250 kbps at the IEEE 802.15.4 PHY. With packet retransmissions and overhead, the typical max bandwidth is around 125 kbps. In other words, orders of magnitude less than Wi-Fi.

Frames on the IEEE 802.15.4 PHY are 127 bytes, but the largest (and typical) maximum transmission unit (MTU) of IPv6 packets in Thread is 1280 bytes. Thus IPv6 packets often need to be split into several PHY frames. This process is defined by RFC 4944.

To learn more, refer to IPv6 Addressing in the [Thread Primer on openthread.io](https://openthread.io/guides/thread-primer).

## Border Routers
So how can Nodes coexist on both transport mediums while in the same fabric? Although both networks share application-level Matter credentials, they don't share the same link technology. In this scenario, the network needs a Thread Border Router (BR) to enable connectivity. BRs are Stub IPv6 Routers.

Stub Routers enable connectivity between stub networks and regular networks. A Stub Network is a "last-mile" network that provides outer connectivity to its members, but doesn't serve as a transit network path between other networks. Typically, Matter Stub Networks are Thread-based. Refer to RFC draft for further information on stub networks.

BRs therefore have the responsibility of being the link between the Stub Network and the Adjacent Infrastructure Network, which is the local Wi-Fi or Ethernet network. They forward only the packets that are relevant to the Thread network.

This process is accomplished by assigning different IPv6 prefixes to Thread and Adjacent Infrastructure Networks. Thus the BR only forwards unicasts to or from the Thread IPv6 prefix.

Border Routers are also responsible for:

- automatically configuring IPv6 prefixes and routes for both the Thread and Adjacent Infrastructure Networks so that hosts on either side of the Thread Border router can communicate.
- publishing mDNS DNS-SD discovery packets on behalf of Thread Nodes, so they can be discovered on the adjacent infrastructure network.

To learn more, refer to the [Border Router guide on openthread.io](https://openthread.io/guides/border-router).

## IPv6 Multicast
Group messages are also important as they allow simultaneous control of several Matter Nodes through Multicast. In order to route this traffic into the Thread network, both Matter and Thread implement the Unicast Prefix-based IPv6 Multicast Addressing Scheme defined by RFC 3306.

This method allows the selection of the destination Nodes of a Multicast packet based on their shared IPv6 Unicast prefix.

For example, a Matter Multicast address might look like this:
```FF35:0040:FD<Fabric ID>00:<Group ID>```

This Table details how this address is constructed:
|Bits|Description|
|--- |--- |
|12 bits|0xFF3|
|4 bits|0x05 Scope: site-local|
|8 bits|0x00 reserved|
|8 bits|0x40 Indicates a 64-bit long prefix|
|8 bits|0xFD Designates a ULA prefix|
|56 bits|Fabric ID|
|8 bits|0x00|
|16 bits|Group ID|


More information can be found in the [Multicast](https://openthread.io/guides/thread-primer/ipv6-addressing) section of the Thread Primer and on the RFC itself.

When IPv6 Multicast Addresses are formed, they also include the upper 56-bits of the Fabric ID. The important implication is that the scope of Multicast is within a Fabric, while Unicast addresses are shared between Fabrics. Nodes with many fabrics can potentially have several Multicast addresses defining overlapping Node Groups scoped at each fabric.


