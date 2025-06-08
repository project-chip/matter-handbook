+++
title = "Glossary"
chapter = true
weight = 7
pre = "<b>7. </b>"
+++

# Glossary & Acronym Decoder

| Term     | Definition                                                                                                                                                                |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ACL      | Access Control List. This is a list of entries in the Access Control cluster that grant access privileges to device and groups                                            |
| adoc     | The filename suffix for asciidoc, which is the markup language we use to write the specification and test plans. [asciidoc](https://asciidoc.org/)                        |
| Alliance | Refers to the Connectivity Standards Alliance (CSA)                                                                                                                       |
| asciidoc | Markup language we use to write the specification and test plans. [asciidoc](https://asciidoc.org/)                                                                       |
| AoE      | Anywhere on Earth. This acronym is commonly used when discussing deadlines to clarify the exact end time.
| ATL      | Authorized Test Laboratory. ATLs run the tests required to certify devices.
| BLE      | Bluetooth Low Energy. BLE is used in many Matter devices for commissioning.
| BOM      | Bill of Materials. This term is generally used to refer to the total cost to manufacture one unit of a product.
| BR       | Border Router. This type of router connects two communication protocols. Matter uses both Thread and Wi-Fi as operational transports, and therefore a Thread border router (TBR) is required to route packets between the Thread and Wi-Fi networks.|
| CA       | Certificate Authority. These entities store, sign and issue digital certificates. In Matter, the Device attestation certificate chain is backed by a Product Attestation Authority certificate that is issues by a manufacturer CA or the CA of a certificate provider (also called a Public Key Infrastructure (PKI) provider). The Node Operational Certificate (NOC) chains are backed by a Trusted Root Certificate that chains to a CA managed by the Fabric administrator. |
| Causeway | Site used to store documents and calendars and track group memberships etc. [https://groups.csa-iot.org/](https://groups.csa-iot.org/)                                    |
| CASE     | Certificate Authenticated Session Establishment. This is the session establishment mechanism used during normal Matter operations                                         |
| CCB      | Change Control Board. In the CSA, CCB is also used as a short-form to refer to issues raised in the CCB system. CCB issues may be raised by members to report issues in either the specification or the test plan. These are most commonly raised for test issues found at certification. The certification section has more information about the [CCB process](../Certification/certifying-a-product/self-pre-test#fixing-bugs). |
| CD       | Certification Declaration - this declaration is provided by devices to prove they have passed certification                                                               |
| CHIP     | Matter used to be called Project CHIP (Connected Home over IP) before it got its current name. Much of the SDK still uses that prefix.                                            |
| CI       | Continuous Integration. This is normally used to refer to the tests performed before pull requests can be merged into any of the Matter-owned repositories.               |
| CLI      | Command line interface.                                                                                                                                                   |
| commissioning | This is the process by which Matter devices are attested, issued operational certificates and credentials for the operational network. More information about the commissioning process can be found in the [Commissioning guide](../HowItWorks/Commisioning/). |
| CRL      | Certificate revocation list. This is a list of certificates that were previously issued by a CA, but that have since been revoked.                                        |
| CSA      | Connectivity Standards Alliance - the member-driven organization that manages the Matter standard                                                                                                   |
| CSG      | Certification Sub Group [CSG](https://groups.csa-iot.org/wg/matter-csg/workgroup)                                                                                          |
| CSR      | Certificate signing request. CSRs are using during the commissioning process to issue operational cetificates for a node. For more information on the operational certificate signing process, please see the [Commissioning](../HowItWorks/Commisioning) section of the handbook.
| CTP      | Certification transfer program. This program is used to allow companies to white-label devices that were previously certified by another member company. More information on the [Certification Transfer Program](https://csa-iot.org/certification/transfer-program/) can be found on the CSA website.
| DAC      | Device Attestation Certificates. See [Attestation](https://handbook.buildwithmatter.com/howitworks/attestation/)                                                          |
| DCL      | Distributed compliance ledger. This system is used to distribute additional information about Matter products. Please see the [DCL guide](../Guides/DistributedComplianceLedger/) for more information.|
| DM       | Data Model. The data model describes the organization of data within a cluster. DM is sometimes also used to refer to the DMTT.                                           |
| DMTT     | Data Model Tiger Team.                                                                                                                                                    |
| DNS-SD   | Domain name service (DNS) service discovery. This is the mechanism used to locate Matter devices on the IP network                                                        |
| DRLC     | Demand Response Load Control                                                                                                                                              |
| EP       | This is a shorthand notation used in some documents to refer to an endpoint on a Matter node. The [Data model](../HowItWorks/DataModel) section has information on Matter nodes and endpoints.
| EVSE     | Electric Vehicle Supply Equipment                                                                                                                                         |
| FastTrack| Matter FastTrack Recertification is a program designed to streamline the recertification process for Matter-certified products. You can find more information about this at the [Matter FastTrack Recertification FAQ](../Certification/MatterFastTrackRecertificationFAQ).|
| FRP      | FastTrack Recertification program. See FastTrack.                                                                                                                         |
| HVAC     | Heating, Ventilation, and Air Conditioning. In the context of Matter, HVAC refers to the category of smart home devices that control environmental conditions within a building.|
| HRAP     | Home Routers and Access Points. This is the tiger team working on Matter support for networking equipment.|
| IDM      | Interaction and Data Model. This term is used within the context of the test plans to refer to tests that are testing the underlying interaction model layers and the conformance of the data model elements to the specification.
| IM       | Interaction Model. The [Interaction Model](../HowItWorks/InteractionModel/) section has more information on this layer.
| ICAC     | Intermediate Certificate Authority Certificate See [Operational Credentials](https://handbook.buildwithmatter.com/howitworks/fabric/)                                     |
| ICD      | Intermittently Connected Devices. These device can sleep for relatively long periods and will be unreachable over Matter during these times.                              |
| MCORE    | MOCRE PICS codes describe device elements that are not directly tied to data model elements. For example, TCP support.|
| mDNS     | Multicast DNS - the mechanism used to perform DNS-SD over Wi-Fi                                                                                                           |
| MPSG     | Marketing and Product Sub Group [MPSG](https://groups.csa-iot.org/wg/matter-mpsg/workgroup)                                                                                |
| MRD      | Market Requirements Document. Large new features are required to have an MRD approved by the MPSG.|
| MRP      | Message Reliability Protocol. The Matter specification uses MRP to provide reliable communication over UDP. MRP includes protocols for message acknowledgements, retransmissions and duplicate message detection.|
| MTU      | Maximum Transmission Unit. MTU refers to the largest size of a packet (Protocol Data Unit) that can be transmitted over a network without being fragmented.
| NFR      | New Feature Request. A new feature request is submitted to the MPSG by a team looking to implement a new feature. These are used for medium-sized features that the MPSG determines does not require a full marketing requirements document (MRD), but is too large for a technical change request (TCR).|
| NOC      | Node Operational Certificate. See [Commissioning](../HowItWorks/Attestation/)|
| NOCSR    | Node Operational Certificate Signing Request. See [Commissioning](../HowItWorks/Commisioning)|
| NOKP     | Node Operational Key Pair. This is the key pair generated on the device as part of the operational certificate signing process. See [Commissioning](../HowItWorks/Commisioning)|
| OpenThread | [OpenThread](http://openthread.io/) is an implementation of the thread protocol.|
| OTA      | Over The Air. This acronym normally refers to software updates delivered to deployed devices.|
| PAA      | Product Attestation Authority. Root certificate for device attestation. See [Attestation](https://handbook.buildwithmatter.com/howitworks/attestation/)                   |
| PAI      | Product attestation intermediate - Intermediate certificate for device attestation. See [Attestation](https://handbook.buildwithmatter.com/howitworks/attestation/)       |
| PAKE     | Password-Authenticated Key Exchange. PAKE is the cryptographic protocol used for key exchange for password-authenticated session establishment (PASE) for commissioning. Matter uses the SPAKE2+ key exchange protocol.|
| PASE     | Password Authenticated Session Establishment. This is the session establishment mechanism used to commission devices.                                                     |
| PHY      | PHY refers to the Physical Layer. The PHY is the lowest layer of the network stack, responsible for the actual transmission and reception of raw data bits over a physical medium. |
| PICS     | Protocol Implementation Conformance Statement. PICS are also used to determine testing requirements for certification                                                     |
| PID      | Product identifier. Product identifiers are allocated by the manufacturer and used to identify individual Matter-enabled proucts.                                         |
| PIXIT    | Protocol Implementation eXtra Information for Testing. These are configuration values provided to certification tests.                                                    |
| PKI      | Public key infrastructure. For Matter, PKI is used for provisioning operational certificates and attesting devices. A "PKI provider" is a company that can provide Matter device attestation certificates for companies that do not run their own certificate authorities.|
| PR       | Pull Request. This is the mechanism used to contribute to the Matter-owned repositories. Information on [GitHub pull requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) can be found on the GitHub site.|
| RCAC     | Root Certificate Authority Certificate. See [Operational Credentials](https://handbook.buildwithmatter.com/howitworks/fabric/)                                            |
| SDK      | Software development kit - a software package implementing the specification [github] (https://github.com/project-chip/connectedhomeip)                                   |
| SKID     | Subject Key Identifier. This information is used to identify certificates.|
| spec     | Short for specification. [github] (https://github.com/CHIP-Specifications/connectedhomeip-spec)                                                                           |
| SRP      | Service Registration Protocol. This is the mechanism used to register thread devices for DNS-SD. Border routers implement this protocol to allow Thread device discovery. |
| SVE      | Specification Validation Event - this follows the test events and acts as the final check on the certification package for a release.                                     |
| SWTT     | [Software development tiger team](https://groups.csa-iot.org/wg/matter-tsg-swd/workgroup). This is the group of people working on the SDK.                                |
| TCOC     | Testing and Certification Oversight Committee. This is a CSA board-level committee that is responsible for overseeing the certification programs of all the Alliance working groups.|
| TCP      | Transmission Control Protocol. TCP is a reliable, connection-oriented network transmission protocol. TCP is a recent addition to the Matter specification, used primarily by the camera stack to transmit large messages that do not fit into a MTU.|
| TCR      | Technical Change Request. A technical change request is used for small changes to existing specification element. These are intended to be a lightweight process for small improvements.|
| TE       | Test Event. These events are held during development to verify that test scripts and SDK development are on track.                                                         |
| TLS      | Transport Layer Security. TLS is a cryptographic protocol used for secure communication over a network. TLS is used by camera device types.|
| TLV      | Tag-Length-Value. The Matter encoding specification uses a TLV encoding for transmission of data.|
| TSG      | Technical Sub Group [TSG](https://groups.csa-iot.org/wg/matter-tsg/workgroup)                                                                                              |
| TT       | Tiger team - a small group focused on one activity or feature.                                                                                                            |
| UDP      | User Datagram Protocol. UDP is a connectionless network transmission protocol. UDP is used for most Matter communication using MRP for reliability. |
| VID      | Vendor identifier. VIDs are allocated by the CSA (see [Membership](../Certification/certifying-a-product/membership/))|
| WG       | Work Group. [Matter](https://groups.csa-iot.org/wg/matter-wg/workgroup) is a working group in the CSA.                                                                 |
| YAML     | YAML Ain't Markup Language. This is a key-value format used primarily for things like configuration files. In Matter, some certification tests are written in YAML. Information about Matter certification YAML can be found in the [YAML testing guide](https://project-chip.github.io/connectedhomeip-doc/testing/yaml.html).
