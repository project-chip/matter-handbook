+++
title = "Distributed Compliance Ledger (DCL)"

chapter = false
weight = 10
+++


## Table of Contents
- [DCL Introduction](#dcl-introduction)
  - [Types of nodes that operate in the DCL](#types-of-nodes-that-operate-in-the-dcl)
  - [Types of account roles that can interact with the DCL](#types-of-account-roles-that-can-interact-with-the-dcl)
  - [Main-Net and Test-Net?](#main-net-and-test-net)
  - [Access and Interaction with the DCL](#access-and-interaction-with-the-dcl)
  - [Getting an account for writing to the DCL](#getting-an-account-for-writing-to-the-dcl)
  - [Interacting with the DCL](#interacting-with-the-dcl)
    - [Web User Interface](#web-user-interface)
    - [Command Line Interface](#command-line-interface)
  - [Observer Nodes](#observer-nodes)
    - [Main-Net public ONs](#main-net-public-ons)
    - [Test-Net public ONs](#test-net-public-ons)
- [FAQs](#faqs)
  - [Why is my Vendor information not listed in the DCL?](#why-is-my-vendor-information-not-listed-in-the-dcl)
  - [When should I write my product information to the Main-Net DCL?](#when-should-i-write-my-product-information-to-the-main-net-dcl)
- [Contact](#contact)

## DCL Introduction
The DCL is a blockchain-based system owned and hosted by Alliance members. It is used by the Matter protocol for storing information such as:

| Information          | Description                                               | Account Role involved                                                    |
| -------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------ |
| Vendor               | The manufacturer or vendor of a device. | Data is entered by an approved Vendor account.                                             |
| Product              | The product device including description, software version, OTA information, etc. | Data is entered by an approved Vendor account.   |
| Compliance status    | The certification status including certification ID, certification date, etc. | Data is entered by the Alliance's Certification Center account.|
| PAA Root CAs         | Product Attestation Authorities (PAA) Root CAs used by commissioners during Device Attestation process. | Data is proposed by the Alliance's Trustee and approved by other DCL Trustees.|

Additional information available in the [Distributed Compliance Ledger (DCL) Policies, Procedure and Governance](https://groups.csa-iot.org/wg/members-all/document/26075).

### Types of nodes that operate in the DCL

| Type of Node         | Description                                                                                                                                          |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Validator Node (VN)  | Participates in creating the consensus process to add information into the ledger. The consensus is the process by which the nodes agree on the state and data of the blockchain; ensuring all nodes have a consistent ledger, while verifying the validity of transactions.                                                                                                                                       |
| Sentry Node (SN)     | Doesn\'t participate in consensus and wraps the VN representing it for the rest of the network as one of the ways for DDoS and access protection.    |
| Observer Node (ON)   | Doesn\'t participate in consensus and is optimized for public data read and authenticated write interactions with the ledger.                        |

### Types of account roles that can interact with the DCL

| Account Role         | Description                                                                                                                                       |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Trustee              | Entrusted to approve or deny other DCL roles and PAA Root CAs in the ledger, as well as to disable Validator Nodes.                               |
| Node Admin           | Can instantiate a single Validator Node.                                                                                                          |
| Vendor               | Can write vendor and product information to the ledger. Alliance members can have one or more vendor accounts.                                    |
| Vendor Admin         | Can add and update the Vendor information table of the ledger.                                                                                    |
| Certification Center | Can submit, update, delete or revoke certification status of a product based on the Certification application in the Certification Tool.          |

### Main-Net and Test-Net

| DCL Deployment       | Description                                                                                                                                                |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Main-Net             |  The production environment that is utilized by the public. Transactions on the Main-Net involve real products and data.          |
| Test-Net             |  Used for testing and development purposes. It provides a safe environment for experimentation and troubleshooting before deploying to the Main-Net. |

### Access and interaction with the DCL

-   **Write** access to the ledger is restricted to approved accounts in the DCL.

-   **Read** access is broadly available through observer nodes.

### Getting an account for writing to the DCL

-   Enrollment for Main-Net DCL accounts is managed through the "DCL Account(s)" section in the Certification Tool system (Knack). You can request access to the Certification Tool 
    by sending an email to <help@csa-iot.org>.

> Note: The Certification Tool portal will depend on the Membership type.

-   Enrollment for Test-Net DCL accounts can be requested by sending an email to <dcl-admin@csa-iot.org>

Review the following document for instructions: [HowTo - Writing to the DCL.pdf](https://groups.csa-iot.org/wg/members-all/document/27881)

### Interacting with the DCL

There are different options available for users and/or systems to interact with the DCL:

-   Web User Interface, for intuitive navigation.
-   API, for seamless integration.
-   Command Line Interface (CLI), for efficient management.

#### Web User Interface
The Web UI allows users to interact with the DCL through a visual interface, making tasks more intuitive and reducing the likelihood of errors. There is no need to install any application client or configuration setup.

#### Command Line Interface

The DCL CLI software (`dcld`) allows users to interact with the DCL via command line using a connection to a specific available Observer Node. The CLI software is available at the following link: 
<https://github.com/zigbee-alliance/distributed-compliance-ledger/releases>.

The instructions for the DCL client are available at the following link: <https://github.com/zigbee-alliance/distributed-compliance-ledger/blob/master/docs/how-to.md>.

### Observer Nodes

An Observer Node (ON) offers APIs or Web User Interfaces for users or systems to interact with the DCL. This facilitates both manual and automated authorized writes, as well as 
public queries to the DCL.

It is not a requirement to deploy an Observer Node. The Alliance has ONs available in various regions across the globe, including trusted ONs managed by our members. This ensures 
broad accessibility and reliable interaction with the DCL from different locations.

#### Main-Net public ONs

| Host Owner       | Region       | Web User Interface                 | URL for API                 | REST    | RPC     | gRPC    |
| ---------------- | ------------ | ---------------------------------- | --------------------------- | ------- | ------- | ------- |
| The Alliance     | US, EU       | <https://webui.dcl.csa-iot.org>    | on.dcl.csa-iot.org          | 443     | 26657   | 8443    |
| TrustAsia        | CN           | <https://main-net.trustasia.com>   | on.main-net.trustasia.com   | 443     | 26657   | 8443    |
| Tuya             | CN           | N/A                                | on-dcl.tuyacn.com           | 1317    | 26657   | 9090    |

#### Test-Net public ONs

| Host Owner       | Region       | Web User Interface                 | URL for API                 | REST    | RPC     | gRPC    |
| ---------------- | ------------ | ---------------------------------- | --------------------------- | ------- | ------- | ------- |
| The Alliance     | US, EU       | <https://testnet.iotledger.io>     | on.test-net.dcl.csa-iot.org |  443    | 26657   | 8443    |
| TrustAsia        | CN           | <https://test-net.trustasia.com>   | on.test-net.trustasia.com   |  443    | 26657   | 8443    |
| Tuya             | CN           | N/A                                | on-dcl-testnet.tuyacn.com   | 1317    | 26657   | 9090    |

## FAQs

### Why is my Vendor information not listed in the DCL?

Each member must add their own Vendor information using an approved Vendor account.

Review the following document for instructions: [HowTo - Writing to the DCL.pdf](https://groups.csa-iot.org/wg/members-all/document/27881)

### When should I write my product information to the Main-Net DCL?

The DCL\'s product information comprises a Model and a Model-Version of the product. Members add this information using an approved Vendor account. This can be done before or after 
completing the certification process. The Compliance entry in the DCL is submitted by the Alliance's Certification team after the certification process is finalized. For this to 
take place, the Model and Model-Version must already be listed in the DCL, match the data from the Certification Tool, and the member must notify the Certification team that the 
DCL information is ready.

Review the following document for instructions: [HowTo - Writing to the DCL.pdf](https://groups.csa-iot.org/wg/members-all/document/27881)

## Contact 
For any questions related to the DCL, please contact the DCL Admin (<dcl-admin@csa-iot.org>).
