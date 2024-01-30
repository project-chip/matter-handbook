+++
title = "Attestation"
chapter = false
weight = 45
+++

Certified Devices are Devices that have gone through the Connectivity Standards Alliance (Alliance) Matter Certification Process.

During the commissioning process, a device cryptographically proves (attests) to the commissioner that:
- it is a genuine product
- it is a product that passed Matter compliance tests and has been thus certified by CSA.

In order to accomplish those goals, the device carries:
- A Device Attestation Certificate (DAC) that conveys device's manufacturer ID (VID) and product ID (PID). The DAC chains up to a set of trusted roots, approved by CSA members.
- A securely-stored, private key associated with the public key stored in the DAC that proves the device owns this unique certificate.
- Certificate declaration is a statement cryptographically signed by CSA that states that a tuple (VID,PID) has passed Matter compliance tests.

During the development phase, the manufacturer is able test their Devices without the full Attestation process. Testers should be explicitly informed that the Device is under testing, and it hasn't yet been certified and launched. Once a manufacturer enters a production phase, the ecosystem of the provisioner should enforce all Attestation requirements.

Attestation uses a Public Key Infrastructure (PKI) that leverages Root Certificate Authorities and Intermediate Certificates, in a similar way to the widely adopted server authentication certificates used for SSL/TLS. This process is called the Device Attestation Certificate Chain.

## Device Attestation PKI

The DAC is a X.509 v3 certificate. The first version of X.509 was published in 1988 by ITU-T. The X.509 v3 with Public Key Infrastructure Certificate and Certificate Revocation List (CRL) used by Matter is specified by [RFC5280](https://datatracker.ietf.org/doc/html/rfc5280). It contains:

- Public Key
- Issuer
- Subject
- Certificate Serial Number
- Validity, where expiration can be indeterminate
- Signature
- Vendor ID and Product ID are attributes of the MatterDACName in the DAC subject.

The DAC is unique per device and associated with the unique attestation key pair within the product. It is issued by a CA associated with the Device manufacturer.

The DAC's signature is validated against the Product Attestation Intermediate Certificate (PAI), which is also issued by a PAA. However, a vendor might choose to create one PAI per product (PID-specific), group of products, or for all its products.

At the root of the chain of trust, the Product Attestation Authority (PAA) Certificate Authority (CA) public key validates signatures from the PAI. Note that the Matter trust store is federated and the set of PAA certificates trusted by commissioners is maintained in a central trusted database (the Distributed Compliance Ledger). Entry of a PAA within the trusted set requires meeting a certificate policy managed by the Alliance.

![Matter Attestation Public Key Infrastructure](../../primer-attestation-pki.png)

The PAI is also a X.509 v3 certificate that includes:

- Public Key
- Issuer
- Subject
- Certificate Serial Number
- Validity, where expiration can be indeterminate
- Signature
- Vendor ID and Product ID (optionally) are attributes of the MatterDACName in the DAC subject.

Lastly, the PAA is the root certificate in the chain and it is self-signed. It includes:

- Signature
- Public Key
- Issuer
- Subject
- Certificate Serial Number
- Validity

## Additional Attestation Documents & Messages

The attestation process has several documents and messages. The following items are a brief overview of their function and composition. The image below aids in the understanding of their hierarchy.

![Attestation Document Hierarchy](../../primer-attestation-document-hierarchy.png)

### Certification Declaration (CD)
The CD allows the Matter device to prove its compliance with the Matter protocol. Whenever the Matter Certification Processes finishes, the Alliance creates a CD for the device type so the Vendor might include it in the firmware. The CD includes among other information:
- VID
- PID (one or more)
- Server Category ID
- Client Category ID
- Security Level
- Security Information
- Certification Type (development, provisional, or official)
- Signature

### Firmware Information (optional)
The Firmware Information contains the CD Version Number and one or more digests of components in the firmware, such as the OS, filesystem, bootloader. The digests may be either a hash of the software components or a hash of the signed manifests of the software components.

The vendor might as well choose to include in Firmware Information only the "hash-of-hashes" of its components, instead of an array of individual hashes.

Firmware Information is an optional element in the Attestation Process and applicable when a vendor has a secure boot environment which handles the Attestation key pair.

### Attestation Information
Message sent from the Commissionee to the Commissioner. The Attestation Information combines a TLV containing the Attestation Elements and a Attestation Signature.
Attestation Elements

### This is a TLV containing:
- Certificate Declaration
- Timestamp
- Attestation Nonce
- Firmware Information (optional)
- Vendor Specific information (optional)

### Attestation Challenge
Out-of-band challenge derived during Passcode Authenticated Session Establishment (PASE)/ Certificate Authenticated Session Establishment (CASE) session establishment and used to further secure the procedure and avoid replayed signatures. Comes from either CASE session, PASE session or a resumed CASE session.

### Attestation TBS (to be signed)
Message containing the Attestation Elements and Attestation Challenge.

### Attestation Signature
Signature of the Attestation TBS, signed using the Device Attestation Private Key.

## Attestation Procedure
The Commissioner is responsible for validating attestation information from the Commissionee. It executes the following steps:

1. Commissioner generates a random 32 byte attestation nonce. In cryptography jargon, a nonce (number used once) is a random number generated in the cryptographic procedure and meant to be used once.
2. Commissioner sends the nonce to the Commissionee and requests the Attestation Information.
3. Commissionee generates the Attestation Information and signs it with the Attestation Private Key.
4. Commissioner recovers the DAC and PAI certificate from the Commissionee, and looks up the PAA certificate from its Matter trust store.
5. Commissioner validates the Attestation Information. These are the conditions for validation:
    - DAC certificate chain must be validated, including revocation checks on the PAI and PAA.
    - VID on the DAC matches the VID on the PAI.
    - The Attestation Signature is valid.
    - Nonce in Device Attestation Elements matches the nonce provided by the Commissioner.
    - Certificate Declaration Signature is valid using one of the Alliance's well-known Certification Declaration signing keys.
    - Firmware Information (if present and supported by Commissioner) matches an entry in the Distributed Compliance Ledger.
    - Additional VID/PID validations also take place between the Device Basic Information Cluster, Certification Declaration and the DAC.

_This content was originally published on the [Google Developer Site](https://developers.home.google.com/matter/primer)_