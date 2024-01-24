+++
title = "The Device Data Model"
chapter = false
weight = 20
+++


Devices in Matter have a well-defined data model (DM), which is a hierarchical modeling of a Device's features. At the top level of this hierarchy there is a Device.

## Devices and Endpoints

All Devices, including smartphones and home assistants, are composed of Nodes1. A Node is a unique identifiable and addressable resource in a network that a user can perceive as functionally whole. Network communication in Matter originates and terminates at a Node.

Nodes are a collection of Endpoints. Each Endpoint encloses a feature set. For instance, an Endpoint might relate to a lighting functionality, while another relates to motion detection, and another deals with utilities such as Device OTA.

![Devices Nodes and Endpoints](/primer-device-node.png)

## Node Roles

A Node role is a set of related behaviors. Each Node may have one or more roles. Node roles include:

- Commissioner: A Node that performs Commissioning.
- Controller: A Node that can control one or more Nodes. Examples include the Google Home app (GHA), Google Assistant, and the Google Nest Hub (2nd gen). Some device types, such as the On/Off Light Switch, have the Controller role.
- Controlee: A Node that can be controlled by one or more Nodes. Most device types can be a - - Controlee, except for some device types which have the Controller role, such as the On/Off Light Switch. The On/Off Light Switch can only be a Controller. It cannot be a Controlee.
- OTA Provider: A Node that can provide OTA software updates.
- OTA Requestor: A Node that can request OTA software updates.

## Clusters

Within an Endpoint a Node has one or more Clusters. These are another step in the Device hierarchy, as they group specific functionality such as a on/off cluster on a smart plug, or a level control cluster on a dimmable light Endpoint.

A Node may also have several Endpoints, each creating an instance of the same functionality. For example, a light fixture may expose independent control of individual lights or a power strip may expose control of individual sockets.

### Attributes
At the last level we'll find Attributes, which are states held by the node, such as the current level attribute of a level control cluster. Attributes may be defined as different data types such as uint8, strings or arrays.

![Nodes, Endpoints, Attributes and Commands](../..//primer-node-endpoint-attribute.png)

### Commands
Besides Attributes, Clusters also have Commands, which are actions that may be performed. They are the equivalent in Matter's DM of a remote procedure call. Commands are verb-like, such as lock door on a Door Lock cluster. Commands may generate responses and results; in Matter, such responses are also defined as Commands, going in the reverse direction.

### Events
Lastly, Clusters may also have Events, which can be thought of as a record of past state transitions. While Attributes represent the current states, events are a journal of the past, and include a monotonically increasing counter, a timestamp and a priority. They enable capturing state transitions, as well as data modeling that is not readily achieved with attributes.

![A sample of the hierarchy of Matter Devices interaction model](../../primer-device-type.png)

The Endpoint 0 is reserved for the Utility Clusters. Utility Clusters are specific Clusters that enclose servicing functionality on an Endpoint, such as discovery, addressing, diagnostics and software update. On the other hand, the Application Clusters support primary actions such as on/off or temperature measurement.

## Device Types

Altogether, which Cluster combinations should be included as a device manufacturer plans a new Device?

The Matter specification requires that the device implement or extend one or more Device Types. A Device Type is a collection of mandatory and optional Clusters that define the top-level attributes of a physical Device, such as Dimmable Light, Door Lock, or Video Player.

The Device Types are not specified by the Matter specification main document, but by an accompanying document: the Device Library. Similarly, all Application Clusters are defined in the Application Cluster Library. These three documents can be found on the [Connectivity Standards Alliance (Alliance) website](https://csa-iot.org/developer-resource/specifications-download-request/).

Each Endpoint implementing a Device Type must implement the mandatory Clusters that define that Device Type. In addition to the mandatory Clusters, the Endpoint may implement additional Clusters, including one or more of the Device Type's optional Clusters, or even Clusters that aren't part of the Device Type.

## Clients and Servers

Clusters might be either a Client Cluster or a Server Cluster. While a Server is stateful and holds Attributes, Events and Commands, a Client is stateless and its responsibility is to initiate Interactions with a remote Server Cluster, thus performing:

- reads from and writes to its remote Attributes.
- reads of its remote Events.
- invocation of its remote Commands.

While the DM is hierarchical within a Node, the relationship between Nodes is not. Nodes in Matter do not have vertical controller/peripheral or leader/follower relationships. On the contrary, the relationship is horizontal: Any Cluster may be either Server or Client. Thus a Node may be both Server and Client with regards to different Clusters and functionalities.

For instance, we may have two table lamps: Node A and Node B. Both nodes implement an On/Off Light Device Type. This Device Type includes an On/Off Server Cluster that controls their respective physical light outputs.

But, as typical table lamps do, our physical devices will also include an On/Off Light Switch Device Type for their local on/off switches. This Device Type must implement an On/Off Client Cluster so it may control the Server Clusters.

![Client and Server Clusters](../..//primer-client-server.png)

In this sample, the On/Off Client Cluster on Node A is changing the attributes of the On/Off Server Cluster on Node A and Node B, while the Node B's Client Cluster is only changing the Server Cluster on Node B itself.

In the next section we'll detail how Client and Server Clusters interact: the Interaction Model.

## Descriptor Cluster
As the name implies, the Descriptor Cluster Server provides introspection information. It describes the Endpoint enumerating its:

- Server Clusters.
- Client Clusters.
- Device Types.
- Additional Endpoints, known as Parts.
Every Device Type requires the implementation of Descriptor Clusters. The Root Device Type is defined on Endpoint 0. Reading its Descriptor Cluster will provide the client the visibility to traverse the full tree of available Endpoints and perform applicable operations.

The Commissioner or Controlling device such as a phone or hub can use the information found on the Descriptor Cluster to model the Device (light, switch, pump, thermostat), and specific features implemented by that particular instance of the Device, showing the correct UI to the user.

### Server Clusters
The `ServerList` Attribute lists the Cluster Servers in the Endpoint.
### Client Clusters
The `ClientList` Attribute lists the Cluster Clients in the Endpoint.
### Device Type List
The `DeviceTypeList` Attribute is a list of Device Types supported by the Endpoint, along with its respective revisions. It must contain at least one Device Type.
### Parts List
The `PartsList` contains the list of Endpoints used for implementing this Device Type.

The `PartsList` of Endpoint 0 (Root Node) contains all the Endpoints of the device apart from itself (Endpoint 0).

The `PartsList` of other Endpoints will usually be empty. For example, a Temperature Sensor mandates a Temperature Measurement Server Cluster and nothing else.

Other device types might be composed in a tree structure of more than one Device Type instance. For example, a Video Player Device type can be composed of TV, Video Player, Speaker and different Content App Device Types, each on a different Endpoint.

[^1]: The Matter specification determines that a Device may have multiple Nodes. For example, smartphones may have multiple apps, each app being a different Node. For the purposes of this primer, all Devices will contain a single Node. It's expected that most physical devices will follow this pattern. 

_This content was originally published on the [Google Developer Site](https://developers.home.google.com/matter/primer)_