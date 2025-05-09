+++
title = "Development"
chapter = false
weight = 6
+++

![](../imgs/development.png)

The process of developing a Matter product is highly dependent on the device
being developed, the platform being used, and the policies of the company doing the development. There
is no single "best" way to integrate Matter into a product. This guide aims to
address the common considerations for Matter product development.

- Information on the Connectivity Standards Alliance (CSA) open source SDK is available at the
[Matter SDK documentation site](https://project-chip.github.io/connectedhomeip-doc/index.html).

- Integration of the SDK on specific platforms is covered by the
[Platform guides](https://project-chip.github.io/connectedhomeip-doc/platforms/index.html).


## Matter-specific product considerations
The documentation in this section aims to give a brief overview of some of the
common product and factory considerations and challenges that may differ from
non-Matter products.

Matter devices require some material to be provisioned at the factory, after
certification. Some of these materials need to be provisioned on a per-device
basis, some are per-product-line.

![](../img/factory_data.png)

Most platforms provide a comprehensive factory data solution customized to
Matter materials. To learn more, see the documentation for your selected
[Platform](https://project-chip.github.io/connectedhomeip-doc/platforms/index.html).

### Device Attestation Certificates and Certification Authorities

Device attestation certificates are used to attest devices (or commissionable apps,
in the case of Matter Casting) as being authentic
devices that are manufactured by the stated vendor and certified as a Matter
device. The full attestation procedure and certificate set is described in the
Handbook's
[Device Attestation](https://handbook.buildwithmatter.com/howitworks/attestation/)
section. The attestation certificate chain matches the Vendor and Product IDs
declared on the device and in the certification declaration.

The device attestation chain consists of the Device Attestation Certificate
(DAC), which is signed by the Product Attestation Intermediate (PAI), which is
signed by the Product Attestation Authority (PAA).

The DAC and PAI are provided by the product being commissioned (device, app, etc), and the PAA is distributed in the
DCL and does not appear on the product.

As a part of the attestation chain, each attesting product needs to be provisioned with:

-   Device attestation private key
    -   Private, stored in the secure subsystem where possible
    -   See Spec section 6.3.2 Firmware information
    -   Covered by the
        [Security Attestation declaration](https://groups.csa-iot.org/wg/members-all/document/27432)
-   Device Attestation Certificate (DAC)
    -   Public
    -   Signed by a PAI
-   Product Attestation Intermediate (PAI)
    -   Public
    -   Signed by a PAA (whose certificate is found in the DCL)

Attesting products can either opt to purchase DAC provisioning packages from a Matter PKI provider or use their
own PAA by operating a Certification Authority (CA) that conforms to the CSA PKI
requirements. Both of these options have an impact on the operational and/or BOM
costs of the product and should therefore be considered early in the process.
More information about this important product decision can be found in
[Getting a DAC for your product](https://groups.csa-iot.org/wg/matter-tsg/document/25881).

Operation of a CA is covered by the PKI certificate policies and attested by the
CPS.

-   [Matter PKI Certificate policy](https://groups.csa-iot.org/wg/matter-tsg/document/25032)
-   [CSA PKI CPS Template](https://groups.csa-iot.org/wg/matter-tsg/document/27111)
-   [Certificate Policy Self-Attestation Compliance Form](https://groups.csa-iot.org/wg/matter-tsg/document/27269)

A list of PKI providers can be found on the CSA site:

-   [Product Attestation Authorities](https://csa-iot.org/certification/paa/)

#### Development DACs
During the development phase, developers often opt to use test DACs using the test Vendor IDs.
The SDK has a number of example DACs that chain up to the SDK test PAAs and these are loaded
by default by the example apps. The development controllers load the test PAAs by default, which
simplifies development.

Development controllers can be switched to use production PAAs by using the `--paa-trust-store-path` parameter.

Test DACs are not permitted during certification testing, and devices must arrive with two instances
with individually provisioned DACs in order to show that the device can meet the requirements
around individual provisioning. Devices at certification are not required to use production DACs.

Device manufacturers may wish to consider joining the CSA early in the process to understand
the details of the security procedures within the Alliance.

### Certification Declaration (CD)

The Certification Declaration (CD) is provided by the CSA after an attesting product is
certified. It is tied to the Vendor ID and Product ID (or IDs) of the certified
product, and is signed by CSA. The public key corresponding to the signing key is
well known and distributed by the CSA through the DCL.

- [CD Signing Certs Root CA](https://on.dcl.csa-iot.org/dcl/pki/all-certificates?subjectKeyId=97:E4:69:D0:C5:04:14:C2:6F:C7:01:F7:7E:94:77:39:09:8D:F6:A5)

- [CD Signing Cert SKIDs](https://on.dcl.csa-iot.org/dcl/pki/child-certificates/MFIxDDAKBgNVBAoMA0NTQTEsMCoGA1UEAwwjTWF0dGVyIENlcnRpZmljYXRpb24gYW5kIFRlc3RpbmcgQ0ExFDASBgorBgEEAYKifAIBDARDNUEw/97:E4:69:D0:C5:04:14:C2:6F:C7:01:F7:7E:94:77:39:09:8D:F6:A5)

The CD is NOT a standard X.509 certificate, but is
instead a CMS-encoded SignedData payload containing a TLV-encoded structure,
described in section 6.3.1 Certification Declaration of the Matter specification. Certification
Declarations can be viewed using the
[Certificate Tool](https://project-chip.github.io/connectedhomeip-doc/src/tools/chip-cert/README.html).

The Certification Declaration for the product line is provided after
certification testing, and therefore cannot be hard-coded in the firmware. New
Certification Declarations are issued for each certified firmware update.
Therefore, product development should include a strategy for initial
provisioning and updates of the Certification Declaration.

See
[Preparing a Device for Certification](#preparing-a-device-for-certification)
for discussion of CDs used for certification testing.

### Matter onboarding materials (QR codes and manual codes)

In addition to DACs, each individual unit needs to be provisioned with its own
onboarding material for discovery and initial commissioning. This includes the
following per-unit items provisioned on the device:

-   discriminator
-   PAKE verifier (encodes the passcode and PAKE salt)
-   PAKE salt

It also includes the following items encoded on the device exterior or
packaging, both of which encode the discriminator and passcode for the
corresponding unit:

-   QR code
-   manual code

Manual codes are required for all devices, QR codes are optional but
recommended. The rules for QR and manual code inclusions are covered in section
5.7.6 and section 13.6 of the specification.

Information about on-package badging and QR and manual codes are documented in the
[Brand Guidelines](https://csa-iot.org/wp-content/uploads/2022/11/Matter_Guideline_v15b_26102022_Public-Use.pdf).

### In-field updates to Matter

If a product that has already been released with non-Matter firmware wishes to update
to include Matter functionality, the Matter firmware and supporting materials can be
installed on the in-field devices using their already available, non-Matter update
mechanism. Devices can continue to use their original update mechanism for future
Matter updates, or may opt to use the Matter-specified Over-the-Air (Matter OTA)
update mechanism.

In-field update considerations are
discussed in section 5.8 of the specification, but it is important to note that
in-field products are subject to the same per-unit requirements as Out-of-Box
Matter products, and thus it is important to consider how to distribute not only
the firmware, but also how to display the on-boarding material or how to do a
background update using the current connected application and how to provision
the per-unit materials discussed earlier in this section in a secure manner
using the security materials available to the current firmware.

## Certification programs

Product developers should be aware of the various certification programs and how
they may impact the product development process across the entire line.

In particular:

-   Products considering software component certification should understand
    which types of products and operating environments qualify for this program.
-   Products with various SKUs and variants should understand the portfolio
    certification program and what constitutes a viable portfolio parent.
-   Bridge devices should understand the bridge certification program and how
    certification of the supported device types works.

Product manufacturers should be aware that the CSA has a sunset policy in effect
for prior specification revisions. The sunset policy is available in Causeway
via this [link](https://groups.csa-iot.org/wg/members-all/document/39617).

## Distribution of Over-the-air updates (OTA) and re-certification

As development continues on the Matter SDK, developers continue to find and fix
bugs, improve performance and maintainability. Ongoing specification development
works to improve interoperability and performance with new features. For these
reasons, its important to consider delivering software updates using either the
Matter OTA mechanism or a manufacturer-specific mechanism.

The mechanism for delivering OTAs is an important product consideration that
needs to be built into the shipping firmware. Update cadence affects the
certification planning for products since all updates need to be
re-certified.