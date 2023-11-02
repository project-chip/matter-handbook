+++
title = "Discovery"
chapter = false
weight = 41
+++

## Commissionable discovery

Commissionable discovery happens before Commissioning and refers to the process of discovering and identifying a commissionable Node. There are three methods through which a commissionable Node may advertise itself:

- Bluetooth low energy (BLE)
- Wi-Fi Soft AP
- DNS-SD on an IP network, also known as an existing IP-bearing network

In either method, the commissionable node advertises information as shown in the table below.

| Field         | Length   | Required |
|---------------|----------|----------|
| Discriminator | 12 bit   | Yes      |
| Vendor ID     | 16 bit   | No       |
| Product ID    | 16 bit   | No       |
| Extended data | variable | No       |

As per the Matter specification, Vendor ID and Product ID are not required but can be included. The Discriminator is mandatory and is crucial during the commissioning process to provision the correct device, in case multiple identical devices are connected at the same time. Extended data may be used to encode custom vendor-specific information.

Many devices will advertise for a short period of time (~3-15 mins) after power-up. Other devices must not start advertising either because their primary control does not originate from the fabric or because automatic unprovisioned advertising of devices such as locks isn't safe. This table summarizes the behavior.

| Primary Device Function                                                                      | Automatic Announcement |
|----------------------------------------------------------------------------------------------|------------------------|
| Locks and barriers access devices                                                            | No                     |
| Most control originates from fabric. For example, switch or light bulb.                      | Yes                    |
| Most control does not originate from fabric. For example, dishwasher or refrigerator.        | No                     |

### Bluetooth Low Energy
In this mode of advertisement, the Commissioner will see BLE advertisements. The Commissionee must implement a Generic access profile (GAP) peripheral interface and advertise its uncommissioned state periodically. For the first 30 seconds after a device is turned on the advertisement frequency must be high, at 20 to 60 milliseconds intervals.

After 30 seconds, the device must advertise at a low frequency, at 150 to 1500 millisecond intervals. When commissioned to its first fabric, the device must stop its BLE advertisement.

The Commissioner does not need to issue scan requests. It should do a passive scan on the three BLE advertising channels: 37 (2402 MHz), 38 (2426 MHz) and 39 (2480 MHz). These channels are picked from regions in the spectrum with minimal overlap with Wi-Fi Channels, minimizing interference cross-radio interference.

BLE is not used for operational discovery.

### Wi-Fi Soft AP
When using Wi-Fi Soft AP, the Commissionee will be discovered through an ad-hoc soft access point (soft AP) network. The network's SSID (network name) is in the form MATTER-ddd-vvvv-pppp, where:

ddd is the 12-bit discriminator in HEX.
vvvv is the 16-bit Vendor ID in HEX.
pppp is the 16-bit Product ID in HEX.
Whenever the Commissioner connects to the Commissionee, both will configure unique IPv6 link-local addresses, enabling connection at the Wi-Fi layer. At this point the discovery continues as in the same case of the DNS-SD method covered in the next section.

Moreover, a Wi-Fi Soft AP may implement DHCP for IPv4 and Information Element (IE) to expose Vendor-specific additional information. IE is a variable length field within the 802.11 (Wi-Fi) management frames that allows custom information to be carried to other systems.

Wi-Fi channels 1, 6 and 11 should be favored during Commissioner scanning, but all channels allowed by local spectrum regulation must be scanned.

Wi-Fi Soft AP is not used for operational discovery.

Note: Wi-Fi Soft AP is not implemented in version 1.0 of the Matter SDK, so no devices are currently using this method of advertisement.


### DNS-SD

In this case the Commissionee will be discovered by its domain name service - service discovery (DNS-SD) advertisements that contain information on services rendered by the nodes. See RFC 6762 for more information about DNS-SD. This is a common method of device discovery when:

The Commissionee is connected to Ethernet and thus has physical access to an unencrypted network medium.
The Commissionee has joined the Wi-Fi or Thread network by any out-of-band means.
The Commissionee was already commissioned to another fabric and has joined the Wi-Fi/Thread network. In this case the Commissionee can't use BLE advertisements or create a Soft AP. Thus all secondary fabrics are provisioned through this method.
Thread devices don't directly use DNS-SD, but instead use a proxied method provided by the Thread Border Router. This method is defined by the DNS-SD Service Registration Protocol and its Advertising Proxy. Thread devices register themselves in the SRP service typically provided by a Thread Border Router. This service handles mDNS traffic on behalf of each registered Thread node without burdening the Thread network with additional traffic generated by these protocols.

The DNS-SD instance name for device discovery is _matterc._udp and the host names are built by either a 48-bit MAC address or a 64-bit MAC Extended Address, expressed as a hex string such as A5F15790B0D15F32.local.. Generally this record is only advertised when the Commissionee may be commissioned. However, it may also continue advertising when not in commissioning mode. That behavior is named extended discovery.

After discovery, IPv6 addresses are returned in the AAAA records and key/value pairs are returned in the DNS‑SD TXT record. The key/value pair contains information such as the Discriminator, Vendor ID, and Product ID. The node also advertises commissioning subtypes, which enables filtering of results to find only Commissionees that match a particular attribute.

## Operational discovery
Operational discovery is the process of discovering and identifying a commissioned node. Operational discovery only happens through the IP-based DNS-SD method. The node instance name will be composed of the 64 bit compressed Fabric ID and 64 bit Node ID. These IDs in hexadecimal are then concatenated with a hyphen, such as in 2906C908D115D362-8FC7772401CD0696.local.. Operational discovery shares the same target host name as DNS-SD Device Discovery.

The DNS-SD service type is `_matter._tcp.` Although `_tcp` naming is used, the device might use other transports such as UDP.

_This content was originally published on the [Google Developer Site](https://developers.home.google.com/matter/primer)_